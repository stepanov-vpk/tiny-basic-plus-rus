# TinyBasic Plus (RUS)

Данный репозиторий является русскоязычной адаптацией библиотеки [Tiny Basic Plus](https://github.com/BleuLlama/TinyBasicPlus), созданной Скоттом Лоуренсом. В рамках проекта были также внесены несколько изменений, таких как добавление поддержки клавиатуры PS/2 и улучшение читаемости кода. Для реализации поддержки клавиатуры PS/2 использовалась библиотека [PS2KeyAdvanced](https://github.com/techpaul/PS2KeyAdvanced) Пола Карпентера. 

Реализация Tiny Basic на языке C с акцентом на поддержку Arduino. Изначально она была написана Гордоном Брандли в виде "68000 Tiny Basic", а затем портирована на C Майклом Филдом как "Arduino Basic", хотя в исходных файлах она по-прежнему называется "Tiny Basic".

TinyBasic Plus является расширением и модификацией оригинального "Tiny Basic", добавляя поддержку нескольких дополнительных устройств, настраиваемую на этапе сборки. Он предназначен для использования на Arduino, хотя сборки также вскоре будут легко доступны для других платформ через командные makefile. В комплекте идет makefile, который собирает для UNIX-подобных операционных систем. Он был протестирован только на Darwin (OS X).

Добавленные функции включают поддержку работы с файлами (библиотека SD), автоматический запуск программы с SD-карты, меньший объем занимаемой памяти (PROGMEM), поддержку ввода-вывода данных по пинам и поддержку встроенного EEPROM для хранения вашей программы.

# Полный список поддерживаемых операторов и функций

## Система

- BYE		- *выход из режима TinyBasic Plus, мягкая перезагрузка Arduino*
- STOP	- *остановка выполнения программы, также означает «СТОП»*
- MEM	  - *вывод статистики использования памяти*
- NEW	  - *очистка текущей программы*
- RUN		- *выполнение текущей программы*

## Работа с SD-картой

- FILES 								- *вывод списка файлов на SD-карте*
- LOAD *filename.bas* 	- *загрузка файла с SD-карты*
- CHAIN *filename.bas*	- *эквивалент: new, load filename.bas, run*
- SAVE *filename.bas* 	- *сохранение текущей программы на SD-карту, перезаписывая*

## EEPROM - энергонезависимая встроенная память

- EFORMAT	- *очистка памяти EEPROM*
- ELOAD 	- *загрузка программы из EEPROM*
- ESAVE 	- *сохранение текущей программы в EEPROM*
- ELIST 	- *вывод содержимого EEPROM*
- ECHAIN 	- *загрузка программы из EEPROM и её запуск*

## Работа с вводом-выводом

- INPUT *variable* 	  - *ввод выражения пользователем (число или имя переменной)*
- PEEK(*address*) 	  - *получить значение по адресу* (не реализовано)
- POKE *address* 		  - *установка значение по адресу* (не реализовано)
- PRINT *expression* 	- *вывод выражения, а также «?»*
- REM *stuff* 				- *замечание/комментарий, также "'"*

## Математические выражения

- A=V, LET A=V 				    - *присвоение значения переменной*
- +, -, \*, / 					  - *арифметические операции*
- <, <=, =, <>, !=, >=, > - *cравнения*
- ABS(*expression*) 		  - *возврат абсолютного значения выражения*
- RSEED(*v*) 					    - *установка случайного начального число на v*
- RND(*m*) 					      - *возврат случайного число от 0 до m*

 ## Основные команды

- IF *expression statement*									    - *выполнение инструкции, если выражение истинно*
- FOR *variable = start* TO *end* 						  - *начало для блока*
- FOR *variable = start* TO *end* STEP *value* 	- *начало для блока с шагом*
- NEXT 																	        - *конец блока*
- GOTO *linenumber* 											      - *продолжить выполнение с номера строки linenumber*
- GOSUB *linenumber* 											      - *вызов подпрограммы в строке с номером строки linenumber*
- RETURN 																        - *возврат из подпрограммы*

## Управление вводом-выводом

- DELAY *timems* - *ожидание (в миллисекундах)*
- DWRITE *pin,value* - *установить значение цифрового пина (HIGH, HI, LOW, LO)*
- AWRITE *pin,value* - *установить значение аналогового пина (pwm) 0..255*
- DREAD(*pin*) - *чтение значения с цифрового пина*
- AREAD(*analogPin*) - *чтение значения с аналогового пина*

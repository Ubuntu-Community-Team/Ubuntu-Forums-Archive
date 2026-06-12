---
title: "Possible batch file help"
date: 2010-09-17
forum: General Help
---

### Post by voncloft on 2010-09-17
Not sure if anyone can help.

But I have a program I would like to run on a thumb drive.

It has a ini file that sets its local variables for the time set and run.

I would like to have a batch file to substitute its variables used to run at run time so it can be universal.  THe program is C++

I have so far these 2 codes
______________________________________________________
c.bat

@echo off
set pathDrive=%cd:~0,2%

set pathConf=%pathDrive%\PortableApps\dev-c++4\devcpp.ini
set BinDir=%pathDrive%"\PortableApps\dev-c++4\Bin\"
set CDir=%pathDrive%"\PortableApps\dev-c++4\Include\"
set CppDir=%pathDrive%"\PortableApps\dev-c++4\Include\G++";%pathDrive%"\PortableApps\dev-c++4\Include\"
set LibDir=%pathDrive%"\PortableApps\dev-c++4\Lib\"
set devcpppath=%pathDrive%\PortableApps\dev-c++4\devcpp.exe
echo BinDir="%BinDir%">>%pathConf%

echo.>> %pathConf%
echo CDir="%CDir%">>%pathConf%

echo.>> %pathConf%
echo CppDir="%CppDir%">>%pathConf%

echo.>> %pathConf%
echo LibDir="%LibDir%">>%pathConf%

echo.>> %pathConf%
start %devcpppath%
_______________________________________
the ini of c++ the section that needs to be substituted

[Directories]
BinDir=F:\PortableApps\dev-c++4\Bin\
CDir=F:\PortableApps\dev-c++4\Include\
CppDir=F:\PortableApps\dev-c++4\Include\G++;F:\PortableApps\dev-c++4\Include\
LibDir=F:\PortableApps\dev-c++4\Lib\

when I run it withou the ini being modded it runs the app but says it can create the runtime environment of default stuff

---

### Post by AlphaLexman on 2010-09-17
'Batch' files are ms-dos/windows specific. Don't confuse batch executables with 'bash' executables.

Bash, is the bourne again shell used by default in ubuntu. It has different variable naming conventions than batch files. It looks like your batch file is NOT compatible with bash.

---


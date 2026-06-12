---
title: "Setup.BAT  from windows asks for admin privilages"
date: 2010-11-05
forum: General Help
---

### Post by mower-elz on 2010-11-05
Hello, i have a program from windows that requires a .bat file for installation, i open it with Wine Windows Program Opener and opens the CMD, if i opened this in windows it would install because i am on the admin account but will not if i am not admin, opening it on here it thinks i am not admin, how can i make it think i am? here are screen grabs,

it shows this for a few seconds....
[ATTACH]174686[/ATTACH]

then shows this, pressing return closes the window
[ATTACH]174687[/ATTACH]

i am using Ubuntu 10.04 LTS -  Lucid Lynx

Thankyou in advance :)

---

### Post by tgm4883 on 2010-11-05
Open the .bat file in a text editor and see if you can find where it does the admin checking

---

### Post by mower-elz on 2010-11-05
> **tgm4883 said:**
> Open the .bat file in a text editor and see if you can find where it does the admin checking

i can open it but do not know where to start, i will post it here, it is quite long.

[B]@echo off 
rem Author: Synapse 
rem Date: April 16th 2009 
rem Setup design version: 2.60 
rem Installer version: 1.0 
cls 
color a 
title Garry's Mod 11 Installation 
set DR=%CD%\Install Files 
set ID=%PROGRAMFILES%\Valve\Garry's Mod 
set TD=%HOMEDRIVE%\GMD-TMP 
echo. 
echo -Checking if UAC is enabled... 
REG QUERY "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v ENABLELUA || goto notvista 
FOR /F "tokens=2* delims=     " %%A IN ('REG QUERY "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System" /v ENABLELUA') DO SET UAC=%%B 
IF NOT %UAC%==0x0 goto uaccheck 
:notvista 
echo -Checking administrative privileges... 
net localgroup administrators>"%SystemRoot%\ADMINS.txt" 
move "%DR%\isadmin.cf2" "%DR%\isadmin.exe">nul 
"%DR%\isadmin.exe" 
IF NOT ERRORLEVEL 1 goto admincheck 
move "%DR%\isadmin.exe" "%DR%\isadmin.cf2">nul 
echo -Removing temporary install files... 
del/f/q "%SystemRoot%\ADMINS.txt">nul 
del/f/q/s %TD%\>nul 
cls 
IF EXIST "%ID%\hl2.exe" goto exist 
goto installation 
:continue 
taskkill /IM debug2.exe /F>nul 
cls 
echo. 
echo Removing previous installation (please wait)... 
del/f/q/s "%ID%\">nul 
:installation 
cls 
echo.[/B]

---

### Post by mower-elz on 2010-11-05
WOW, i may have success. it is installing now, i deleated all the parts to do with admin checks from the file!!

---


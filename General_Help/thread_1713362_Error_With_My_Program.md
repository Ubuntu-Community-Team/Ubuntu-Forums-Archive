---
title: "Error With My Program"
date: 2011-03-24
forum: General Help
---

### Post by lordethanr12 on 2011-03-24
```
@echo off
echo Hello sir, how are you today?
set /p mood
if %mood% == good go to good mood
if %mood% == bad go to bad mood 
:good mood
echo Well I am delighted to hear that!
go to begin
:bad mood
echo Well I am sorry to hear that!
go to begin
:begin
echo What file would you like to open today sir?
set /p file
if %file% == Internet Explorer Start C:\Program Files\Internet Explorer
```
 
This is a Batch program I'm trying to do and it says that the syntax of the command is incorrect and it also says it for this file 2
 
 
```
@echo off
:start
echo Hi! I am your computer. I've never got to speak to you before. What's your name?
set /p name=
if %name% == stop goto exit
echo Nice to meet you %name%!
echo How are you %name%?
set /p mood=
echo That's good. I am %mood% too.
echo What do you want to do?
set /p do=
echo I don't want to do %do%.
echo Shall i quit?
set /p quit=
if %quit% == yes goto exit
if %quit% == no goto continue
:continue
echo Cool I didn't want to stop talking to you. 
echo So what is your favorite food?
set /p food=
echo I like %food% also.
echo I'm getting bored do you want to quit?
set /p quit2 
if %quit2% == yes goto exit
if %quit2% == no goto continue2
if %quit2% == mabye goto secret
:continue2
echo So how old are you? (if you're older than 40 just say 40+)
set /p age
if %age% == 1 goto younglings
if %age% == 2 goto younglings
if %age% == 3 goto younglings
if %age% == 4 goto younglings
if %age% == 5 goto younglings
if %age% == 6 goto kids
if %age% == 7 goto kids
if %age% == 8 goto kids
if %age% == 9 goto kids
if %age% == 10 goto kids
if %age% == 11 goto kids
if %age% == 12 goto kids
if %age% == 13 goto teens
if %age% == 14 goto teens
if %age% == 15 goto teens
if %age% == 16 goto teens
if %age% == 17 goto teens
if %age% == 18 goto teens
if %age% == 19 goto young adult
if %age% == 20 goto young adult
if %age% == 21 goto young adult
if %age% == 22 goto adult
if %age% == 23 goto adult
if %age% == 24 goto adult
if %age% == 25 goto adult
if %age% == 26 goto adult
if %age% == 27 goto adult 
if %age% == 28 goto adult
if %age% == 29 goto adult
if %age% == 30 goto adult
if %age% == 31 goto adult 
if %age% == 32 goto adult
if %age% == 33 goto adult
if %age% == 34 goto adult
if %age% == 35 goto adult
if %age% == 36 goto adult
if %age% == 37 goto adult
if %age% == 38 goto adult
if %age% == 39 goto adult
if %age% == 40+ goto old adult
:younglings
echo Wow so you must be pretty smart! 
goto continue3
:kids
echo Ahhh that age is the best!
goto continue3
:teens
echo Those are very complicated years.
goto continue3
:young adult
echo You're growing up and the world is very new and exciting!
goto continue3
:adult
echo Oh being old stinks but you're not there yet.
goto continue3
:old adult
echo You may be old but you have expeirence!
goto continue3
:secret
echo Wow you've found the secret spot
pause 
echo Sooooo? 
pause
echo Hmmmmmmm.
pause
echo Ahh I know! So do you want to advance?
set /p quit3
if %quit3% == yes goto exit
if %quit3% == no goto continue2
:continue3
```
 
 
so can you please tell me what i am doing wrong? THX :)

---


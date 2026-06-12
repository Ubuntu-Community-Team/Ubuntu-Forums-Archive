---
title: "Compiz.real use 100% CPU...THIS PROBLEM IS NOT SOLVE..MULTIPLE THREAD...NEED HELP !!!"
date: 2010-02-17
forum: General Help
---

### Post by jee_bee on 2010-02-17
Ubuntu 9.10 2.6.31.19 (updated from 2.6.31.14) 64X 

(in my case 6600gt, was working realy fine on 9.04)

on nvidia 185 and 173 driver:
 
On each startup (or when opening a session) compiz.real use 100% of the cpu
so the system became unusable, only way to get the system usable until next restart or session ending it's by goin in                     System>Administration>System Monitor 
and kill compiz.real

[IMG]http://img59.imageshack.us/img59/3180/96compizreal.png[/IMG]

if i try to relaunch compiz.real in terminal...

[IMG]http://img718.imageshack.us/img718/3539/compizreal.png[/IMG]

if i try to launch compiz --replace

[IMG]http://img682.imageshack.us/img682/1603/compizreplace.png[/IMG]

on nvidia 96 driver:

system became stable but imposible to activate any effect
when you select normal or extra effect windows frames disapear
and it's impossible to do anything

ps aux | less result before and after i kill compiz.real are atached...

any other info needed ??? just let my know!

---

### Post by OliW on 2010-02-17
You've clearly been through a hell of a lot trying to fix this... I would suggest a clean install (even if it's just a temporary one) of 9.10 to see if that fixes things. If it does, you can look at migrating old bits across.

Might seem like a lot of effort but it's just 30 minutes to see if it's something you're never going to find manually.

---

### Post by jee_bee on 2010-02-17
forgot to mansion..... IVE DID IT ! 5 time

every time i instal a driver the probleme apear

---

### Post by jee_bee on 2010-02-18
OK freSH INSTAL OFF UBUNTU 9,10 32BIT SAME PROBLEM HELP MY PLEASE!!!!!!!! NOBODY EVEN TRY TO HELP MY IT'S BEEN 3 DAY THaN I ONLY WORK ON THAT IL DO ANYTHING TO AVE SOME HELP
IM TOTALY PISS OFF AND AFTER 3 INTeNSE DAY OFF WORK ON THAT PROBLEM I FEEL LIKE I hAVE NO SUPORT AT ALL !!!!!!

it's the second time here than i post a question and i diden get
any awnser........

ask my ANY info u need i let u remote acces my machine if u wish



on sytem start (or when opening session) compiz.real process
use ALL the cpu for 10 minutes or more after the system stabilise
by it self ( and by the way after it became stable it's solid like rock !! no lag at all  whit normal effect )
than when the screen saver come up problem came back.....

it's a triple boot sytem and everyting work super super fine exept ubuntu
(XP,7,Ubuntu)

and like the title of the thread say this probleme is comon and never ave been solve !!!!!   

and if nobody can help my, at least tell my where can i get some help !!!!!!

PLEASE!!     IM BEGGIN UR GUY TO SOLVE MY PROBLEM     PLEASE!!

---

### Post by jee_bee on 2010-02-18
I Need Help !!!!!!!!!!!!!!

---

### Post by Lockheed on 2010-02-18
Mate, I have EXACTLY the same problem, except once I kill it in Sys Monitor, I am then able to start it again with 
```
compiz.real --replace
```
However, this is extremely annoying having to do it at 9 out of 10 system startups and this methods only works in 80% of cases, anyway.

My system is as in the signature and I am using nvidia 190.52 drivers.

---

### Post by jee_bee on 2010-02-18
i perfecly know that  and i now even think the solution can be to include a sricpt including [COLOR="DarkRed"]compiz.real --replace[/COLOR] in the startup what do u think ?

---

### Post by jee_bee on 2010-02-18
[COLOR="Blue"]yeah!! we gonna do right a script so compiz.real will be kill and
execute compiz.real --replace  and run that process in backgroud......    yeah!!!   let me do that !! ( if i can lol;))[/COLOR]

---

### Post by Lockheed on 2010-02-18
Yeah, I was thinking about it since last few weeks but was too lazy to do it. Besides, I am not sure how to kill process without knowing its ID.

Bear in mind the operation needs to hold some timeframe.

Startup
20 seconds wait
kill compiz.real
5-10 seconds wait
compiz.real --replace

---

### Post by jee_bee on 2010-02-18
lol u want to keep the process compiz.real in a terminal !!!?

[http://ubuntuforums.org/showthread.php?p=8847971#post8847971]("http://ubuntuforums.org/showthread.php?p=8847971#post8847971")

---

### Post by Lockheed on 2010-02-18
Why would I want it? And stop using 'lol' as punctuation.

---

### Post by jee_bee on 2010-02-19
ok.... i found a way to fix the problem temporatly.....

create a srcript that kill compiz.real and exec compiz.real --replace
fix the freeze startup but take a few second more than a normal ubuntu
startup (hard to notice...)

[COLOR="Red"]here are the step by step instruction:[/COLOR]

[COLOR="Blue"]create a plain file by right clicking where u want to create it >
( where the script is dosen mater put it where ever u want )
create a documents>
plain file>
name the file  wathever you want as long that it end with .sh

ok now that we create our file we gona make it executable by
right click on the new file>
properties>
go to the tab "permissions">
make sure that Allow executing file as program is ticked and press close

now double click your file and and click on "Display"
and enter the next two line:[/COLOR]

> kill compiz.real
exec compiz.real --replace
[COLOR="Blue"]
save it and close it...

now that we create the script we need to make ubuntu execute it
at each session opening ( you need to do the next step to each user
if you ave more than one ) >

 Systeme> Preference> Application on startup   >
click on the button "add"  >
Name = wathever you want....
Command = browse to the path where you save the script and select it

click on "Close" to close the application on startup windows

Restart your machine[/COLOR]

thats it !!! no more compiz.real 100% cpu load



And by the way for people who ave more Ubu-knowledge than my.....
you gona need to find a permanent fix for that bug....

im the first one to find a solution and it scared my alot because
for more than 3 day i was unable to get a stable ubuntu 9.10
and nobody REaly help my out.............(mean i found the solution)
i was here basicly to get help and save time... :<
but that wasen the case !.............

 
if any boddy use my solution feel free to thank's me or ask any question......

Peace ! X)

---

### Post by rifter on 2010-03-11
[post=4045036]This post[/post] suggests disabling the special effects to reduce compiz cpu usage:

> Right click on your desktop. Select "Change Desktop Background".
Select tab "Visual Effects"
Select none.
Note the sudden drop in CPU usage.

This is very similar to undoing the special effects in Windows XP in that it can increase performance even if you weren't haveing problems using the effects before.

---

### Post by Lockheed on 2010-03-11
Well, I found a way to solve the problem without sacrificing anything.
All you need to do is delay some of the startup application, so that there is no heard of cpu-hungry apps at system bootup.

It worked perfect ever since.

---

### Post by rifter on 2010-03-13
> **Lockheed said:**
> Well, I found a way to solve the problem without sacrificing anything.
All you need to do is delay some of the startup application, so that there is no heard of cpu-hungry apps at system bootup.

It worked perfect ever since.

That helps with cpu intenseness on startup, but my problem with compiz is that at least under certain conditions it seems to seize the cpu in the middle of a session.  I've had it do this when I killed something else, like a game emulator, that was not working and hogging resources.  Until I found out about --replace I was stuck with rebooting because I didn't think I could fix my windows without restarting X.

Now I will say that even --replace has not been a perfect fix for me.  When I kill compiz all my windows are still on the screen but I can't do anything with them.  The applications are still running.  The last time I did a --replace on compiz it made my windows work again, but I had some weird transparency to the window bars, like for some reason it was using a different and unexpected theme.  Going into the control panel and changing the effects fixed that, but I think probably that just reasserting the preferences would have worked even without changing the effects.

I will say that compiz has a bad reputation going way back for this sort of thing.  People used to always have to disable it to be able to play games, because it hogged so many resources.  I am actually contemplating that process myself because I am wondering if it will help performance in some things that unfortunately under Ubuntu I am having worse performance than under Windows on the same box (never before a problem with Linux -- it was always the opposite, but then I have favoured less intense window management systems in the past as well).  

In any case there is some wonkiness here that bears looking into.

---

### Post by Zeno Izen on 2010-11-23
> **rifter said:**
> [post=4045036]This post[/post] suggests disabling the special effects to reduce compiz cpu usage:



This is very similar to undoing the special effects in Windows XP in that it can increase performance even if you weren't haveing problems using the effects before.



Wow... I wish I had done that sooner.  My productivity probably just increased 12%.

---


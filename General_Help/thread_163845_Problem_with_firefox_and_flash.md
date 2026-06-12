---
title: "Problem with firefox and flash"
date: 2006-04-21
forum: General Help
---

### Post by Artist22405 on 2006-04-21
the problem I am have is that when I go to youtube to watch some vids or any other flash based videos firefox tells me that javva is old or that flash is old . I have used automatix to install firefox  I have installed the newest flash player but still to no avail any help would be great thank you

---

### Post by _linux_ on 2006-04-21
Weird. Have you tried Firefox 1.5?

---

### Post by moon_dog on 2006-04-21
try installing this copy of flash.  it auto installs to your mozilla firefox and/or opera browser.  if this doesn't work, find the flash folder and manually copy the flash plugin files to your mozilla firefox plugins folder.

[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

the flash plugin files are:
flashplayer.xpt
libflashplayer.so

---

### Post by Artist22405 on 2006-04-21
I did install the newest falsh player and after some looking around I found the plugins folder the files are intsalled it also says java may be turned off what dos this mean

---

### Post by moon_dog on 2006-04-21
it means that you don't have the java plugin.  just google it up and download it.  there are several threads on this forum on how to install the java plugin.  go to [http://www.speakeasy.net/speedtest/](http://www.speakeasy.net/speedtest/).  if you can use the speed test then you have java on your pc.  if not, then you need to install it.

---

### Post by Slasher9641 on 2006-04-21
Or you could use Automatrix instead off googleing

---

### Post by Artist22405 on 2006-04-21
ok did what you said insatlled it again to find out it still doesnt work](*,)

---

### Post by moon_dog on 2006-04-21
if you're talking about java, here are the instructions i followed for allowing firefox to use java.

credits go to KansasJoe

> Download it here [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

Follow instructions here [http://www.java.com/en/download/help...selfextracting](http://www.java.com/en/download/help...selfextracting)

i suggest extracting the file to home directory to avoid permission issues and your plugin for mozilla is located in /home/"your username"/.mozilla/plugins

so now when you go to set up the link you will open terminal and
cd .mozilla/plugins

next in terminal type

ln -s /home/"your username"/jre1.5.0/plugin/i386/ns7/libjavaplugin_oji.so

you can copy this exactly minus the your username which will obviously be your username and you must extract the jre file you dl to your home folder.

if you're talking about flash, are you using firefox or swiftfox?  if you're using swiftfox, you have to copy the flash files to the swiftfox plugins folder.

---

### Post by Artist22405 on 2006-04-21
java installed flash installed speakeasy say latest flash needs to be installed i am using firefox 1.5 before I used automatix everything worked fine with mozzilla hmm](*,)

---

### Post by moon_dog on 2006-04-21
you'll have to isolate whether it's flash or java that's not  working.  go to this site to verify that java works on your browser.

[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

it's step 3, verify installation.

once you've verified that java has been installed, then try the youtube website.  if you still can't view the videos then flash hasn't been installed.

---

### Post by Artist22405 on 2006-04-21
ok it is a java problem I cant seem to install it as pre ther insturctions hmm what a noob

---

### Post by tie wrap on 2006-04-22
[QUOTE=moon_dog]try installing this copy of flash.  it auto installs to your mozilla firefox and/or opera browser.  if this doesn't work, find the flash folder and manually copy the flash plugin files to your mozilla firefox plugins folder.

[http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

the flash plugin files are:
flashplayer.xpt
libflashplayer.so[/QUOTE]

im just a newbie in this forum and also a newbie with regards to ubuntu. the reason why im here is that i cant play any flash files from my mozilla firefox. the worst thing is that the link from the download site of macromedia to download flashplayer is not working. im just wondering if anyone here have a copy of the installer and perhaps would send me the copy or any link that i can download the installer.

thanks a lot for your help

---

### Post by Artist22405 on 2006-04-22
I used the installer for flash its ays its installed but still doesnt work as far as the installer goes you can extact the files open the terminal and just move the flash installer file there and it will promt you with yes or no ?s it is installed java 1.4 is installed but I cantseem to get the hang of installing java 1.5.0and I think thats the problem you cant log on as root which I like because it keeps you from messing things up but when you have a problem and try to follow most of the instuctions for installing things in root I just dont get it I used rot terminal but it tells me no such file or something like that I know its there its right on the desktop and being a a long time windoze user I havent used the command line for much but I am making the switch to linux all the way but for 1 program that I use to cut vinyl on my sign plotter so I guess it will take time
sorry for the run on sentance  
and thank you for all the help so far
now if I could just play flash files hmm
I will play with it some more

---

### Post by Artist22405 on 2006-04-22
ok problem solved I installed new java that didnt work hmm installed flash 4 times and now it works oh installed an adblock too dont know what I did to make it work but thanks for all the help:-D

---


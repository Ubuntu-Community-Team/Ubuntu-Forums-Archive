---
title: "wma and avi are not working."
date: 2006-04-07
forum: General Help
---

### Post by latinpride613 on 2006-04-07
hello. i have followed the instructions on getting the win32 codecs and installed them properly, but that is not working. its saying that


              "This file is encrypted and cannot be played back."

if someone could help me with this that would be great. thanks!

---

### Post by frodon on 2006-04-07
Which instruction did you followed ?
All you need should be here : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Some players require to set the path to the w32codecs lib in their settings, by the way which player do you use ?

---

### Post by frup on 2006-04-07
can you play any other formats like mp3 or something?

---

### Post by latinpride613 on 2006-04-07
**Mp3's do work and work pretty good. the only problem is the avi's and wma's. the instuctions i followed were:**

  "1.You have to OWN A LEGAL COPY of Windows, because these are proprietary codecs (somebody correct me if I'm wrong)

2)Install &#8220;xine-ui&#8221; and &#8220;totem-xine&#8221; in Synaptic or type in the command line: 
sudo apt-get install xine-ui ; totem-xine

3) Launch Xine (or Totem) and try to play a video (this will create a .config file)

4) Download the codecs from this website:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
(just download the &#8220;essential codecs package&#8221;)

if the link above is temporarily down try this mirror:
[http://www4.mplayerhq.hu/homepage/design7/dload.html](http://www4.mplayerhq.hu/homepage/design7/dload.html)

5) Open the command line(&#8220;Konsole&#8221; if you are using KDE, &#8220;Terminal&#8221; if you are using GNOME) and follow these steps:

a) Get to the directory where you have downloaded the file (/home/alberto/downloads in my case)

cd /home/alberto/downloads

b) Create the directory in which you are going to put the codecs (/usr/lib/win32) 

sudo mkdir /usr/lib/win32

c) Now, assuming the file you downloaded is &#8220;essential-20050412.tar.bz2&#8221;:

tar -xjf essential-20050412.tar.bz2 (this will extract the file)

sudo mv essential-20050412/* /usr/lib/win32 (this command will move the files to the desired folder)

d) Now restart xine (if you were using it)

Congratulations, now you can open wma, wmv, and avi files by using Totem and Xine!"

**i checked to see if the files were in the exact place, and they are. Thanks for the quick response guys!**

---

### Post by damu on 2006-04-07
I guess you should use [Automatix]("http://www.ubuntuforums.org/showthread.php?t=138405&highlight=AUTOMATIX")...it does it all for you

---

### Post by frodon on 2006-04-07
Hum, this should work (i followed quite the same steps at the time).

Look in the totem settings, especially in the codec settings tab you should see the path that the player use to search codecs, maybe the path for wma codecs is wrong or empty.

---

### Post by latinpride613 on 2006-04-07
I checked the settings tab in xine and it says /usr/lib/win32. i cant find the tab for totem though. and i have automatix and just used it again and nothing still. well, at least you guys tried...thanks alot for your help and quick responses. i will keep looking around.

---


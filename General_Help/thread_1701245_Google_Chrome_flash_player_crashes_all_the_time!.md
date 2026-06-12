---
title: "Google Chrome flash player crashes all the time!"
date: 2011-03-06
forum: General Help
---

### Post by dioxholster on 2011-03-06
so i went to preferences to see plugins and cant find flash player just Shockwave player and if i disable it no youtube video. There is also something called Icetea or whatever.

---

### Post by dioxholster on 2011-03-06
no one got that problem?

---

### Post by AbuSix on 2011-03-06
actually i got that problem on firefox last night after the update but today its gone !

---

### Post by dioxholster on 2011-03-06
> **AbuSix said:**
> actually i got that problem on firefox last night after the update but today its gone !

i got no problem with firefox, just chrome. How do i reinstall maybe that could fix it?

---

### Post by pqwoerituytrueiwoq on 2011-03-06
could just be your flash version
if you have a 64bit system
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
we can help with installing if we know how you have flash installed
if you just want it in chrome extract it to this folder
/opt/google/chrome/plugins
you may need to make the plugins folder

you could just enable html 5 video on youtube
[http://www.youtube.com/html5](http://www.youtube.com/html5)
big link at the bottom

---

### Post by dioxholster on 2011-03-06
> **pqwoerituytrueiwoq said:**
> could just be your flash version
if you have a 64bit system
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
we can help with installing if we know how you have flash installed
if you just want it in chrome extract it to this folder
/opt/google/chrome/plugins
you may need to make the plugins folder

you could just enable html 5 video on youtube
[http://www.youtube.com/html5](http://www.youtube.com/html5)
big link at the bottom


im running a netbook ao i dont think its a 64bit system. But i couldnt find a plugins folder and theres no way for me to create one.

here are my chrome plugins:

> IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1))
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1)) executes Java applets.
Name:	IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1))
Description:	

The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.5 (6b20-1.9.5-0ubuntu1)) executes Java applets.


Default Plug-in - Version: 1
Provides functionality for installing third-party plug-ins

Shockwave Flash (2 files)
Shockwave Flash 10.2 r154
Name:	Shockwave Flash

Chrome PDF Viewer 

...

I tryed the Html5 it works but crashes the whole browser and gets slow quickly. While adobe gives me error that crashes all youtube videos and other times turns all videos into black & white.

---

### Post by pqwoerituytrueiwoq on 2011-03-06
run this command
uname -m
if it says "x86_64" it is 64 bit
if it says "i686" it is 32bit
edit:
try html5 with compiz off

also you can make a folder with this command
sudo mkdir /opt/google/chrome/plugins
then you can move the libflashplayer.so file there with this command
sudo mv /home/$USER/Desktop/libflashplayer.so /opt/google/chrome/plugins
assuming the file is on your desktop

---

### Post by dioxholster on 2011-03-06
> **pqwoerituytrueiwoq said:**
> run this command
uname -m
if it says "x86_64" it is 64 bit
if it says "i686" it is 32bit
edit:
try html5 with compiz off

also you can make a folder with this command
sudo mkdir /opt/google/chrome/plugins
then you can move the libflashplayer.so file there with this command
sudo mv /home/$USER/Desktop/libflashplayer.so /opt/google/chrome/plugins
assuming the file is on your desktop

its 32bit. compiz is not installed because im running it like netbook edition. Did everything you said made folder and all but still no luck.

---

### Post by pqwoerituytrueiwoq on 2011-03-06
not sure what else there is we can do flash is hell on linux and macs
when flash dies i expect more people will use non MS operating systems
you can try the .tar.gz flash on [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
just extract the libflashplayer.so to the desktop and move it to chromes plugin folder
already posted the command for that
it is probably the same flash you are using already

---

### Post by dioxholster on 2011-03-07
> **pqwoerituytrueiwoq said:**
> not sure what else there is we can do flash is hell on linux and macs
when flash dies i expect more people will use non MS operating systems
you can try the .tar.gz flash on [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
just extract the libflashplayer.so to the desktop and move it to chromes plugin folder
already posted the command for that
it is probably the same flash you are using already

Kinda odd that im the only one with this problem, should i reinstall or something like that?

---

### Post by pqwoerituytrueiwoq on 2011-03-07
you can try a different version of chrome 
stable/beta/unstable
you can always just use firefox 4
[http://nightly.mozilla.org/](http://nightly.mozilla.org/) (edit page says updated today but my install says it is up to date 2011-03-03)
it has not updated in a few days the RC should be out soon
just extract it and run firefox in the firefox script in it
/path/to/firefox
may end up being something like 
/home/$USER/firefox/firefox
or like i have mine
/opt/nightly-firefox/firefox

---

### Post by simonmoon42 on 2011-03-07
I would try installing Chromium instead... It just seems more stable to me. I used to have flash issues all the time, but since I switched Chromium they've all gone away. Flash needs to die... soon.

---

### Post by dreamsR4living on 2011-03-10
I have this same problem with flash since a day or two, never had it before and I have been using Ubuntu since 6.06

In Chrome flash doesn't work at all, while in Firefox it is also not working as it should. Most of it works, but youtube is refusing to play.

I am running Ubuntu 10.10 on a i386 system. As I said, the problem just started out of the blue.

---

### Post by dreamsR4living on 2011-03-10
> **simonmoon42 said:**
> Flash needs to die... soon.

It should, for sure! HTML5 + CSS3 rules

---

### Post by Foxcow on 2011-03-10
I get the occasional crash but the one think that always makes Flash crashes when I try to upload to Flickr via browser.

I'm using 10.2 r152.

There was a 10.3 beta that came out a few days ago that I'm thinking about giving a shot but there is not 64-bit version.

This is the latest natively 64-bit version from Adobe:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)


edit:  

To the original poster, I forgot that you were running 32-bit.  Here is a link to 10.3 beta:

[http://labs.adobe.com/downloads/flashplayer10-3.html](http://labs.adobe.com/downloads/flashplayer10-3.html)

---

### Post by dreamsR4living on 2011-03-10
> **dreamsR4living said:**
> In Chrome flash doesn't work at all, while in Firefox it is also not working as it should. Most of it works, but youtube is refusing to play.

I did;

```
sudo apt-get purge adobe-flashplugin && sudo apt-get install adobe-flashplugin
```

It fixed my Firefox Youtube problem.

But Chrome is still acting the same. Only when it is running flash for some time it sometimes suddenly starts working after a page reload.

---

### Post by eyco on 2011-03-12
hi i have flash problem to. cant see videos on youtube only! clip is running but no picture. i try'd opera, chrome, and firefox.
whan i installed the flash for the first time i can see youtube video only once, and in the next video theres no picture only voice.
up to date flash from adobe.

---

### Post by polardude1983 on 2011-03-12
> **simonmoon42 said:**
> I would try installing Chromium instead... It just seems more stable to me. I used to have flash issues all the time, but since I switched Chromium they've all gone away. Flash needs to die... soon.

Me I had the opposite and had to switch to chrome. On chromium flash would crash instantly when I loaded a website.

---

### Post by dioxholster on 2011-03-15
Guys I fixed it finally. The problem is not limited to any browser, its adobe flash thats the problem. What I did was disable Hardware Acceleration in the adobe flash settings menu. For me I couldnt access the settings menu and I had to reinstall chrome and make sure to have the flash-plugin, the one used by all browsers installed as well. Anyway for some reason, I cant access those settings again. Its unclickable. So if you are able to disable hardware acceleration that oughtta do it regardless of which latest flash you have.

You can change which version of flash or other SWF in the plugins page in preferences/content settings. And for firefox when playing video there is "manage content settings" in tools. I found Gnash and HTML5 to be extremely slow.

---


---
title: "I can't control the youtube videos"
date: 2010-08-08
forum: General Help
---

### Post by chechenia007 on 2010-08-08
Ok i have this problem: i am using epiphany, i used firefox but flash playback is sloppy(at least in my case). Ok wathever. The point is that i can play a video very nicely from youtube but can't control it, the volume the pause, it runs on it's own, and well sometimes i got to have control; not that i am such a control freak but i guess you get the point. I don't seem to have this problem with other video sites, so maybe it's a youtube problem, and it happened recently i think, so well maybe it's a youtube problem, but if not...  

I tried updating flash, with medibuntu, im on karmic koala here, so well, where's the solution from the friendly community haha. 

I'd really appreciate if you can help me out, i don't want to use windows again so i'm seeking the help from the free community.  

Ok then i expect a quick and neat answer hahaha or the help you can give me. Altough a good step by step thing might be nice.

---

### Post by dino99 on 2010-08-08
video on youtube are "as is" and you cant make much, depend of how they have been made (poor quality)

---

### Post by lovinglinux on 2010-08-08
This usually happens when you are using the 32bit plugin on a 64bit system. If this is the case, then you need to edit the npviewer file. 

Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by chechenia007 on 2010-08-08
Oh well thanks, but i think you mistyped the file to edit, it doesn't quite opens. 
Can you check it please?

and well yes, that was a neat and perfect diagnose im using a 32 on 64 bit, thanks for the help, really, it means a lot to me.

---

### Post by lovinglinux on 2010-08-08
> **chechenia007 said:**
> Oh well thanks, but i think you mistyped the file to edit, it doesn't quite opens. 
Can you check it please?

and well yes, that was a neat and perfect diagnose im using a 32 on 64 bit, thanks for the help, really, it means a lot to me.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

[IMG]http://tinyurl.com/26b85o2[/IMG]

**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by chechenia007 on 2010-08-08
ok then i've attached the images, and couldn't execute the last batch of commands, it says that the file doesn't exists, i tried creating an empty document but no luck. Thanks in advance.[IMG]file:///home/rafael/Escritorio/Pantallazo-1.png[/IMG]

Oh and i don't have a mouse middle button, im kind of a laptop guy. and have no external mouse available.

---

### Post by Zach G on 2010-08-08
[Reply Deleted]

---

### Post by Zach G on 2010-08-08
I previously had to edit the npviewer with terminal because my flash player was acting up too, this is what my 64 bit npviewer looks like now, and what yours should. 

#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer


If editing that, and restarting your browser doesn't work try installing the flash-aid firefox add on and disabling all your other plugins in firefox (besides your default flash player) like that VLC Media plugin you got. 

[Tools > Add ons > Plugins ] 

These are the plugins I have for firefox and everything with flash works perfectly. 

Iced-Tea NPR web browser plugin
and shockwave flash player

[Flash-Aid firefox add on; [https://addons.mozilla.org/en-US/firefox/addon/161939/]](https://addons.mozilla.org/en-US/firefox/addon/161939/])

Good luck man.



[Edit; oh and this code works fine, you just have to do it a few times for it to open, it wasn't opening for me the first time, enter the code, have it open, keep it open for a while, then close and try again, keep trying it will eventually open and show the text, it's not alot, but for some reason and acts as if it was a big text file] 


"gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer"

---

### Post by chechenia007 on 2010-08-08
Ooooh maaaan!!!! thanks a freakin' lot!!!! 

all i had to do was to edit, but first to create npviewer file and put the contents in it. I had to create it with the subdirectories and all but well, what a sweet victory and all thanks to you and the free community 

Now youtube works cool. everything is healing nicely

I used thunar to navigate and create the file, And used ```
sudo thunar
```r to gain root privileges, dont know how to do that on nautilius.

And now if you excuse me i got a lot of freakazoid and monty python to watch. :D

---

### Post by lovinglinux on 2010-08-08
> **chechenia007 said:**
> Oh well thanks, but i think you mistyped the file to edit, it doesn't quite opens. 
Can you check it please?

and well yes, that was a neat and perfect diagnose im using a 32 on 64 bit, thanks for the help, really, it means a lot to me.

> **chechenia007 said:**
> Ooooh maaaan!!!! thanks a freakin' lot!!!! 

all i had to do was to edit, but first to create npviewer file and put the contents in it. I had to create it with the subdirectories and all but well, what a sweet victory and all thanks to you and the free community 

Now youtube works cool. everything is healing nicely

I used thunar to navigate and create the file, And used ```
sudo thunar
```r to gain root privileges, dont know how to do that on nautilius.

And now if you excuse me i got a lot of freakazoid and monty python to watch. :D

For graphical programs you should use gksudo instead of sudo.

---


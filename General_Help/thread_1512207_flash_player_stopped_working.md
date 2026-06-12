---
title: "flash player stopped working"
date: 2010-06-17
forum: General Help
---

### Post by mick463 on 2010-06-17
:confused:Hi i am running an asus laptop with 10.04 lucid 64 bit.I had adobe flash working fine through google chrome but not firefox but i did not care as google chrome still worked. Today i updated my ubuntu and flash just stopped working all together now i can not access my cisco .netacad.net site and i need to.I have tried to fix it to no avail can any one please help a new to ubuntu person that is sick of windows. Thank you in advance.

---

### Post by Vaphell on 2010-06-17
```
about:plugins
``` in address bar to see if flash plugin is detected by ff

if not then follow
[http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/Adobe-Flash-Player-for-64-bit-Linux-42958.shtml)

Above is for 64 bit. There is newer version of flash, but it's 32 bit and is used with wrapper - that option should be available in repository (flashplugin-installer package)

---

### Post by mick463 on 2010-06-17
Hi thank you but how do i do this part.

Unpackage the file. A directory which contains libflashplayer.so will be created.
6. Copy libflashplayer.so to ~/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet.
 Thank you.

---

### Post by wojox on 2010-06-17
Go into the .mozilla directory and run this command

```
mkdir plugins
```

---

### Post by Vaphell on 2010-06-17
GUI way: in nautilus press ctrl+h to show hidden stuff, find .mozilla, create new dir inside, copy-paste libflashplayer.so there

command line way:
```

cd .mozilla
mkdir plugins
cp ~/Desktop/libflashplayer.so plugins

```

---

### Post by mick463 on 2010-06-17
How do i get to the .mozilla dir.
I have unpacked it to my desktop now i have a file there called 
libflashplayer.so and that is as far as i have got

---

### Post by Vaphell on 2010-06-17
i already explained that
run nautilus, go to your home folder, press ctrl+h (or show hidden files from menu) and it should be right there

---

### Post by wojox on 2010-06-17
Open a terminal and follow Vaphell commands. :p

---

### Post by thornomad on 2010-06-17
> **mick463 said:**
> :Today i updated my ubuntu and flash just stopped working all together now i can not access my cisco .netacad.net site and i need to.

I can say I had the same experience -- after Google announced native support in Chrome for Flash, it began working (as expected).  Recently, however, even with a fresh install of Ubuntu and Chrome, I no longer have any Flash.

I'm not sure if this is a Chrome problem but am wondering if other people still have native Flash support from Chrome ...

---

### Post by Vaphell on 2010-06-17
btw i encourage you to try the command line way of fixing stuff, despite it being confusing or downright scary - been there, done that :). It has a great advantage when you look for help at the forums - you can copy paste stuff verbatim (highlight and middleclick-paste into terminal line by line) and things just work, even across different linux flavors with different UIs.

of course understanding the commands is desirable, otherwise someone would be able to convince you to destroy your system and you wouldn't notice :)

---

### Post by mick463 on 2010-06-17
Thankyou for all your help and patience it was realy apreciated.It worked a treat.Now my firefox even works you are the man.

---

### Post by mick463 on 2010-06-17
Yay

---


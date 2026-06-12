---
title: "Ubuntu 10.04 startup is extremely slow"
date: 2010-05-02
forum: General Help
---

### Post by Chataqua on 2010-05-02
Hi!
 
I have a Lenovo IdeaPad S12, where I've just installed the new Ubuntu 10.04. The system works great, it's quite fast, actually it feels faster than Ubuntu 09.10 Netbook Remix which I had installed on it until this friday.
 
Now, when I turn this computer on, it's a quite different story. I get the boot-screen with the Lenovo logo etc, and then it goes to a screen with only a _-marker, which blinks for about 2 minutes and 45 seconds. After that the boot-session for Linux starts, and it only uses 15 seconds from that point until I've logged in to my computer.
 
My question is; does anyone have this same problem, or is it just me? And; why does my computer freez for almost 3 minutes before anything happens? Is this a bug in Ubuntu 10.04, or is it simply a hardware-error in my computer? I've never encountered this problem on my computer before, so I might wonder if it is a software-error. Any thoughts?

---

### Post by Aly007 on 2010-05-02
I also have this problem in 10.04, never had it in 9.10 Karmic. 
I got this blank screen with a "_ ..." blinking for ~8 seconds then i see the Ubuntu logo and after ~2 sec it disappear and now comes startup which is also slow, about 10 seconds to startup. Pidgin launch instantly but those two panels comes out very slow.

---

### Post by fatleader on 2010-05-02
Also got the same problem here, just not nearly as bad..
My "-" flashes for around 20 seconds, then loads into the ubuntu login screen.

Still really bothers me though since bootup time back in 9.10 was around 10 seconds.

---

### Post by boom2k1 on 2010-05-02
I still find no improvement in boot speed vs. 9.10, or it could be slower. (I didn't time it.)

About the blinking cursor, see the web page 

[http://ubuntuforums.org/showthread.php?p=9218536](http://ubuntuforums.org/showthread.php?p=9218536)

---

### Post by sandman3838 on 2010-05-02
I'm also having the same issue?
Ubuntu 9.10 was faster!

Also I have to say that I really hate that Purple Splash screen.  
It's ugly and too large.

---

### Post by xantone on 2010-05-02
[FONT=Times New Roman][SIZE=3]Hi there I have tried the suggestion by **bomm2k1** went to the add [/SIZE][/FONT][COLOR=black][FONT=Verdana][[COLOR=#444444]http://ubuntuforums.org/showthread.php?p=9218536[/COLOR]]("http://ubuntuforums.org/showthread.php?p=9218536") [/FONT][/COLOR][FONT=Times New Roman][SIZE=3]and it work, just go to step No.4 and follow the instruction there I change mine to:[/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]GRUB_GFXPAYLOAD_LINUX=640x480[/FONT][/COLOR]**
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The steps go like this:[/SIZE][/FONT]
**[COLOR=black][FONT=Verdana]4. Bootup/Plymouth. [/FONT][/COLOR]**[COLOR=black][FONT=Verdana]
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[[COLOR=#444444]https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013")

Graphical solution : [[COLOR=#444444]http://news.softpedia.com/news/How-t...4-140810.shtml[/COLOR]]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]gksu /etc/default/grub[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** Save the file and run [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Code:[/FONT][/COLOR]
[COLOR=black][FONT=Courier New]sudo update-grub[/FONT][/COLOR]

[COLOR=black][FONT=Verdana]The resolution chosen should be your monitors native resolution.[/FONT][/COLOR]

---

### Post by Mrs Twaddle on 2010-05-03
I can't access either of those pages, so no idea if they are relevant to me.

---

### Post by Mazz35 on 2010-05-03
How do you make your text bold in gedit?

---

### Post by coolcaseley67 on 2010-05-03
hi  everyone 
[U]
The issue is Plymouth [/U]
Proprietary 'ATI/NV' drives are not designed to run in UMS ;user  space' and Plymouth works with KMS 'kernel mode'. All OSS drivers use  KMS.  this is way your start is slow
see [http://ubuntuforums.org/showthread.php?t=1462437](http://ubuntuforums.org/showthread.php?t=1462437)

---

### Post by MrPok on 2010-05-03
> **Mazz35 said:**
> How do you make your text bold in gedit?
xantone only wanted to *emphasize* that you should _add_ this.
(It doesn't need to be bold, and "1680x1050" might be different on your computer depending on the maximal resolution of your monitor or laptop screen)

---

### Post by Mazz35 on 2010-05-04
Thanks..I guess will just wait till they fix this bug.

---

### Post by mario.cesar2509 on 2010-05-05
Same for me. I installed Lucid Lynx today and the boot is really slow, more than with Karmic Koala. Also waking up from Hibernate and Suspension is sensible slower.

---

### Post by Epaminond on 2010-05-08
I also run Lucid on Lenovo IdeaPad S12. And I don't have such a problem. )
Did you try to put your sata to compatibility mode in bios?

---

### Post by Chataqua on 2010-05-09
Thanks. I just put the SATA in comtibility mode, and that did the trick. I'm now down to 30 seconds from I turn the computer down untill the login screen appears. 

Still got the blinking cursor, though.

---

### Post by philinux on 2010-05-09
See the forum sticky for full info, to date, re boot up.

---

### Post by lostinwoods on 2010-08-03
Hi All

I searched this in google to see if only I'm having this problem. Seems like quite a few people are having same.

I have installed Ubuntu 10.04 via VMWare, I have been using Ubuntu like this for a while now but this version is extremely slow which is annoying coz MS is trying to reduce boot up time and can see effort in WIn 7 however OS is a ****; anyway I expect Ubuntu team to try few things and test user tolerance limit but not with bootup time.

Someone has something else to add please go ahead.

---


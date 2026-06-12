---
title: "Beginner needs help fixing Plymouth resolution"
date: 2010-06-07
forum: General Help
---

### Post by Cosmogirl on 2010-06-07
Hi,

Have just upgraded to 10.04 and apparently like a lot of people I'm having problems with slow start-up and Plymouth.  Haven't made much progress with the start-up time but I'd like to improve the low resolution of Plymouth.  So I found this page:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

and tried to follow the instructions given in 'Alternative One' but when I get to step 2 and run: 

gksu gedit /etc/default/grub

a new window opens but it's blank - no text.  Now why is that please?  And how can I access the grub file?

Sorry if these seem like stupid questions but we all have to start somewhere...

Thanks in advance for your help!

---

### Post by WinterRain on 2010-06-07
Try doing
```
sudo update-grub
```
first.

---

### Post by Cosmogirl on 2010-06-07
Thanks for your reply.  I tried ```
sudo update-grub
``` and then ran ```
 gksu gedit /etc/default/grub
``` but the new window still came up blank.  Any ideas?

---

### Post by davidmohammed on 2010-06-07
go to administration - synaptic manager and type in the search box

grub

which grub is installed

grub

or 

grub-pc?

if its grub, suggest you upgrade to grub2 by following [this page]("http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/").

---

### Post by Cosmogirl on 2010-06-08
Davidmohammed, the version I have is grub.  So I tried to upgrade to grub-pc following the steps on the page you recommended: 
[http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/](http://www.unixnewbie.org/how-to-easily-upgrade-grub-2/)

However when I got to step 3 c), I got the message:

> The following command line was extracted from /etc/default/grub or the 'kopt' parameter in GRUB Legacy's menu.lst. Please verify that it is correct, and modify it if necessary.

Linux command line:
________________________________________________


The command line is blank.  Is this normal?  Didn't go any further with the upgrade as I wasn't sure about this.

Thanks for your help!

---

### Post by User 04 on 2010-06-09
&#65279;&#65279;&#65279;&#65279;[COLOR=#0000ff]Information below is a variation of the Softpedia instructions, but just using a terminal. [/COLOR]
 
[COLOR=#0000ff]This should work, in a 32 bit installation, if it doesn't then suggest a re installation of the OS. [/COLOR]
 
[COLOR=#0000ff]Also see [www.eeemc.com/]("http://www.eeemc.com/")[/COLOR]


[COLOR=#0000ff]Your OS should be running grub2, if not run,

root@computer:~# apt-get install grub2[/COLOR]

 
 
[COLOR=#0000ff]*Fixing Plymouth's resolution, *[/COLOR]
 
 
[LEFT]*[COLOR=#ff6600]Step 1: Access Applications > Accessories > Terminal[/COLOR]*[/LEFT]
 
 
[LEFT][COLOR=#008080]*Enter sudo -i *[/COLOR]
*[COLOR=#008080]and enter normal password as requested.[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]Example,[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]user@computer:~$ sudo -i[/COLOR]*
*[COLOR=#008080][sudo] password for user: [/COLOR]*
*[COLOR=#008080]root@computer:~# [/COLOR]*[/LEFT]
 
[LEFT][COLOR=#008080]*Then enter,*[/COLOR][/LEFT]
 
[LEFT]*[COLOR=#008080]apt-get install v86d[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]or you can use synaptic to install v86d.[/COLOR]* [/LEFT]
 
 
[LEFT][COLOR=#ff6600]*Step 2: *[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#008080]*gedit /etc/default/grub*[/COLOR][/LEFT]
 
[LEFT]*[COLOR=#008080]- Replace the following line ( line number 9 ):[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]with this one:[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080][I][COLOR=#008080]- Replace the following line ( line number 18 ):[/COLOR]*[/COLOR][/I][/LEFT]
 
[LEFT]*[COLOR=#008080]#GRUB_GFXMODE=640x480[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]with this one:[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]GRUB_GFXMODE=1280x1024[/COLOR]* [/LEFT]
 
[LEFT][COLOR=#008080]*&#65279;Save the file and close it!*[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#ff6600]*Step 3: *[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#008080]*gedit /etc/initramfs-tools/modules*[/COLOR][/LEFT]
 
[LEFT]*[COLOR=#008080]When the text window appears, add the following line at the end of the file:[/COLOR]*[/LEFT]
 
[LEFT]*[COLOR=#008080]uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap[/COLOR]* [/LEFT]
 
[LEFT][COLOR=#008080]*&#65279;Save the file and close it!*[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#ff6600]*Step 4:*[/COLOR] [/LEFT]
 
 
[LEFT][COLOR=#008080]*echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash*[/COLOR] [/LEFT]
 
 
[LEFT][COLOR=#008080]*&#65279;*[/COLOR][COLOR=#ff6600]*Step 5: *[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#008080]*sudo update-grub2*[/COLOR] [/LEFT]
 
 
[LEFT][COLOR=#008080]*&#65279;*[/COLOR][COLOR=#ff6600]*Step 6:*[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#008080]*sudo update-initramfs -u *[/COLOR][/LEFT]
 
 
[LEFT][COLOR=#008080]*&#65279;*[/COLOR][COLOR=#ff6600]*Step 7: Reboot your computer. When the system starts, you should see a better looking Ubuntu logo!*[/COLOR][/LEFT]

---

### Post by Cosmogirl on 2010-06-11
Thanks for replying, User O4.  However the problem I have is at step 2

gedit /etc/default/grub

I have no text!  So I can't change line 9.  I presume this is because the wrong version of grub is installed.

So I tried installing grub 2 as suggested but got stuck.  See above - linux command line blank: is this normal?  Don't want to proceed with installation if there should be some code on this line, as I'd like to have grub working so as to be able to start my computer!  

If you can provide any help that would be great.

---

### Post by dcstar on 2010-06-12
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Cosmogirl on 2010-06-12
Thanks David!

That solved my problem.  Bless you and all your 9,174 beans.

---

### Post by topet2k12001 on 2010-09-05
> **Cosmogirl said:**
> Hi,

Have just upgraded to 10.04 and apparently like a lot of people I'm having problems with slow start-up and Plymouth.  Haven't made much progress with the start-up time but I'd like to improve the low resolution of Plymouth.  So I found this page:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

and tried to follow the instructions given in 'Alternative One' but when I get to step 2 and run: 

gksu gedit /etc/default/grub

a new window opens but it's blank - no text.  Now why is that please?  And how can I access the grub file?

Sorry if these seem like stupid questions but we all have to start somewhere...

Thanks in advance for your help!

Hi Friend,

I followed the same instructions in the URL you mentioned (to the dot) and it worked fine with me. Perhaps you missed out on checking the "Run In Terminal" box when you did this?

---


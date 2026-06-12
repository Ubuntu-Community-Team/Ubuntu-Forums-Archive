---
title: "problems using apt-get install"
date: 2010-05-16
forum: General Help
---

### Post by mindlessbrain on 2010-05-16
I'm trying to get Ubuntu to connect to the internet using a 3g USB Modem, specifically Sudani one mdsl model # E1750 HSPA USB Stick. 

Anywhoodle I did a google search and found someone with the exact same problem who used wvdial to make everything ok. 

My problem is when I type in sudo apt-get install wvdial

I get:

jill@jill-desktop:~$ sudo apt-get install gparted
[sudo] password for jill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gparted
jill@jill-desktop:~$ 

(I guess this is from gparted, but I get the exact same thing when I try for gnome-ppp and wvdial.)

What's going on here? Do I need to be on the net to get stuff like this? How do I do that if my problem is that I'm not on the net? 

Thanks in advance for any much needed help!
MB

---

### Post by iponeverything on 2010-05-16
> What's going on here? Do I need to be on the net to get stuff like this? How do I do that if my problem is that I'm not on the net?


From a machine with an Internet connection grab the wvdial deb like so:

[http://packages.ubuntu.com/jaunty/i386/wvdial/download](http://packages.ubuntu.com/jaunty/i386/wvdial/download)
 
Where "jaunty" is replaced with your version of Ubuntu.

Put the deb on a usb drive and copy it to the machine then install it with:

dpkg -i <wvdial package>

---

### Post by mindlessbrain on 2010-05-16
Does it matter where I put the deb file? Is the desktop ok? And do I need to specify where I put it in the command? For instance is it the same command if its on the desktop?

And will that solve all my install troubles?

Thanks!

---

### Post by mindlessbrain on 2010-05-16
I tried using lucid (version 10.04) and this is what happened. Please advise. 

jill@jill-desktop:~$ dpkg -i <wvdial package>
bash: syntax error near unexpected token `newline'

Thanks!

---

### Post by warfacegod on 2010-05-16
Its a .deb file, just double click it.

---

### Post by GeorgeVita on 2010-05-17
> **mindlessbrain said:**
> I tried using **lucid **(version **10.04**) and this is what happened. Please advise. 
...**wvdial** package

Hi **mindlessbrain**, wvdial and dependencies exist into LiveCD of LL desktop version but NOT installed!
Also 'sudo apt-get install wvdial' gives the error you mentioned...

Read '[offline installation of wvdial]("http://ubuntuforums.org/showthread.php?p=7245790")' and also [post#20]("http://ubuntuforums.org/showpost.php?p=9307966&postcount=20")

Regards,
George

---


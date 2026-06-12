---
title: "can't go to tty1..."
date: 2009-12-20
forum: General Help
---

### Post by huanwng on 2009-12-20
everything was right before yesterday but, now, i just can't go to tty1.... 
for the gui terminal or tty7, it's successful to log in. and it's also no problem when i enter ternimal in gui. 
all in all i just can't go to tty1, tty2 ...till tty6... when i press ctrl + alt + f1, the only thing displaying in my screen is a little flashing white bar...the same to tty2-6. just like tell me to type sth, but when i type, nothing happens. 

i'm confused, what happen? what should i do?

ubuntu9.10 on IBM x60.

---

### Post by SecretCode on 2009-12-20
If you go to tty2 with ctrl-alt-f2, then press alt-left, do you get the same?

I think you are getting to tty1 but it does not have a running login shell (for some reason). 

What does _who --all_ say?

---

### Post by huanwng on 2009-12-22
entering tty2 and then alt + left   no reaction...><(with the same)
i typed who --all
display
mike +tty7   2009-12-22 12:50 old  1158(:0)
mike +pts/0 2009-12-22 12:55        1661 (:0,0)
surprised ,no tty1??
what should i do?

---

### Post by SecretCode on 2009-12-23
The output of ```
who --all
``` should list **all** your ttys, like this:
```
           system boot  2009-12-21 13:32
LOGIN      tty4         2009-12-21 13:32              2097 id=4
LOGIN      tty5         2009-12-21 13:32              2098 id=5
LOGIN      tty2         2009-12-21 13:32              2103 id=2
LOGIN      tty3         2009-12-21 13:32              2104 id=3
           run-level 2  2009-12-21 13:32                   last=
LOGIN      tty6         2009-12-21 13:32              2109 id=6
joe      + tty7         2009-12-21 11:34  old         3362 (:0)
joe      + pts/0        2009-12-23 09:30   .          4456 (:0.0)
LOGIN      tty1         2009-12-21 11:35              3941 id=1

```

Do you not get any LOGIN tty* lines at all?

---

### Post by huanwng on 2009-12-25
yes, only tty7 ,what should i do?
i remembered there were many other tty*, but not anymore....

---

### Post by SecretCode on 2009-12-25
Looks weird. Have you rebooted?

What is in your /etc/init/tty1.conf file?

---

### Post by LillaLux on 2009-12-25
Exactly the same issue on IBM ThinkCenter with intel 865S.
 

  I have already checked several kernel options (vga, modeset, splash etc.), which works after my upgrade from 9.04 to 9.10 days before. But all this options seems to be have no more effect.:sad:


 I am not sure to 100%, but it seems the last update on Friday cause this problem.   
 

 Any Idea? :confused:

---

### Post by pbrane on 2009-12-25
The flashing cursor with no prompt can happen if you are setting a display resolution on the kernel command line, like vga=791, that is not compatible. It seems that some things have changed with grub2. So if you are using a kernel option you may want to try botting without it to see if thats the issue.

---

### Post by LillaLux on 2009-12-26
Thanks – but the kerenl options I have already checked with and without vga and no effect.
 

 When I exececute the statement „sudo /sbin/getty -8 38400 ttyX “  (where X means 1 to 6) I can login in the corresponding console X (by CTRL ALT X).
 I have also checked the „/etc/init/ttyX.conf „ and don't found a difference between my laptop (on which is working) and my workstation (on which is not working) both on ubuntu 9.10.
 

 For me it seems the ttyX are not started during startup.
 

  Where can I take a look?

---

### Post by huanwng on 2009-12-27
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn
exec /sbin/getty -8 38400 tty1
------------------------------------------------------
this is all the code in that file.
what to do next?

---

### Post by SecretCode on 2009-12-27
I don't have anything further to suggest except googling ... nothing conclusive that I see. 

Is this installation an upgrade from an earlier Ubuntu version?

Wild idea: what happens if you run *exec /sbin/getty -8 38400 tty1* in a terminal window? (And then check ctrl-alt-f1, try tty2 as well, and check output of *who --all*)

---

### Post by LillaLux on 2009-12-27
I found the cause for my system.:P
 

 My system runs no more into run level 2. The statment „sudo runlevel“ returns status „unknown“. Maybe this is the same for your system?
 

 This was caused because I had removed in „/etc/network/interfaces“ the „lo“ (loopback)
 device. This „lo“ device is checked in „/etc/init/rc-sysinit.conf“ and therefore all further dependent jobs are blocked >>> NO run level 2.

---

### Post by huanwng on 2009-12-29
Thanks you guys SOOOOOO much !!!! LillaLux, your suggestion is great!! I finally revert my ubuntu....:)
thank you SecretCode for so many days of help, thanks.

but there is still a problem, iIm using network manager 0.7.997, and the reason why I remove interface is to solve the problem that i can't connect to the internet through ADSL using NM. if i add interface, i can't get into internet through ADSL...:( what should i do?

are there any other way to connect to ADSL without deleting interfaces???


PS, i will offer you the way i did to solve the ADSL problem.

firstly&#65292;add“NetworkManager daily trunk builds for ubuntu” PPA &#65292;

deb [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/network-manager/trunk/ubuntu](http://ppa.launchpad.net/network-manager/trunk/ubuntu) karmic main

secondly,delete the sentence“exec pppd call dsl-provider” in the file /etc/ppp/pppoe_on_boot  

thirdly, delete /etc/network/interfaces

forthly, edit "auth_admin_keep"(under the line “System policy prevents modification of system settings”) to "yes" in the file /usr/share/polkit-1/actions/org.freedesktop.network-manager-settings.system.policy

finally , restart.

---

### Post by huanwng on 2010-01-04
i have solved this problem, though i don't know the reason... i have revert the file--interface, and keep other edition of my computer. adsl is well, and all tty* is accessible now.
thank you all the people who helped me.

---


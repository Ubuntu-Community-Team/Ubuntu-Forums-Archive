---
title: "Can't type Sudo password in terminal"
date: 2010-07-04
forum: General Help
---

### Post by matsemann08 on 2010-07-04
I'm totally new with Ubuntu.
I was trying to enter sudo gedit /boot/grub/menu.lst
But it ask for a password
And when I try to type it nothing happens, it's just blank.
How do I type? :P

Thanks

---

### Post by 55 62 75 6E 74 75 6D 65 on 2010-07-04
So, when it asks for your password, type it in and press enter. This is the way it is, perhaps it is extra security or.... Anyway, once you are done, press enter. That's it. If you mess up you can hit ctr+u and start over.

Best,
...

---

### Post by an0dos on 2010-07-04
> **matsemann08 said:**
> I'm totally new with Ubuntu.
I was trying to enter sudo gedit /boot/grub/menu.lst
But it ask for a password
And when I try to type it nothing happens, it's just blank.
How do I type? :P

Thanks
Why do you need to edit menu.lst?

Just type the password and press enter.

---

### Post by overdrank on 2010-07-04
> **matsemann08 said:**
> I'm totally new with Ubuntu.
I was trying to enter sudo gedit /boot/grub/menu.lst
But it ask for a password
And when I try to type it nothing happens, it's just blank.
How do I type? :P

Thanks

Hi and welcome, it does not show the password being typed for security. Just type the password and then enter.
Also you may use the alt, F2 keys to enter commands. :)

---

### Post by philinux on 2010-07-04
> **matsemann08 said:**
> I'm totally new with Ubuntu.
I was trying to enter sudo gedit /boot/grub/menu.lst
But it ask for a password
And when I try to type it nothing happens, it's just blank.
How do I type? :P

Thanks

Please use gksudo for gui apps like gedit.

Which ubuntu version are you using?

---

### Post by matsemann08 on 2010-07-04
Ubuntu 10.04

I got the password thing to work, but when the file menu.lst opens it's just blank
I wanted to change the default starter OS, and it said that I should just open that file and change some stuff.
Any help on that matter?

---

### Post by CharlesA on 2010-07-04
10.04 uses GRUB2. It doesn't use menu.lst.

---

### Post by philinux on 2010-07-04
> **matsemann08 said:**
> Ubuntu 10.04

I got the password thing to work, but when the file menu.lst opens it's just blank
I wanted to change the default starter OS, and it said that I should just open that file and change some stuff.
Any help on that matter?

See these two bit's of info.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If that is too much info install startupmanager and use it to change the default OS. It appears is system>admin.

---

### Post by matsemann08 on 2010-07-04
Ahh ;)
Thanks

---

### Post by wheels666 on 2010-07-18
Hi - i'm also new to Ubuntu

i am unable to type my password in - it's not that it won't enter - it just wont type anything at all - i've tried a few restarts but no go - so far no terminal action, but nearly everything else works fine

[sudo] password for ian:    

i get to this bit then can't type anything in

i'm using Ubuntu 10 on a Dell GX280 with dual boot to win xp, and a microsoft keyboard which is working fine everywhere else within ubuntu

thanks

---

### Post by watupgroupie on 2010-07-18
Once again, It will NOT show as anything being typed. This is for security reasons. Just type it as you would normally and hit enter.

---

### Post by Danzopop on 2011-04-08
> **wheels666 said:**
> Hi - i'm also new to Ubuntu

i am unable to type my password in - it's not that it won't enter - it just wont type anything at all - i've tried a few restarts but no go - so far no terminal action, but nearly everything else works fine

[sudo] password for ian:    

i get to this bit then can't type anything in

i'm using Ubuntu 10 on a Dell GX280 with dual boot to win xp, and a microsoft keyboard which is working fine everywhere else within ubuntu

thanks



This issue was answered earlier on. The password is actually typed, it´s just that you cant see it. Type your password and hit enter. You will not see the password, but it will be entered. You can´t see the wind but you know it´s there when it makes stuff work.

---


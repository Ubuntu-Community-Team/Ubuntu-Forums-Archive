---
title: "how to trade the order o te boot"
date: 2010-04-24
forum: General Help
---

### Post by TurboThiago on 2010-04-24
hi guys,
 
I've installed the ubuntu 9.10 in my pc. But, I want to trade the order of the boot, because my brothers use windows. I know how to do it in the version 9.04 in the directory /boot/grub trading the configuration of the file menu.lst ,but i cannot find this same file in this new version. How should I do?
 
thanks
 
PS: my version is ubuntu 9.10 amd 64bits

---

### Post by stinkeye on 2010-04-24
In the terminal
```
gksudo gedit /etc/default/grub
```

and change this line 
```
GRUB_DEFAULT=[COLOR="Red"]0[/COLOR]
```

Counting starts at zero.

Then run
```
sudo update-grub
```

---

### Post by TurboThiago on 2010-04-24
> **stinkeye said:**
> In the terminal
```
gksudo gedit /etc/default/grub
```and change this line 
```
GRUB_DEFAULT=[COLOR=Red]0[/COLOR]
```Counting starts at zero.

Then run
```
sudo update-grub
```

I undertood how to go to the directory, but what should I change there? What do I put in place of the GRUB_DEFAULT=[COLOR=Red]0[/COLOR]

---

### Post by stinkeye on 2010-04-24
> **TurboThiago said:**
> I undertood how to go to the directory, but what should I change there? What do I put in place of the GRUB_DEFAULT=[COLOR=Red]0[/COLOR]
Count down your number of boot choices(starting at 0) on your startup screen, to the windows option and change the number to that.

Alternatively, just install startupmanager through synaptic and use that.

---

### Post by akand074 on 2010-04-24
If you prefer using a GUI to do this first install the StartUp-Manager:

```
sudo apt-get install startupmanager
```

or go to Synaptic Package manager and install it. Anyways then you can easily go to System > Administration > StartUp-Manager and play around with the Grub menu. Just a simple alternative to editing the configuration file yourself.

---

### Post by TurboThiago on 2010-04-24
> Quote:
Originally Posted by TurboThiago  
I undertood how to go to the directory, but what should I change there? What do I put in place of the GRUB_DEFAULT=0
Count down your number of boot choices(starting at 0) on your startup screen, to the windows option and change the number to that.

Alternatively, just install startupmanager through synaptic and use that.

stinkeye,

Is this number refers to the total number of systems that I have?
Do I have to alter this number? But if I alter this I'll be able to alter the order? 
Expain again please... i'm so noob....:?

> If you prefer using a GUI to do this first install the StartUp-Manager:

Code:
sudo apt-get install startupmanager
or go to Synaptic Package manager and install it. Anyways then you can easily go to System > Administration > StartUp-Manager and play around with the Grub menu. Just a simple alternative to editing the configuration file yourself.

akand074,

I don't like GUI to configure these things, I prefer the code interface. But I'll test it when i go home, where my pc is. Thank you.

Goodbye

---

### Post by stinkeye on 2010-04-24
Just count the listings on your boot selection screen.
eg If your screen looks like the attached pic
you would use 
```
GRUB_DEFAULT=[COLOR="Red"]3[/COLOR]
```

Remember counting starts at 0.

If that's wrong,see what is highlighted when you reboot and adjust accordingly.

---

### Post by TurboThiago on 2010-04-24
Very good. Thanks, I understood now. But after this, how can i alter the order? Where can i chance to put the windows first?

---

### Post by BLiNOK on 2010-04-24
Hi I have a question regarding the grub menu...when I boot i have these options:

Ubuntu 2.6.31-20-generic
Ubuntu 2.6.31-20-generic (recovery mode)
Ubuntu 2.6.31-14-generic
Ubuntu 2.6.31-14-generic (recovery mode)
windows loader

Before I upgraded I only had 3 options and now they are 5. I don't like them to be that many :redface:

My question is : can I delete the -14 entries so that I only have -20 ? I saw them in grub.cfg should I just remove them from there ? I also installed startup manager but it doesn't have an option to remove entries..

---

### Post by stinkeye on 2010-04-24
[_**[COLOR="DarkRed"]The Grub 2 Guide[/COLOR]**_]("http://ubuntuforums.org/showpost.php?p=7505203&postcount=1")

From the README  in the /etc/grub.d directory you'll see that the scripts are loaded in a certain order.
The 30_os-prober script is the one which produces the windows entry.
If you change it's name to
```
09_os-prober
``` it will load first.

Then you will have to have
```
GRUB_DEFAULT=[COLOR="Red"]0[/COLOR]
```
in your /etc/default/grub file for it to be highlighted on boot.

Run ```
sudo update-grub
```
for changes to take affect.

Make backups in case you stuff up something.

---

### Post by TurboThiago on 2010-04-24
i've read part of the that guide and I have something that I would to ask: 
this file "/boot/grub/grub.cfg" is the same of the "/boot/grub/menu.lst", isn't it? So Can I trade the options there? Can I put windows 7 in the first option?

Is there something diferent in the ubuntu 9.10 64bit?

---

### Post by stinkeye on 2010-04-24
> **TurboThiago said:**
> i've read part of the that guide and I have something that I would to ask: 
this file "/boot/grub/grub.cfg" is the same of the "/boot/grub/menu.lst", isn't it? So Can I trade the options there? Can I put windows 7 in the first option?

Is there something diferent in the ubuntu 9.10 64bit?

*/boot/grub/grub.cfg* and */boot/grub/menu.lst* are not the same.


See edit in previous post.

---

### Post by TurboThiago on 2010-04-24
So I have to find the number that refers to windows in this "/etc/grub.d" and change it to 09. Why 09? Is it the first? 

I think i'll just change the number of the default to last of my boot list. It's easier.

Thank you very much  now I understand. Bye

---

### Post by stinkeye on 2010-04-24
If your having trouble understanding grub2 I suggest you leave it as it is
and just use startupmanager to change your default boot selection.

---

### Post by BLiNOK on 2010-04-24
> **BLiNOK said:**
> Hi I have a question regarding the grub menu...when I boot i have these options:

Ubuntu 2.6.31-20-generic
Ubuntu 2.6.31-20-generic (recovery mode)
Ubuntu 2.6.31-14-generic
Ubuntu 2.6.31-14-generic (recovery mode)
windows loader

Before I upgraded I only had 3 options and now they are 5. I don't like them to be that many :redface:

My question is : can I delete the -14 entries so that I only have -20 ? I saw them in grub.cfg should I just remove them from there ? I also installed startup manager but it doesn't have an option to remove entries..

Alright I've found a solution to my problem and it worked:

> IcemanV9
April 25th, 2008, 01:55 PM

That is perfectly normal. You have two kernels installed. If -16 causes the problem, then you can fall back to -14 until the fix is implemented for -16. If you don't have a problem with -16 and STILL want to remove -14. Then, you type in the terminal ...
sudo aptitude purge linux-image-2.6.24-14-generic
The grub will be updated automatically.

A big advantage for ubuntu as oposed to other distros is that there is soo much information about troubleshooting it in the internet and the ubuntu forum.Ubuntu is great for newbies to linux like me.

---


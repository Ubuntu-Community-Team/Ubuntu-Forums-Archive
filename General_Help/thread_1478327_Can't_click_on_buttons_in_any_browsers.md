---
title: "Can't click on buttons in any browsers"
date: 2010-05-09
forum: General Help
---

### Post by applehead on 2010-05-09
HI

upgraded to 10.4

on many web pages, when I click on a button, nothing happens. If I hover over the button, the cursor turns to a pointing hand but that's it.

I've tried firefox, cromium, epiphany and arora, they're all the same.

I think it's just on flash content, some things work, some don't and I cant tell the difference between them. Tried install flash again and tried gnash which I couldnt get to appear in the pluggins list.

Ant ideas?

---

### Post by applehead on 2010-05-14
if I disable visual effects, that solves the problem.

Not entirely solved though if I cant have visual effects.

---

### Post by applehead on 2010-06-05
This still isn't solved. If I enable normal or extra visual effects, the buttons on web pages don't work.

I have a Nvidia card and am using the non proprietary drivers.

---

### Post by lovinglinux on 2010-06-05
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by applehead on 2010-06-06
Thanks. flash-aid hasn't worked, worth a try though.

I cant believe I'm the only one with this problem.

As an example of my problem, if I go to this online game:

bumperball.com

the first page on that site gives the option of one or two players. When I move the cursor over one of the buttons, the button lights up and the cursor turns into a pointing hand. When I click on it, it looks like it has responded but nothing happens, I'm just stuck on that page until I disable visual effects. Then everything works fine.

I've now been without visual effects since upgrade to 10, which is such a shame since it looks so good.

---

### Post by WorMzy on 2010-06-06
Are you using 32-bit or 64-bit Ubuntu?

I'm going to assume 64. If you're using 32, don't follow this advice.

* Open up software sources (System -> Administration -> Software Sources) and click Add.
Enter the following info:
```
Type:         Binary
URI:          http://ppa.launchpad.net/sevenmachines/flash/ubuntu
Distribution: lucid
Components:   main
```
and hit OK.

It'll probably ask you to reload package information, allow it to do so.

* Open Synaptic (System -> Administration -> Synaptic Package Manager) and search for flash.
Uninstall anything like flashplugin-nonfree, flashplugin-installer, gnash, etc, then install flashplugin64-installer.

That should fix the problems. Also, you don't need to have desktop effects turned off.

---

### Post by applehead on 2010-06-06
Thanks, that works!

It asked me for the complete apt line so I entered:

deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) lucid main

That seems to work fine.

I am using an AMD 64 but the 32 bit version of Ubuntu so I never Know what to choose when asked if my system is x32 or x64. I wonder if I should get a 32bit machine.

---

### Post by lovinglinux on 2010-06-06
> **applehead said:**
> Thanks, that works!

It asked me for the complete apt line so I entered:

deb [http://ppa.launchpad.net/sevenmachines/flash/ubuntu](http://ppa.launchpad.net/sevenmachines/flash/ubuntu) lucid main

That seems to work fine.

I am using an AMD 64 but the 32 bit version of Ubuntu so I never Know what to choose when asked if my system is x32 or x64. I wonder if I should get a 32bit machine.

That doesn't make sense, since that tutorial is for 64bit. Besides, FLASH-AID should detect the browser architecture and install the 64bit flash too, which solves that problem with unclickable flash content.

So, what version of flash did FLASH-AID prompt for installation?

---

### Post by WorMzy on 2010-06-06
Just fyi, the names AMD64 and Intel 80386 (i386) don't mean that they will only work on AMD/Intel processors, they're just architectures named after their respective developers. 64-bit processors will run either AMD64 or i386 OS' with no problems, but 32-bit processors cannot run AMD64 OS'.

I think you're mistaken about which version of Ubuntu you're using. Opening a terminal and running "uname -m" (no quotes) will tell you whether you're using 32-bit (x86_32) or 64-bit (x86_64) Ubuntu. If you really are running 32-bit Ubuntu, then you shouldn't be able to run the 64-bit flash plugin (as far as I'm aware).

---

### Post by lovinglinux on 2010-06-06
> **WorMzy said:**
> Just fyi, the names AMD64 and Intel 80386 (i386) don't mean that they will only work on AMD/Intel processors, they're just architectures named after their respective developers. 64-bit processors will run either AMD64 or i386 OS' with no problems, but 32-bit processors cannot run AMD64 OS'.

I think you're mistaken about which version of Ubuntu you're using. Opening a terminal and running "uname -m" (no quotes) will tell you whether you're using 32-bit (x86_32) or 64-bit (x86_64) Ubuntu. If you really are running 32-bit Ubuntu, then you shouldn't be able to run the 64-bit flash plugin (as far as I'm aware).

Also in Firefox, go to Help >> About Firefox to see the browser architecture.

---

### Post by applehead on 2010-06-07
Well I'm astonished to learn that after running uname -m, I have a 64 bit OS, and after checking about forefox, I have x64 browser. how'd that happen.

The problem I have now is that my browsers keep crashing on pages with flash stuff (apart from chromium). If I swap flashplugin64 with flashplugin, it works fine, but then I have the original problem of unclickable flash content.

any ideas?

I just tried flash-aid again an sure enough, it detected 64 bit. Don't know why it didn't the first time.

---

### Post by WorMzy on 2010-06-07
flashplugin64-installer has worked fine for me on every site I've come across so far.. if that's not working for you, then I'm out of ideas. Just to make sure, you are sure it's a flash issue, right? Not a Java issue? Because Java is another tricky area on 64-bit Ubuntu.

---

### Post by applehead on 2010-06-07
must be flash.

if I disable flash plugin, it doesnt crash, I enable it, it does. for example if I go to [http://www.guardian.co.uk/multimedia](http://www.guardian.co.uk/multimedia)
the browser closes.

I too am out of ideas

---

### Post by WorMzy on 2010-06-07
It works fine for me. Are you sure you uninstalled all other flash plugins?

---

### Post by applehead on 2010-06-08
> **WorMzy said:**
> It works fine for me. Are you sure you uninstalled all other flash plugins?

I did a search and found nothing flash. I think flash-aid purges all things flash first.

I'm just going to have to use 32 bit flash with no effects for the foreseeable future.

---

### Post by lovinglinux on 2010-06-08
> **applehead said:**
> I did a search and found nothing flash. I think flash-aid purges all things flash first.

Yes, it does.

> **applehead said:**
> I'm just going to have to use 32 bit flash with no effects for the foreseeable future.

I think I saw an alternative solution for those with 32bit, but I can't find it right now.

---

### Post by applehead on 2010-06-13
Since I can't find a solution, and since it seems to be fine on every one else's system, I wonder if I should buy a different graphics card. Can anyone recommend one that will work?  

By the way I tried a 32 bit install of linux mint, still same problem.

---

### Post by lovinglinux on 2010-06-13
Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by kokonobs on 2010-06-13
Same problem here. Using a 64bit system. It appears to install the 32bit with nspluginwrapper. Iplayer buttons dont work :(

---

### Post by applehead on 2010-06-13
> **lovinglinux said:**
> Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

IT WORKS!!!

I have effects enabled and I'm using flash stuff in firefox!

Thank you very much.

What was that line I added? How does that work?

---

### Post by applehead on 2010-06-13
> **kokonobs said:**
> Same problem here. Using a 64bit system. It appears to install the 32bit with nspluginwrapper. Iplayer buttons dont work :(

have you tried everything in this thread? I don't know weather to mark this as solved or not...

---

### Post by lovinglinux on 2010-06-13
> **applehead said:**
> IT WORKS!!!

I have effects enabled and I'm using flash stuff in firefox!

Thank you very much.

What was that line I added? How does that work?

I don't know exactly, but this is the most popular workaround posted in the forums and most users say it works.

---

### Post by Bryan55 on 2010-06-13
Thanks Lovinglinux.

This worked for me.
> 
Try this:

     Code:
     gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer 
Add the following line before the last line:

     Code:
     export GDK_NATIVE_WINDOWS=1 
Save and restart the browser.Bryan.

---

### Post by kokonobs on 2010-06-14
> Quote:
Originally Posted by kokonobs View Post
Same problem here. Using a 64bit system. It appears to install the 32bit with nspluginwrapper. Iplayer buttons dont work

have you tried everything in this thread? I don't know weather to mark this as solved or not...

Did not work for me sadly. Thanks though
------------
Edit: Works now.. Would help if i read the instructions properly. The 

```
export GDK_NATIVE_WINDOWS=1
```

Should come before the last line. That was my error. Thanks

---

### Post by lovinglinux on 2010-06-14
> **kokonobs said:**
> Did not work for me sadly. Thanks though

Have you restarted the browser?

Try to disable hardware acceleration. Perhaps it helps. Right-click the video, select properties.

---

### Post by lovinglinux on 2010-06-28
> **kokonobs said:**
> Did not work for me sadly. Thanks though
------------
Edit: Works now.. Would help if i read the instructions properly. The 

```
export GDK_NATIVE_WINDOWS=1
```

Should come before the last line. That was my error. Thanks

It is stated on the instructions that it should be placed before the last line. Anyway, I'm glad you fixed it.

---


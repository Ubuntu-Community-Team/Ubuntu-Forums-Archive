---
title: "Grub shows old kernel version"
date: 2011-11-30
forum: General Help
---

### Post by faixan on 2011-11-30
Hi,

i'm using Ubuntu Maverick Meerkat WUBI, installed on XP SP2, after installation when i did my first update about a little more than a year ago may be, the kernel version was updated as well: 2.6.35-23 at that time.

i've just updated it again after several more updates in the past, but Grub as well as terminal after booting, keep showing the version to be same as above where as during the update the version was shown to be 2.6.35-31.

what could be the problem, and how can i fix this please?

---

### Post by crazy bird on 2011-11-30
So, if you type the command **uname -r** in a terminal, the output shows you the older kernel version? 
 
Try removing every older kernel version using synaptic (synaptic shows you in a better way which is the latest version) and type this command in a terminal: **update-grub**. What happens then?

---

### Post by faixan on 2011-11-30
> **crazy bird said:**
> So, if you type the command **uname -r** in a terminal, the output shows you the older kernel version? 
 
Try removing every older kernel version using synaptic (synaptic shows you in a better way which is the latest version) and type this command in a terminal: **update-grub**. What happens then?

here's the terminal output for uname -r
```

user@ubuntu:~ $uname -r
2.6.35-23-generic

```

and i'm trying to find kernel version in synaptic, but unable to find, could you please provide a detailed path to it in synaptic?

---

### Post by rattskjelke on 2011-11-30
In the Synaptic search box typing
**linux-headers** or **linux-image**
Will show what versions are installed.

---

### Post by faixan on 2011-11-30
> **rattskjelke said:**
> In the Synaptic search box typing
**linux-headers** or **linux-image**
Will show what versions are installed.


here's the result of search of **linux-image**

---

### Post by crazy bird on 2011-12-01
You have the latest version installed, 2nd from the bottom: linux-image-2.6.35-23-generic.
 
What you must do now is removing all the other files starting with linux-image- except for the latest version since you don't need the older version to be installed. The run **update-grub** in a terminal. 
 
What happens if you do this?

---

### Post by faixan on 2011-12-01
> **crazy bird said:**
> You have the latest version installed, 2nd from the bottom: linux-image-2.6.35-23-generic.
 
What you must do now is removing all the other files starting with linux-image- except for the latest version since you don't need the older version to be installed. The run **update-grub** in a terminal. 
 
What happens if you do this?


understood, 
i've loads of stuff running in this install, which i don't really want removed or crashed, so just to re-assure myself i need to ask this from you as i have no idea of consequences of this action that you've asked me to do, is it safe, it wouldn't crash or any thing like that or is there a chance of something like that happening here? :( :confused:

---

### Post by faixan on 2011-12-01
> **crazy bird said:**
> You have the latest version installed, 2nd from the bottom: linux-image-2.6.35-23-generic.
 


and, ummm...

**linux-image-2.6.35-23**

this is the latest one?

---

### Post by crazy bird on 2011-12-01
> **faixan said:**
> and, ummm...
 
**linux-image-2.6.35-23**
 
this is the latest one?
 
My apologies! The latest version you have is linux-image-2.6.35.31! My mistake, i've mixed up the version you see in Grub and the latest version.
Remove all the others except linux-image-2.6.35.31! Then do update-grub.

---

### Post by faixan on 2011-12-01
> **faixan said:**
> understood, 
i've loads of stuff running in this install, which i don't really want removed or crashed, so just to re-assure myself i need to ask this from you as i have no idea of consequences of this action that you've asked me to do, is it safe, it wouldn't crash or any thing like that or is there a chance of something like that happening here? :( :confused:

> **crazy bird said:**
> My apologies! The latest version you have is linux-image-2.6.35.31! My mistake, i've mixed up the version you see in Grub and the latest version.
Remove all the others except linux-image-2.6.35.31! Then do update-grub.


oO... no worries, thanks :)

so i take it that it's perfectly safe, no chance of crash and burns? :confused:

---

### Post by crazy bird on 2011-12-01
> **faixan said:**
> so i take it that it's perfectly safe, no chance of crash and burns?
 
Basically, no. Your system will use the latest version installed. Removing the others should not end in problems.

---

### Post by faixan on 2011-12-01
> **crazy bird said:**
> Basically, no. Your system will use the latest version installed. Removing the others should not end in problems.

well if system uses the latest version, then why does terminal show the old version? :confused:

---

### Post by crazy bird on 2011-12-01
I mean, when you remove all the other versions then your system will use the latest version.
Why the terminal shows an older version? Beats me...

---

### Post by faixan on 2011-12-01
i just looked up on google as well, no where i seem to find the answer to this question why does terminal show the older version :( :( :(

---

### Post by bcbc on 2011-12-02
What's the output of:
```
ls -al /boot
```

And:
```
df -h
```

And:
```
sudo update-grub
```

You can run all three commands in terminal (Ctrl+Alt+t), then from the menu (Edit?) select all, and Edit copy and paste back here.

---

### Post by surfer on 2011-12-02
what is the output of
```
$ dpkg -l linux-image-generic*
```

and then
```
$ sudo update-grub
```
as mentioned above should get grub to see the new kernel and boot it by default.

---

### Post by faixan on 2011-12-02
> **bcbc said:**
> What's the output of:
```
ls -al /boot
```

And:
```
df -h
```

And:
```
sudo update-grub
```

You can run all three commands in terminal (Ctrl+Alt+t), then from the menu (Edit?) select all, and Edit copy and paste back here.

**here's the output**

```

**[05:24 AM] user@ubuntu:~ $ls -al /boot **
total 139320
drwxr-xr-x  3 root root     4096 2011-12-02 23:07 .
drwxr-xr-x 23 root root     4096 2011-11-30 15:34 ..
-rw-r--r--  1 root root   705737 2010-10-17 07:02 abi-2.6.35-22-generic
-rw-r--r--  1 root root   705862 2010-11-24 16:21 abi-2.6.35-23-generic
-rw-r--r--  1 root root   705861 2010-12-02 12:07 abi-2.6.35-24-generic
-rw-r--r--  1 root root   705861 2011-01-22 03:04 abi-2.6.35-25-generic
-rw-r--r--  1 root root   706021 2011-02-23 05:50 abi-2.6.35-27-generic
-rw-r--r--  1 root root   706021 2011-03-19 05:36 abi-2.6.35-28-generic
-rw-r--r--  1 root root   706300 2011-10-11 23:53 abi-2.6.35-30-generic
-rw-r--r--  1 root root   706300 2011-11-29 05:01 abi-2.6.35-31-generic
-rw-r--r--  1 root root   128592 2010-10-17 07:02 config-2.6.35-22-generic
-rw-r--r--  1 root root   128592 2010-11-24 16:21 config-2.6.35-23-generic
-rw-r--r--  1 root root   128614 2010-12-02 12:07 config-2.6.35-24-generic
-rw-r--r--  1 root root   128615 2011-01-22 03:04 config-2.6.35-25-generic
-rw-r--r--  1 root root   128615 2011-02-23 05:50 config-2.6.35-27-generic
-rw-r--r--  1 root root   128604 2011-03-19 05:36 config-2.6.35-28-generic
-rw-r--r--  1 root root   128644 2011-10-11 23:53 config-2.6.35-30-generic
-rw-r--r--  1 root root   128644 2011-11-29 05:01 config-2.6.35-31-generic
drwxr-xr-x  2 root root     4096 2011-12-02 23:07 grub
-rw-r--r--  1 root root 10763721 2010-11-18 07:45 initrd.img-2.6.35-22-generic
-rw-r--r--  1 root root 10758844 2010-12-08 18:59 initrd.img-2.6.35-23-generic
-rw-r--r--  1 root root 10757856 2011-01-24 02:23 initrd.img-2.6.35-24-generic
-rw-r--r--  1 root root 10758068 2011-03-07 13:50 initrd.img-2.6.35-25-generic
-rw-r--r--  1 root root 10762890 2011-03-15 10:26 initrd.img-2.6.35-27-generic
-rw-r--r--  1 root root 10762962 2011-07-02 03:34 initrd.img-2.6.35-28-generic
-rw-r--r--  1 root root 10797313 2011-11-30 15:34 initrd.img-2.6.35-30-generic
-rw-r--r--  1 root root 10798151 2011-12-02 23:07 initrd.img-2.6.35-31-generic
-rw-r--r--  1 root root   165084 2010-09-24 22:14 memtest86+.bin
-rw-r--r--  1 root root   167264 2010-09-24 22:14 memtest86+_multiboot.bin
-rw-r--r--  1 root root  1830809 2010-10-17 07:02 System.map-2.6.35-22-generic
-rw-r--r--  1 root root  1831172 2010-11-24 16:21 System.map-2.6.35-23-generic
-rw-r--r--  1 root root  1831358 2010-12-02 12:07 System.map-2.6.35-24-generic
-rw-r--r--  1 root root  1831296 2011-01-22 03:04 System.map-2.6.35-25-generic
-rw-r--r--  1 root root  1831833 2011-02-23 05:50 System.map-2.6.35-27-generic
-rw-r--r--  1 root root  1832012 2011-03-19 05:36 System.map-2.6.35-28-generic
-rw-r--r--  1 root root  1833031 2011-10-11 23:53 System.map-2.6.35-30-generic
-rw-r--r--  1 root root  1833031 2011-11-29 05:01 System.map-2.6.35-31-generic
-rw-r--r--  1 root root     1192 2010-10-17 07:05 vmcoreinfo-2.6.35-22-generic
-rw-r--r--  1 root root     1192 2010-11-24 16:23 vmcoreinfo-2.6.35-23-generic
-rw-r--r--  1 root root     1192 2010-12-02 12:10 vmcoreinfo-2.6.35-24-generic
-rw-r--r--  1 root root     1192 2011-01-22 03:06 vmcoreinfo-2.6.35-25-generic
-rw-r--r--  1 root root     1192 2011-02-23 05:52 vmcoreinfo-2.6.35-27-generic
-rw-r--r--  1 root root     1192 2011-03-19 05:39 vmcoreinfo-2.6.35-28-generic
-rw-r--r--  1 root root     1192 2011-10-11 23:54 vmcoreinfo-2.6.35-30-generic
-rw-r--r--  1 root root     1192 2011-11-29 05:03 vmcoreinfo-2.6.35-31-generic
-rw-r--r--  1 root root  4289616 2010-10-17 07:02 vmlinuz-2.6.35-22-generic
-rw-r--r--  1 root root  4293488 2010-11-24 16:21 vmlinuz-2.6.35-23-generic
-rw-r--r--  1 root root  4294032 2010-12-02 12:07 vmlinuz-2.6.35-24-generic
-rw-r--r--  1 root root  4294672 2011-01-22 03:04 vmlinuz-2.6.35-25-generic
-rw-r--r--  1 root root  4294640 2011-02-23 05:50 vmlinuz-2.6.35-27-generic
-rw-r--r--  1 root root  4295344 2011-03-19 05:36 vmlinuz-2.6.35-28-generic
-rw-r--r--  1 root root  4298288 2011-10-11 23:53 vmlinuz-2.6.35-30-generic
-rw-r--r--  1 root root  4298160 2011-11-29 05:01 vmlinuz-2.6.35-31-generic
**[05:24 AM] user@ubuntu:~ $df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            9.9G  8.8G  602M  94% /
none                  982M  332K  982M   1% /dev
none                  987M  180K  987M   1% /dev/shm
none                  987M  104K  987M   1% /var/run
none                  987M     0  987M   0% /var/lock
/dev/sda3              98G   89G  8.7G  92% /host
/dev/sda5              31G   28G  3.0G  91% /media/pri
/dev/sda7             105G   97G  8.1G  93% /media/sec
**[05:24 AM] user@ubuntu:~ $sudo update-grub**
[sudo] password for user: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.35-31-generic
Found kernel: /boot/vmlinuz-2.6.35-30-generic
Found kernel: /boot/vmlinuz-2.6.35-28-generic
Found kernel: /boot/vmlinuz-2.6.35-27-generic
Found kernel: /boot/vmlinuz-2.6.35-25-generic
Found kernel: /boot/vmlinuz-2.6.35-24-generic
Found kernel: /boot/vmlinuz-2.6.35-23-generic
Found kernel: /boot/vmlinuz-2.6.35-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

> **surfer said:**
> what is the output of
```
$ dpkg -l linux-image-generic*
```

and then
```
$ sudo update-grub
```

**here's the output**
```

**[05:31 AM] user@ubuntu:~ $dpkg -l linux-image-generic***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                       Version                                    Description
+++-==========================================-==========================================-====================================================================================================
ii  linux-image-generic                        2.6.35.31.40                               Generic Linux kernel image
**[05:32 AM] userk@ubuntu:~ $uname -a**
Linux ubuntu 2.6.35-23-generic #41-Ubuntu SMP Wed Nov 24 10:18:49 UTC 2010 i686 GNU/Linux

```

---

### Post by drs305 on 2011-12-02
It looks like you are still using Grub legacy. Perhaps we can wipe off the cob webs enough to figure out your /boot/grub/menu.lst file if you post its contents.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> It looks like you are still using Grub legacy. Perhaps we can wipe off the cob webs enough to figure out your /boot/grub/menu.lst file if you post its contents.

just trying to make sure that i understand what you have asked here, you want me to post all the content of 
```

/boot/grub/menu.lst

```
?

---

### Post by faixan on 2011-12-02
and, umm... well before reading this post above by drs305, i just modified the content of menu.lst and commented out the kernels -22, -24, -25, -27 and left only -23, -30, -31

yet after doing this when i rebooted the system, grub was still showing, -22 and -23 kernels in the boot menu :confused:

/*Edit*/
the more i read stuff the more screwed i feel... :s but well, drs305 mentioned grub legacy, so i looked up on google, and came across material from help.ubuntu.com about grub2, which mentioned to be working using /boot/grub/grub.cfg, now my poor brain is a bit confused here again, if i'm using legacy, i should only have menu.lst file, not the grub.cfg, which i have in my /boot/grub/ directory... but any ways, i checked the grub.cfg file... it only has -22 and -23 kernels in it :s

---

### Post by larrypg on 2011-12-02
Just a comment...do NOT remove all of your older kernels.  You should always keep the one before the current one you are using just in case you have a problem and have to revert to it.

---

### Post by faixan on 2011-12-02
> **larrypg said:**
> Just a comment...do NOT remove all of your older kernels.  You should always keep the one before the current one you are using just in case you have a problem and have to revert to it.

that i did... but it still shows the commented out versions when i boot the system :|

---

### Post by drs305 on 2011-12-02
I would get rid of the bipolar boot system and stick with Grub 2. You can wipe it all by purging grub (grub legacy) and grub-pc and then reinstalling grub-pc, which would leave you with only Grub 2.

```
sudo apt-get update # Update repositories and check Internet connection
# Note: Do not proceed if you don't have an Internet connection.
sudo apt-get purge grub-common # Will remove Grub legacy and Grub 2
sudo apt-get install grub-pc # Installs Grub 2
```

When you purge grub, it will warn you about losing your bootloader. TAB to OK.
You will be asked if you want to include options. Most users don't need them (things like acpi=off, noapic, nomodeset, etc). TAB to OK.
When asked where to install Grub 2, use the SPACEBAR to select your boot drive. Do NOT select a partition. TAB to OK.

If you have questions, just ask. I can't guarantee this is going to solve your kernel situation, but it will make things much clearer.

The procedure is described in a bit more detail in the "Chroot" link below, although you don't need the 'chroot' or 'LiveCD' to accomplish the purge/reinstall from a working system.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> I would get rid of the bipolar boot system and stick with Grub 2. You can wipe it all by purging grub (grub legacy) and grub-pc and then reinstalling grub-pc, which would leave you with only Grub 2.

```
sudo apt-get update # Update repositories and check Internet connection
# Note: Do not proceed if you don't have an Internet connection.
sudo apt-get purge grub-common # Will remove Grub legacy and Grub 2
sudo apt-get install grub-pc # Installs Grub 2
```

When you purge grub, it will warn you about losing your bootloader. TAB to OK.
You will be asked if you want to include options. Most users don't need them (things like acpi=off, noapic, nomodeset, etc). TAB to OK.
When asked where to install Grub 2, use the SPACEBAR to select your boot drive. Do NOT select a partition. TAB to OK.

If you have questions, just ask. I can't guarantee this is going to solve your kernel situation, but it will make things much clearer.

The procedure is described in a bit more detail in the "Chroot" link below, although you don't need the 'chroot' or 'LiveCD' to accomplish the purge/reinstall from a working system.


ummm... that means my suspicion was correct, i do have both versions of grub... ?!? if so, then can you shed some light on why that might have happened? i remember most of the updates and installed i've done since i installed this ubuntu, but really don't remember messing up with grub before now...so how could this have happened?

also, if my grub-legacy is working, why didn't the commenting work? it still shows the commented out 2.6.35-22 version in the boot menu... :confused:

---

### Post by drs305 on 2011-12-02
If you have upgraded through the various releases grub legacy could have just hung around, or perhaps you installed "grub" at some point, thinking it was the same as grub-pc. EDIT: See forum member *bcbc's* explanation in Post #33.

We can get a good look at your boot files if you download/run the boot info script and post the contents of RESULTS.txt

Mind we may be straying off your original problem, but I'd say there is a decent change the two are related.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Give me a moment and I'll post a command you can run to force Grub 2 to update, which may be all you need.

Here it is:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
If you are really using Grub 2 but are editing and updating Grub legacy it would explain a few things.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> If you have upgraded through the various releases grub legacy could have just hung around, or perhaps you installed "grub" at some point, thinking it was the same as grub-pc.

We can get a good look at your boot files if you download/run the boot info script and post the contents of RESULTS.txt

Mind we may be straying off your original problem, but I'd say there is a decent change the two are related.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Give me a moment and I'll post a command you can run to force Grub 2 to update, which may be all you need.

Here it is:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
If you are really using Grub 2 but are editing and updating Grub legacy it would explain a few things.


i've the RESULTS.txt, should i post that first or run this command?

---

### Post by drs305 on 2011-12-02
> **faixan said:**
> i've the RESULTS.txt, should i post that first or run this command?

You can run the command and see what happens. Since it might update the boot files, run the boot script after trying the above and then post - unless using that command fixes things.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> You can run the command and see what happens. Since it might update the boot files, run the boot script after trying the above and then post - unless using that command fixes things.

before proceeding, just another thing i want to let you know which i have just noticed...
just rebooted my system to check which version of bootloader was actually runing
here's what was written there

**Grub Version 1.98+20100804+5ubuntu2**

don't know if that changes any thing for what we're trying to do here, but just so you know, also that i looked in the grub.cfg, it only contains 2.6.35-22 and 2.6.35-23 kernel versions. which leads me to believe that bootloader is Grub2.

should i still proceed?

---

### Post by drs305 on 2011-12-02
> **faixan said:**
> before proceeding, just another thing i want to let you know which i have just noticed...
just rebooted my system to check which version of bootloader was actually runing
here's what was written there

**Grub Version 1.98+20100804+5ubuntu2**

don't know if that changes any thing for what we're trying to do here, but just so you know, also that i looked in the grub.cfg, it only contains 2.6.35-22 and 2.6.35-23 kernel versions. which leads me to believe that bootloader is Grub2.

should i still proceed?

Yes. And that is what the problem has been. When update-grub is being run, it is updating your grub legacy menu.lst but NOT the grub 2 menu which is actually being used to boot.

Running the update-grub command as "grub-mkconfig" as I described is going to force grub to update the proper menu. 

At that point, you should get access to the latest kernel as the top item in your Grub 2 menu.

And you could continue just using 'grub-mkconfig' but purging grub would still probably be best.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> Yes. And that is what the problem has been. When update-grub is being run, it is updating your grub legacy menu.lst but NOT the grub 2 menu which is actually being used to boot.

Running the update-grub command as "grub-mkconfig" as I described is going to force grub to update the proper menu. 

At that point, you should get access to the latest kernel as the top item in your Grub 2 menu.

And you could continue just using 'grub-mkconfig' but purging grub would still probably be best.


Thanks a gazillion :) it's working now, just one last thing, i found out how to control how many kernel versions can be displayed in Grub-legacy, but how exactly can i control this number in Grub2?

---

### Post by drs305 on 2011-12-02
You could learn how to edit the Grub 2 files by clicking on some of the links in my signature line, but I wouldn't wish that on anyone. Those guides were written when manual updates were all that we could do.

Today there are a few great apps for use with Grub. A great one for tweaking Grub 2 settings is Grub Customizer. It can set the default kernel, rename and reorder titles, and lots more. Click the "Customizer" link for more information.

The number displayed can be controlled by the number of kernels you have installed on your computer, and starting with Grub 1.99 the older kernels are now hidden in a submenu so the main menu stays relatively uncluttered.

---

### Post by faixan on 2011-12-02
> **drs305 said:**
> You could learn how to edit the Grub 2 files by clicking on soem of the links in my signature line, but I wouldn't wish that on anyone. Those guides were written when manual updates were all that we could do.

Today there are a few great apps for use with Grub. A great one for tweaking Grub 2 settings is Grub Customizer. It can set the default kernel, rename and reorder titles, and lots more. Click the "Customizer" link for more information.

The number displayed can be controlled by the number of kernels you have installed on your computer, and starting with Grub 1.99 the older kernels are now hidden in a submenu so the main menu stays relatively uncluttered.

Thank you so very much for your time and effort, really been good learning two hours after a long while for me. 
Thanks again :)

---

### Post by bcbc on 2011-12-02
Glad to see you got it sorted with the help of drs305. 

One way you can get grub-legacy installed on a Wubi system is by installing LVPM which has a dependency on grub-legacy so it will remove grub2 (on the actual Ubuntu install) but this won't change the grub4dos boot mechanism which uses grub2. So likely if you installed lvpm it would have frozen grub.cfg in place since that time. That's one possibility.

---

### Post by faixan on 2011-12-02
> **bcbc said:**
> Glad to see you got it sorted with the help of drs305. 

One way you can get grub-legacy installed on a Wubi system is by installing LVPM which has a dependency on grub-legacy so it will remove grub2 (on the actual Ubuntu install) but this won't change the grub4dos boot mechanism which uses grub2. So likely if you installed lvpm it would have frozen grub.cfg in place since that time. That's one possibility.

and an absolutely correct statement, exactly how it happened, i have LVPM installed, needed to increase the size of WUBI partition, never knew it was gonna cause this issue :s another lesson well learnt :), thanks :)

---

### Post by bcbc on 2011-12-03
This will resize wubi disks: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

This will migrate a wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Until lvpm is updated (unlikely) or the wubi migration is incorporated in the live cd (planned), that's pretty much your best bet. You're a little short on space right now, but after you remove a bunch of those kernels you'll probably be okay for a little while.

---

### Post by faixan on 2011-12-03
> **bcbc said:**
> This will resize wubi disks: [http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

This will migrate a wubi install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Until lvpm is updated (unlikely) or the wubi migration is incorporated in the live cd (planned), that's pretty much your best bet. You're a little short on space right now, but after you remove a bunch of those kernels you'll probably be okay for a little while.

what i meant was that i did install LVPM quite a while ago but didn't know about it's dependencies back then, but still thanks, this technique looks easier i might need to do it someday :)
how much space can i get free by removing old kernels? i have 
2.6.35-22 to 2.6.35-31 all the kernels...

---

### Post by drs305 on 2011-12-03
Opening Synaptic and doing a search for "3.2.0-2", the installed size of the associated kernel and headers is about 200MB.

Ubuntu Tweak is a great GUI app that can make a lot of your system changes hassle-free, including removing older kernels. Here is a link for removing them, and how to use Ubuntu Tweak is included in the first post:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by faixan on 2011-12-03
> **drs305 said:**
> Opening Synaptic and doing a search for "3.2.0-2", the installed size of the associated kernel and headers is about 200MB.

Ubuntu Tweak is a great GUI app that can make a lot of your system changes hassle-free, including removing older kernels. Here is a link for removing them, and how to use Ubuntu Tweak is included in the first post:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

that is 200MB for each kernel version? that would mean having all kernels; 22, 23, 24, 25, 27, 28, 30; removing them would free me 1.4GB of space?

---

### Post by drs305 on 2011-12-03
> **faixan said:**
> that is 200MB for each kernel version? that would mean having all kernels; 22, 23, 24, 25, 27, 28, 30; removing them would free me 1.4GB of space?

No. My entire /boot folder is only 24MB. I don't know how Synaptic comes up with the installed size. When I did a find for "3.2.0-2" it found files in /boot and /var/lib/dpkg info, but the folder sizes don't come anywhere near what Synaptic reports. I don't know where everything is stored but I'd be surprised if it saves that amount of space. 

Since you don't need all those older kernels, I'd just recommend you uninstall them. If you are really interested in how much space it saves, make a note of your disk usage both before and after (and let us know how many kernels you removed and how it affected your disk space).
```
df | grep /dev/
df -h | grep /dev/
```

I'd remove an older kernel on my system just to let you know but I'm currently booted into Precise and only have one kernel installed...

---

### Post by faixan on 2011-12-03
> **drs305 said:**
> No. My entire /boot folder is only 24MB. I don't know how Synaptic comes up with the installed size. When I did a find for "3.2.0-2" it found files in /boot and /var/lib/dpkg info, but the folder sizes don't come anywhere near what Synaptic reports. I don't know where everything is stored but I'd be surprised if it saves that amount of space. 

Since you don't need all those older kernels, I'd just recommend you uninstall them. If you are really interested in how much space it saves, make a note of your disk usage both before and after (and let us know how many kernels you removed and how it affected your disk space).
```
df | grep /dev/
df -h | grep /dev/
```

I'd remove an older kernel on my system just to let you know but I'm currently booted into Precise and only have one kernel installed...

Before removing any thing.
```

[08:02 PM] user@ubuntu:~ $df -h | grep /dev/
/dev/loop0            9.9G  8.8G  600M  94% /

```
Kernel Version 2.6.35-22 Removed using Ubuntu Tweaks
```

[08:02 PM] user@ubuntu:~ $df -h | grep /dev/
/dev/loop0            9.9G  8.6G  806M  92% /

```
Kernel Version 2.6.35-24 Removed using Ubuntu Tweaks
```

[08:05 PM] user@ubuntu:~ $df -h | grep /dev/
/dev/loop0            9.9G  8.4G 1012M  90% /

```

i see a 200MB space freed for each kernel... isn't it so?

/*Edit*/
Also i want to know now, since i've not yet purged the Grub-legacy so ubuntu tweaks just updated menu.lst, i'm assuming i'm gonna have to use

```

:~ grub-mkconfig /boot/grub/grub.cfg

```
again?

---

### Post by drs305 on 2011-12-03
> **faixan said:**
> 9.9G  8.4G 1012M  90% /


i see a 200MB space freed for each kernel... isn't it so?

It looks like Synaptic was telling the truth.  ;-)

> 
Also i want to know now, since i've not yet purged the Grub-legacy so ubuntu tweaks just updated menu.lst, i'm assuming i'm gonna have to use

```

:~ **[COLOR="DarkRed"]sudo [/COLOR]**grub-mkconfig **[COLOR="DarkRed"]-o [/COLOR]**/boot/grub/grub.cfg

```
again?

Yes, except don't forget the "-o" switch in the command. You will need to run that command as long as Grug legacy remains on your system. If you don't need Grub, purging 'grub' and reinstalling 'grub-pc' should make this unnecessary.

To see which file is being updated, run "sudo update-grub" and watch to see if grub.cfg or menu.lst is being generated.

---

### Post by faixan on 2011-12-03
> **drs305 said:**
> It looks like Synaptic was telling the truth.  ;-)



Yes, except don't forget the "-o" switch in the command. You will need to run that command as long as Grug legacy remains on your system. If you don't need Grub, purging 'grub' and reinstalling 'grub-pc' should make this unnecessary.

To see which file is being updated, run "sudo update-grub" and watch to see if grub.cfg or menu.lst is being generated.

so that means i can have total of 1.4GB free space... :P 

Oo..yea... my bad, forgot the switch... thanks :) :)

another query popped in my mind this evening after looking at some stuff... i realized my internet connection menu is now showing options for wireless as well now that i'm using new kernel,which it wasn't showing when i was using older kernel... does this mean that all the updates which are installed are kernel specific, or is it only true for hardware updates and not true for software updates?

---


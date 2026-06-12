---
title: "persistent usb"
date: 2011-09-28
forum: General Help
---

### Post by skor78 on 2011-09-28
Hi,

i was wondering, is it any different to have a live usb with casper-rw persistence from having a installed version on a usb. I don't really know if this question makes sense. I don't use linux very often.

Before i used to setup the persistence from another source of a live distro, then install, etc... now persistence(?) is installed with soft like unetbootin, etc., but what i see is, persistence is the file casper-rw, and don't understand if that affects boot time (looking for/loading drivers, kernel, etc.).

Also, if a installed version is better, if it could be made like in Joli OS (you just run the live and install in the stick, choose boot option, done!).
```
[Run Jolicloud from a persistent USB stick instead of a hard drive]("http://getsatisfaction.com/jolicloud/topics/run_jolicloud_from_a_persistent_usb_stick_instead_of_a_hard_drive") 
```Thanx!

---

### Post by KBD47 on 2011-09-28
I don't know if this will help, but I run several distros on persistent usb: Lubuntu, Kubuntu, Xubuntu, Puppy Linux, Bodhi Linux, etc. Persistence is pretty easy to do on the buntu's except for the main Ubuntu because for some reason it hangs on the 'try' or 'install' menu. Puppy Linux can be made using Unetbootin because Puppy asks you to create a save file that acts as your persistence. I usually use Mint 9 using Startup Disc Creator for the other buntus with persistence, just slide the persistence control where you want it before making the live usb. These usb's are pretty fast, especially the light ones like Puppy and Lubuntu.
KBD47

---

### Post by dcstar on 2011-09-29
> **skor78 said:**
> Hi,

i was wondering, is it any different to have a live usb with casper-rw persistence from having a installed version on a usb. I don't really know if this question makes sense. I don't use linux very often.

Before i used to setup the persistence from another source of a live distro, then install, etc... now persistence(?) is installed with soft like unetbootin, etc., but what i see is, persistence is the file casper-rw, and don't understand if that affects boot time (looking for/loading drivers, kernel, etc.).
........

Persistence on a Live USB is just that - a Live USB environment that will save settings between boots. The Live USB is designed to not prematurely send the USB device to failure (on the assumption that it is a solid state "stick" device). The Persistence file on a Live USB will also eventually fill up because you do not get space back when deleting or overwriting files - this is by design.

Running a normal Linux distro on a USB stick will eventually kill it as the continuous writes to specific parts of these drives is not what they are designed for.


PS: Compared to many questions in these forums yours is certainly not "dumb"!

---

### Post by skor78 on 2011-09-29
Thanks! Both your answers have been very helpful and useful, and now lead me to a new set of doubts i hope you can still help me with.

**1st **is, I have a Asus 1201N (Atom N330 2x1.6GHz, NVidia ION, 4Gb), and i want to create a **fast/light** boot and performance distro in a **usb live persistent **stick to simple media player (via HDMI), and all basic functions, something similar to express gate, but bootable by usb. 
 [COLOR=#0000FF]Basically  something with easy access to use anywhere (bus, train, car, sidewalk), many times only for a couple of minutes, avoiding HDD use,  with fast access to basics apps such as media player or msn,  web-browser, etc. (like a smartphone, or a tablet)
[COLOR=Black]What distro would you recommend for me to accomplish this?

**2nd **question is much more complicated (maybe too much for me, but i'll try to keep up).. 
I am trying to setup on the side, a USB HDD (not a stick) with several persistent "[/COLOR][/COLOR][COLOR=Black]normal Linux distros"[/COLOR][COLOR=#0000FF][COLOR=Black], as in opposite to "live persistent" distros, and also some live distros and tools in between. Software i found to do this was YUMI and others, but they only create "persistent live", and i'm way too confused in how to proceed to create one or several normal distros in it. Also, i'd like to create a SWAP partition common to all distros.[/COLOR]
[COLOR=Black]
In example, the HDD would be:
- Mint persistent
- Mint live [/COLOR][/COLOR][COLOR=Black](to install in other machines)
[/COLOR][COLOR=#0000FF][COLOR=Black]- Ubuntu live
- Lubuntu live
- Joli OS persistent
- Puppy persistent
- Hiren's Boot
- common SWAP
- NTFS storage partition
- etc..

Thanks![/COLOR]
[/COLOR]

---

### Post by oldfred on 2011-09-29
Yoiu have to be careful with many of the flash drive installers as they totally erase flash drive as it is assumed they are dedicated smaller devices. Using that on a Hard drive may erase the entire drive.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Pros & cons of persistent install over direct install to flashdrives 
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

I have several USB flash drives. My 4GB is full of different ISO for install or repair. My 16GB is a full install in a 8GB partition. My 2GB has the Windows repairCD, but boots with grub2 and has another repair ISO or two. Note that I use grub2 everywhere. Something like when you have a hammer everything looks like a nail, I like grub2 so everything boots with it.

Full install of Ubuntu is not speedy but is functional. If you want speed Puppy or a small memory only install may be better.

---

### Post by skor78 on 2011-09-29
Wow! Allot of useful info for me to chew on the next couple of hours..

In between..
[QUOTE=oldfred]If you want speed Puppy or a small memory only install may be better.[/QUOTE]
Well, to my first question, yes, the goal is speed above all else, but i'd really like to be sure which is the best release for me before trying it again.
I tried [COLOR=#008000]Joli OS[/COLOR], that i like the interface, but it's very slow to boot and work on. I think even slower than mint. 
Also tried [COLOR=Green]androidx86[/COLOR], and even worse.
 [COLOR=#008000]Meego [/COLOR]it doesn't work on ION.
Heard about [COLOR=#008000]Puppy Linux [/COLOR]but didn't test it yet, because i was unsure if it would be faster than distros, such as [COLOR=Green]Lubuntu[/COLOR], [COLOR=Green]Xubuntu[/COLOR], [COLOR=Green]Eeebuntu[/COLOR], or any other i don't know, etc., etc., etc..
I was hoping your experienced users (like KBD47 shared in his post) could save me some time on this.
[QUOTE=oldfred]You have to be careful with many of the flash drive installers as they  totally erase flash drive as it is assumed they are dedicated smaller  devices.[/QUOTE]
This happened to me installing Joli. Definitely something to be on the lookout.

[QUOTE=dcstar]Compared to many questions in these forums yours is certainly not "dumb"![/QUOTE]
Thanx! I referred to it as dumb regarding my knowledge itself, not the questions, but considering the topic evolving much more i even expected, i'm gonna change the title from 'persistent usb dumb question?' to 'persistent usb and multi-boot questions'. I think, and hope the topic can help more people with same kind of doubts. [COLOR=Blue][edit] - Nevermind, title can't be edited..[/COLOR]

I can't express enough gratitude how much your answers have been complete, and helpful to me.

Cheers!

---

### Post by KBD47 on 2011-09-29
I've used Joli as a full install on a couple of computers, not really meant for usb, definitely would not be fast. For fast you can't beat Puppy, latest is 5.2.8 and if you want access to the Ubuntu repository Lubuntu would be a good choice. If you want something pretty but needs attention I'd say Bodhi Linux. Speed=Puppy and Lubuntu IMO.
KBD47

---

### Post by WasMeHere on 2011-09-29
Have you read about [_GeeXboX_]("http://www.geexbox.org")? It is a live mediaplayer using xbmc with USB persistent user data storage.

And have you heard about [_Multisystem_]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")? It is software that you can use to create a multiboot disk or flash drive.

I think you have many tips to sort out now. Good luck and let us know when you are satisfied with your multiboot disk and how you made it!
Olle

---

### Post by oldfred on 2011-09-29
If interested in Puppy.

Boot puppy ISO from hard drive:
[http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy&page=2](http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy&page=2)
[http://art.ubuntuforums.org/showthread.php?t=1600093](http://art.ubuntuforums.org/showthread.php?t=1600093)

---


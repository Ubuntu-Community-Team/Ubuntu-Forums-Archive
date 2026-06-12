---
title: "Friend is having problems, I'm stumped"
date: 2009-11-08
forum: General Help
---

### Post by DracoJesi on 2009-11-08
[IMG]http://img526.imageshack.us/img526/3991/screenshot1ht.png[/IMG]

I doubt this is a package problem, I guessing hardware, it happened a soon as he upgraded to 9.10....

I asked him to posts here and he said only aim.com and facebook are loading, that's just weird.... if something happend to the hosts files... why would they work?

he used this:

```
sudo apt-get update && sudo apt-get upgrade
```

and got this 

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:/home/linux# ^C
root@ubuntu:/home/linux#
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.

```

he thinks it's the kernel, he backported and restarted and the green bars went away but not h says it's the screen is flashy....

when he restarted, the text and graphics were broken

I'm trying have him take a screenie of -lspci now

---

### Post by DracoJesi on 2009-11-08
```
linux@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
```

---

### Post by coolclassic on 2009-11-08
sudo dpkg --configure -a

Will fix problem

then update upgrade

---

### Post by DracoJesi on 2009-11-08
sound not working either

```
linux@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

it's like he didn't get all the packages but updating them doesn't work

---

### Post by DracoJesi on 2009-11-08
> **coolclassic said:**
> sudo dpkg --configure -a

Will fix problem

then update upgrade

he doesn't think anything happned and is now telling me he is on 

2.x.16?.xx generic o.0

> nothing else changed, Except the reboot..

It was a black page this time.

And it said "auto refresh in progress"

and that was it.

Froze after that.
2:07pmJesi

is it still frozen?
2:07pmJustin

no.. I had to hold down my power button
2:07pmJesi

are you sure it wasn't just taking forever?
2:07pmJustin

pretty sure.. see whenever something happens in the background or other wise.. i hear crap in my speakers

no interference happened, i think it froze

---

### Post by coolclassic on 2009-11-08
I should have said that this should be done in in text mode only by selecting console login then do sudo dpkg --configure -a

---

### Post by justinnn on 2009-11-08
I tried that, oh, it's me Btw.

I tried doing that.. the GUI is incredibly hard to use being all super flashy.

---

### Post by justinnn on 2009-11-08
Just finished.. The image cannot be configured using sudo dpkg --configure -a

There are dependency errors that stop it, I think

---

### Post by DracoJesi on 2009-11-08
> **coolclassic said:**
> I should have said that this should be done in in text mode only by selecting console login then do sudo dpkg --configure -a

ah, ok, thanks :)

did you get that Justin?

---

### Post by justinnn on 2009-11-08
Yes, that's how i ran it.. i think.. During boot, recovery console?

---

### Post by justinnn on 2009-11-08
tried running under xterm

Same output..

---

### Post by DracoJesi on 2009-11-08
try doing the same but doing sudo apt-get update afterwards....before restarting , that looks promising before it froze before when the GUI was up

---

### Post by justinnn on 2009-11-08
E: linux-image-2.6.31-14-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured


Update manager told Me I had a broken package, and tried to fix it, this is the error I get

---

### Post by justinnn on 2009-11-08
wow.. SO I set my update manager to.. Well.. some other setting.. 97 updates.. check back later..

---

### Post by Dark9204 on 2009-11-08
>>wow.. SO I set my update manager to.. Well.. some other setting.. 97 updates.. check back later..

Yes, i was thinking about that. Make sure that you have the new sources and that you accept all packages(mark reccomended, security and so on...)

---

### Post by justinnn on 2009-11-08
After installing my updates, same problem.

I think I am missing alot of libraries and dependencies..

IS there anyway I can force my pc to re-install the upgrade 9.10?


[edit]

Turns out installing anything returns this:

E: linux-image-2.6.31-14-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

---

### Post by justinnn on 2009-11-09
After doing many many many things and reading many many many many things, I have seemed to fix my pc. I still have alot of broken images, and the same errors occur, but now i have sound, opengl.

So far....so good.

---

### Post by Dark9204 on 2009-11-09
I would save myself the trubble and reinstall.
The system just seems too broken.

---

### Post by JoelOl75 on 2009-11-10
I would try sudo apt-get dist-upgrade

This should resolve any held back/dependancy probs

---

### Post by renkinjutsu on 2009-11-10
synaptic does a pretty good job in these situations

just open up synaptic, and on the bottom left, click "custom filters" then in the list on the left, click "broken"

then, just remove all the broken packages

---

### Post by justinnn on 2009-11-11
"Broken" Is empty.

Everythings pretty much working fine. I wish I coud reinstall.

---

### Post by justinnn on 2009-11-18
Everytime I install something I get this;

E: linux-image-2.6.31-14-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-2.6.31-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: hlbr: subprocess installed post-installation script returned error exit status 1

---

### Post by kaspien on 2009-12-02
[]("http://www.uluga.ubuntuforums.org/member.php?u=950443")Any luck getting the issue resolved? I'm in the same boat ([http://ubuntuforums.org/showthread.php?p=8427988](http://ubuntuforums.org/showthread.php?p=8427988))

---


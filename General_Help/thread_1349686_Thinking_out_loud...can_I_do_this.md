---
title: "Thinking out loud...can I do this?"
date: 2009-12-08
forum: General Help
---

### Post by zadadka on 2009-12-08
Hello All,
 
Although I've had a decade as a (current, serving) Windows NT sysop, I'm thinking of doing the below, and wondered if it was simple and acheivable for an Ubuntu Noob.
 
I've Googled muchly, and it *appears* I can, but if there's a helpful soul here that can warn of any caveats, or even direct me to useful guides for just this (these) situation(s), I will be pleased to bestow gratuitous amounts of smileys upon them...
...and, gladly, a beer or several if they transpire to be in my locality.
 
I'd like to rebuild my Foxconn Intel Quad Core * and install the Koala as my Host OS, which logs in automatically at boot.
Considered from a Windows context, I suppose this autologin would probably be best as a non-Administrative User?
* My tin already runs a VMWkstn 5.x with an XP-VM on Vista/Win7, so I know the BIOS supports it.
 
I'd then like to install VMWare Workstation 7 (from a Windows EXE...how?...is "Wine" native to Koala for me to achieve this?).
 
Afterwards, VMWkstn7 would autolaunch at Ubuntu autologin, and again ideally, would then run up (startup) a Windows 7 VM ... I don't object to manually launching, but I've three young 'uns (5, 12 & 14) who would just want to login to their usual Windows environment and get on with "killing bad guys" etc in their favourite games, without yelling "DAD !! wtf? !?!" . ;)
 
Two serious questions here...
I run an Active Directory home network... does Ubuntu recognise/allow/support Kerberos credentials...?...
...and...
Will they see any lag issues whilst gaming (BF2, CoD-WaW etc) over and above current experience from the hardware in a native Windows environment?
 
My thoughts (if not already obvious) are to maximise available resources to the Guest OS' by using Ubuntu as Host.
 
One other thing that I have not been able to determine is whether I would need manufacurers' Ubuntu drivers for (eg) Graphics cards, or whether the (P2V'd or clean build) Guest OS would handle it by themselves? 
 
That's it....thanks just for viewing.
Abundant thanks for any useful contribution will be acknowledged in this thread.
The aforementioned beers will be by arrangement :D
 
Zad

---

### Post by Vaphell on 2009-12-08
installation of VM certainly requires linux binaries

i wouldn't count on marriage of virtualization and gaming (i tried to do that once but failed), wine is better but problematic nonetheless - check [http://appdb.winehq.org/](http://appdb.winehq.org/)
my guess is that you need actual host OS drivers for your gfx hardware, after all VM communicates with hardware via host OS (my virtualboxed XP uses some fake sun drivers)

Active Directory - no idea

---

### Post by argosreality on 2009-12-08
Your children are not going to be happy gaming under a virtual machine. While VMware, Parallels and Virtualbox support 3D acceleration to a certain extent its buggy as hell and SLOW. The only true way to game is either natively under ubuntu (through wine) or under Windows. Forget trying to VM it unless its a very old game

---

### Post by zadadka on 2009-12-08
Many thanks to Vaphell & argosreality, both for their responses and for being so prompt in providing them...
 
...clearly, I'll have to re-think this.  *sigh* ;)

---


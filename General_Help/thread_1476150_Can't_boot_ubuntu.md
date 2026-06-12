---
title: "Can't boot ubuntu"
date: 2010-05-07
forum: General Help
---

### Post by mclexer12 on 2010-05-07
Hi,
I have pc with NVIDIA GeForce 6600 GT graphic card, AMD processor i686, and 1G of RAM.  Well the pc is quite old and it has win xp istalled on it. 
Now I want to install the latest version of ubuntu and have doual boot (Ubuntu and win). But there is a problem. I did put ubuntu on a CD, but It won't boot when I start my pc, It just goes directly to windows. So thats my problema and yes I have check that the version of Ubuntu I have is for i686 microarchitecture. But I have find only one Ubuntu version for i686, if there are any more versions for i686 please post them bellow. 
And another thing. When I first downloaded Ubuntu I got Ubuntu 9.4 for x86 because I didn't know I need a spesific version of Ubuntu for my  microarchitecture. And I did boot and It showed me the menu, but when I tried to install It it said that I need x86, but I have i686.
 So that's my story and I find It very weird that it boots the 9.4 version for x86 but not the 10.4 for i686. 

So please help me forum, what should I do? and where is the fault me, cd, pc ? 

And sory for the long text.

Cheers

---

### Post by efflandt on 2010-05-07
You need to get into CMOS setup to change your boot order to boot from CD before hard drive.  That is from the initial splash screen from your BIOS before anything else comes up for any OS.  Typically F1 or F2 would get you into CMOS setup, but it might be some other F# key.  Or that screen may have a button to press to select boot device (sometimes Esc or F12).

If you have a monitor that has to wake up when you boot (especially a CRT), you may want to wake that up just before you boot so you can see the BIOS splash screen.  Otherwise that can sometimes be fast and gone before you see it.

One other note is that you may need to either insert the CD before you shut down. and then boot.  Or if you can open the drive with a paper clip in a small hole, insert the CD before you boot.

---


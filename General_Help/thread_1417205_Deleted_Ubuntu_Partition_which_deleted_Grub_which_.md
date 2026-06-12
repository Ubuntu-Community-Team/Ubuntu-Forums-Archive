---
title: "Deleted Ubuntu Partition which deleted Grub which means I'm Screwed"
date: 2010-02-27
forum: General Help
---

### Post by mmmg on 2010-02-27
Installed Ubuntu next to Windows 7, graphics card wasn't working or something, so I couldn't login. Like an Idiot, I decided to delete Ubuntu and try again. Made a live usb, deleted Ubuntu partition(terrible idea). When I booted up, I got some error in grub about it not being there and "grub-rescue>" I have no idea what to do. I booted into my usb and that all works. Then I tried to completely get rid of the Ubuntu partition and that worked, then I tried to resize my windows portion and I got an error. Now that drive is unaccessible. I tried installing Ubuntu again and it didnt work because the drive is messed up. So basically I know I'm screwed. I don't have a Windows 7 Recovery Disk because it came with windows 7 so I cant boot into windows if its even still there. I did however make a system image when I first got the laptop so I could always do that and go back to the beginning...I really don't know what to do. Any help would be greatly appreciated. Any info I left out I'll be happy to provide, just ask.

---

### Post by wilee-nilee on 2010-02-27
Your computer probably has a recovery partition that can be prompted to reinstall W7, not knowing exactly what has happened that may be worth looking into.

If you get W7 back only re-partition W7 with its disk manager. 

You may find the key prompt on startup for your computer to rewrite the W7 partition if this works, you will be lucky if anything is saved. 

As it is you can probably pull out anything in the W7 OS with a live Ubuntu Cd and a usb plugin to save with.

There are recovery discs that can be downloaded.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I haven't used this so hopefully more help will arrive.

---

### Post by mmmg on 2010-02-27
Yeah thanks, I found those after I posted this and its almost done burning. Hope I can recover some stuff...I don't know though, in the live usb of Ubuntu, it wasn't saying the drives name, and only knew the size of it. Which to me, doesn't seem good.

---

### Post by mmmg on 2010-02-27
Just went into the Windows 7 recovery disc and ran this in command prompt: Bootrec.exe/FixMbr
Everything works now

---

### Post by j03l5k1 on 2010-04-01
> **mmmg said:**
> Just went into the Windows 7 recovery disc and ran this in command prompt: Bootrec.exe/FixMbr
Everything works now



OMG i have been searching ages for this thank you.

i am also selling my pc and need to get rid of linux. did the exact same way as you did by deleting partition.

so happy this was fixed so easily

---


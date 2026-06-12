---
title: "&quot;Minimal BASH-like line editing is supported.... GRUB 1.90 5ubuntu3"
date: 2011-03-02
forum: General Help
---

### Post by lukoil on 2011-03-02
Hi,

I have a problem with the GRUB menu. When i open my computer it gives me error message " Minimal BASH-like line editing is supported...."  I can't get passed that. So, it makes the computer unuseful. Windows 7 is not seen, neither Ubuntu. I am stuck at that screen. 

Before i was running dual-boot Windows 7 32-bit and Ubuntu 10.10.
The GRUB version is GNU GRUB version 1.98+20100804-5ubuntu3

I looked everywhere to get this fixed but i just cant seem to fix it! I would really appreciate it if someone could help me out. 

Thanks

---

### Post by Diametric on 2011-03-02
Did this "just all of the sudden" begin happening, or was there anything that led up to this?  More info would help us out in offering advice.

Cheers.

---

### Post by lukoil on 2011-03-02
Well , it all started when i say in GRUB Windows Vista. I had no Windows Vista installed installed, only Windows 7 so i wanted to see what that Windows Vista thing is. It booted the recovery partition but, i didnt do anything to it. Just opened in the main menu and thats it. I closed it after. I also re-booted and i saw a dash at top left flashing with nothing popping up. I got the USB and yeah from there i tried a bunch of stuff and didnt do any good. Any suggestions?

---

### Post by Alex090391 on 2011-04-13
I am having the same problem right now. I restarted my laptop and then this came up and I have no clue on how to fix this.

---

### Post by hwangche on 2011-04-23
I have the same problem too. I saw the post "unusual grub minimal bash-like line editing is supported, anyone can assist?" and I followed the solution there(quote below). Although when I ran the second line, it said it could not read the file, but my problem was solved by just running the first line and reboot. I hope it'll solve yours too.

> **bcbc said:**
> This is a very common problem with 10.04 as shown by the popularity of the wubi megathread. It also mentions a tool that you can use to access the virtual partition used by Wubi (this is why you can't find it because it's not a real partition). It's a file C:\ubuntu\disks\root.disk (change C: depending on the drive you installed on but it seems like C: from the ls output). 

And PS that should probably be (hd0,msdos1)

So you can just enter:
```
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```
And that should boot it. Then you can apply the Permanent Fix shown in the thread.

---


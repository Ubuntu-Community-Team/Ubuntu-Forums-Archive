---
title: "Unable to start up ubuntu"
date: 2011-03-28
forum: General Help
---

### Post by aleifr on 2011-03-28
When I boot up, right before the login screen appears, everything freezes, and I have no choice but to turn the computer off manually.

The first time it happened, I had just downloaded a HUGE update (hadn't been online with ubuntu in a long time), and the computer was probably installing the updates when it crashed, and then, the problem I described above.

I tried to boot up in recovery mode, but at some point the computer couldn't come further. I don't think it crashed, I think it was working, but nothing happened. At the time it got stuck the last command line read:
[ 7.451509] udev[514]: starting version 163

In addition to ubuntu, I also run windows 7 on the computer.

Anyone know how I can fix this?

---

### Post by aleifr on 2011-03-29
When I try to boot up in ubuntu, I see my windows 7 desktop for a few seconds, which leads me to believe there is some sort of clash between ubuntu and windows.

When I turn my computer on, before I choose a system to boot up, I can go into emacs or bash in gnu grub (I don't know what all that means, I don't know much about all this). I don't know, maybe I can do something from there?

I don't know, if nothing works, I'm considering deleting the ubuntu partition and re-installing it...or just overwriting it, but I don't think that's possible.

---

### Post by kiyop on 2011-03-29
How about pressing ESC key some times?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

How about pressing r,s,e,i,u,b successively while pressing ALT+SysRq?

---

### Post by aleifr on 2011-03-29
> **kiyop said:**
> How about pressing ESC key some times?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

How about pressing r,s,e,i,u,b successively while pressing ALT+SysRq?

Thanks, for the reply. Esc did nothing. r,s,e,i,u,b + ALT+SysRq only restarted the computer, and when I booted up in ubuntu after that, I had the same problem.

---

### Post by Rubi1200 on 2011-03-29
Hi and welcome to the forums :-)

1. please post the specifications for the computer, especially RAM and graphics card

2. please run the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


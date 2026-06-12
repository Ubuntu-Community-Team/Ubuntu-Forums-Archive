---
title: "How to get boot text back"
date: 2011-09-20
forum: General Help
---

### Post by doctordruidphd on 2011-09-20
What I would like is to get the bootup messages and text that used to display when the splash option was removed.

Since maverick, I have not been able to get that, even after disabling plymouth. All I get is a black screen, until after the fsck stuff runs, then I get brief text before the greeter screen. I can't really remove plymouth itself -- it threatens to remove most of the OS along with it. But I have disabled it with sysv-rc-conf, removed its hooks in /usr/share/initramfs-tools/hooks and done an update-initramfs -u, and removed the "splash" option in /etc/default/grub. No luck, I still get a black screen most of the time.

OK so it's not pretty, but I want to see that stuff. Anyone got it working?  Thanks.

---

### Post by ddr3XD on 2011-09-20
This guide helped me fixed this in Lucid, not sure if it will work with Natty.

[COLOR=DeepSkyBlue][High resolution Plymouth & Virtual Terminal for ATI/NVIDIA cards with proprietary/restricted driver]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")[/COLOR]

Use this guide with caution if you must give it a try. Make sure to backup all files that the guide insists on changing.

Edit: My bad, i just realized your asking for the opposite of what the guide i posted is telling you to do. srry about that.

---

### Post by doctordruidphd on 2011-09-21
Right, I want to get rid of the graphics until the greeter screen. Still works in debian, not sure what ubuntu has done to break it.

---


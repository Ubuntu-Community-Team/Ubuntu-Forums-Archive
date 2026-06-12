---
title: "Clear Swap Partition?"
date: 2006-02-12
forum: General Help
---

### Post by Autolycus on 2006-02-12
Howdy...

I setup Ubuntu with 3 partitions....1 boot; 1 main; and 1 swap partition...
I was investigatibg the various menu items and found one that displyed the hard drive partitiond....
I noticed that the swap partition seemed full....is there a way to clear out this partition or is it done automatically....
My computer seems to run slow....I use it only for downloading torrents from the internet...

TIA,

Ken

---

### Post by atoponce on 2006-02-12
[quote=Autolycus]Howdy...

I setup Ubuntu with 3 partitions....1 boot; 1 main; and 1 swap partition...
I was investigatibg the various menu items and found one that displyed the hard drive partitiond....
I noticed that the swap partition seemed full....is there a way to clear out this partition or is it done automatically....
My computer seems to run slow....I use it only for downloading torrents from the internet...

TIA,

Ken[/quote] My swap partition is also full.  Interesting.  I have never thought if it before.  However, my computer runs quite snappy.  What is your current setup?

---

### Post by taurus on 2006-02-12
When you reboot, your swap will be empty!  How much RAM do you have in your machine and what size is your swap partition anyway?

---

### Post by Autolycus on 2006-02-12
I am aware that by rebooting the swap partition will be cleared...is there a way to do it without rebooting?

Current setup..

Acer Celeron 466 mHz, 192 mb ram, 17.94 gb hard drive [boot (hda1) 188 mb, main (hda3) 17.47 gb), swap (hda2) 283 mb].

I realize this computer is not the best and I do not want to invest in upgrading it....I will probably purchase a new computer later this year...

TIA,

Ken

---

### Post by pt78 on 2006-02-12
[QUOTE=Autolycus]
Acer Celeron 466 mHz, 192 mb ram, 17.94 gb hard drive [boot (hda1) 188 mb, main (hda3) 17.47 gb), swap (hda2) 283 mb].
I realize this computer is not the best ...
[/QUOTE]

Well, I'm running my Red Hat 7.2 on 486 laptop with 12 megs of RAM and 10GB drive. No X and multimedia, but samba runs just fine. :cool:

---

### Post by taurus on 2006-02-12
[QUOTE=Autolycus]I am aware that by rebooting the swap partition will be cleared...is there a way to do it without rebooting?

Current setup..

Acer Celeron 466 mHz, 192 mb ram, 17.94 gb hard drive [boot (hda1) 188 mb, main (hda3) 17.47 gb), swap (hda2) 283 mb].

I realize this computer is not the best and I do not want to invest in upgrading it....I will probably purchase a new computer later this year...

TIA,

Ken[/QUOTE]
If you have Gnome as your window manager with firefox and some other apps open, expect your RAM to be 100% and most of your swap as well...  Therefore, try something a little lighter like Xfce4, IceWM, or even fluxbox!!!

---

### Post by GTvulse on 2006-02-12
[QUOTE=Autolycus]

[snip]
I noticed that the swap partition seemed full....is there a way to clear out this partition or is it done automatically....
[/quote]

Err no. The name itself implies it, a swap space is a place to dump unused pages of memory to disk while they are needed again. It is transient space and its written to and erased *constantly*. Of course, the last contents of RAM will be there to be read by anyone with the knowledge, determination and tools. If you feel that it is a risk to leave there traces of your comunications with the Illuminati, you can [encrypt]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=encrypt+swap&fullsearch=Text") it.

> 
My computer seems to run slow....I use it only for downloading torrents from the internet...
Ken

That means that you are short of memory, physlcal RAM and swappiing space. If you type "free" at a terminal, you'll get a better idea of your present situation.

---

### Post by newuser111 on 2006-02-12
there are instructions for wiping a linux swap on this [http://www.iusmentis.com/security/filewiping/wipeswap/](http://www.iusmentis.com/security/filewiping/wipeswap/)

I doubt it will improve your performance, swap is far slower than ram, buy more ram if you want linux to use less swap

---


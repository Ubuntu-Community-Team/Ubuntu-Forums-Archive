---
title: "First time with Linux."
date: 2010-04-20
forum: General Help
---

### Post by Dray67 on 2010-04-20
Like the title says I'm taking the plunge after years of Windows use, I'm wondering whether to try a Wubi install first or just going dual boot, my system has a Intel 160gb SSD with win 7 pro installed on it and a 500gb sata, I've installed a few programs on the SSD with the rest on the 500gb, if dual boot is the way to go I was going to split the SSD and give Win and Ubuntu 80gb each and take it from there if advice tells me that is the way go.

In addition to the HDDs I have an I7 Intel cpu, 6gb ram and a couple of geforce 275 in sli config.

Any tips and info would be appreciated until I get my head round Ubuntu.

---

### Post by nothingspecial on 2010-04-20
Hi

First I would recommend a dual boot, if only for the fact that most people here don`t use wubi and you will get better help. 

Also, you only need about 5 gigs for Ubuntu, I usually use 7-8 to be safe. The point is, if you give 80 gigs to ubuntu that`s 80 gigs windows is going to struggle to use (I think it`s possible). Ubuntu will be able to read your files from windows no problem.     
If you see what I mean.....

Opinions only, I don`t dual boot with windows.

---

### Post by prodigy_ on 2010-04-20
Wubi isn't intended for permanent installations and also it often causes troubles for Grub (Linux bootloader). I'd suggest to skip Wubi completely and try regular dual-boot instead.

---

### Post by Alaxandar on 2010-04-20
Hey I am glad to see your ready to make the switch! First off let me tell you my experiences with starting linux. I had vista and I was up all night woking on some big project, and word forze, which happens so I went to alt control delete it and the black screen came up. I finaly was so fed up with windows I just wiped my system. And I am glad I did, althought I missed photoshop for a bit, and just a couple programs you can only get on windows it force me to learn linux, which in turn has been the best thing in the world for. You have a good enough computer to dual boot. Its all  your preferance, my advise is to just go for it all out. 
MY tips are: try both KDE and GNOME, they are both great and it makes it that much better if you know your options. If you have any queston no matter how small try and find the answer the more you research and know about linux the more you enhoy it.

Good luck man!

---

### Post by P4man on 2010-04-20
As you may or may not know, before installing you can just boot from the cd or usb stick and try ubuntu that way, although with some limitations (no proprietary videodrivers, slow boot etc). 

If you want to give it a real try, I second everyone else: make a dual boot. Its not difficult and will save you headaches in the long run. 

You can install Ubuntu  on the SSD and have the installer divide the space as you want (id recommend 10gb at least for ubuntu. it installs and runs fine with less, but some headroom never hurts).

I would also suggest you manually partitiom your drive (during the install) and create a separate partition on your 500GB drive for your /home and put ubuntu root partition  ("/") on the SSD. Separating your home from the rest will make life a lot easier if you want to reinstall or experiment with other releases.

---

### Post by Dray67 on 2010-04-20
Dual boot it is, I do play a few games so I need windows for the time being, that and the fact I'm coming into Linux with very little knowledge so the learning curve will be steep initially.

Thanks for the replies.

---

### Post by Dray67 on 2010-04-20
In Ubuntu atm updating, Win 7 crashes when I try to boot from grub but I'm not panicking yet, I'll see how it goes before I run for the hills.

---

### Post by P4man on 2010-04-20
eck. not a good start. Did you by any chance hibernate windows before installing ubuntu? updating ubuntu is not likely to cure your windows woes..

---

### Post by Dray67 on 2010-04-20
Last thing I did in windows was shrink the SSD and sata hdd volumes, 45gb and 100gb respectively for the Ubuntu install.

The install is ok so far, wondering what format to use for the 100gb partition, ext2,3 etc?

Any ideas as to why Win 7 wont boot?

---

### Post by P4man on 2010-04-20
> **Dray67 said:**
> Last thing I did in windows was shrink the SSD and sata hdd volumes, 45gb and 100gb respectively for the Ubuntu install.

The install is ok so far, wondering what format to use for the 100gb partition, ext2,3 etc?

Ext4 for best performance. Some people recommend Ext3 because Ext4 is rather new and there are some rumours of bugs in it, but I have yet to see any hard evidence. Ext4 is great afaik.

But ahm.. you already installed it? Then its a bit trickier to create a /home partition for you data and settings, the best way to do that is during the install. Now your /home sits on the same partition as your ubuntu, and separating them is possible but a bit of work (google on it)

> Any ideas as to why Win 7 wont boot?

Id guess something with grub. What happens when you try booting it?

---

### Post by Dray67 on 2010-04-20
It gets to the loading screen where you get the animation for the logo and as the colours circle around it crashes just as they merge.

---

### Post by P4man on 2010-04-20
then its not grub, as its long passed grub. Did you reboot after resizing the partitions (probably not)? Maybe something went wrong there? Doesnt sound like ubuntu is to blame though. Perhaps try safe mode in windows and see what you get.

Be adviced if you will try fixing windows from the windows cd (recovery stuff) it will wipe grub bootloader, and you wont be able to boot ubuntu, but its rather straightforward to reinstall grub from the ubuntu cd to give you dualboot again.

---

### Post by Dray67 on 2010-04-20
I'll give that a go, thanks for the help.

---

### Post by P4man on 2010-04-20
other thought: when you resized the windows partition, did you make room left or right of the partition? I dont know about 7, but previous windows insisted on being on the first partition, so if you made room on the left side, it wouldnt boot. If in doubt, in ubuntu run gparted (might need to install that from software center, long name is gnome partition editor).

---

### Post by Penguin Guy on 2010-04-20
> **Dray67 said:**
> Like the title says I'm taking the plunge after years of Windows use, I'm wondering whether to try a Wubi install first or just going dual boot, my system has a Intel 160gb SSD with win 7 pro installed on it and a 500gb sata, I've installed a few programs on the SSD with the rest on the 500gb, if dual boot is the way to go I was going to split the SSD and give Win and Ubuntu 80gb each and take it from there if advice tells me that is the way go.

In addition to the HDDs I have an I7 Intel cpu, 6gb ram and a couple of geforce 275 in sli config.

Any tips and info would be appreciated until I get my head round Ubuntu.
You've got lots of memory and your processor supports x86_64, so you should get the x86_64 version (otherwise you'll only be able to use 3.2GBs of your memory). Good luck.

---

### Post by Dray67 on 2010-04-20
Installed gparted and it shows the win partition on the left but right at the front there is a 1MiB partition unallocated?

Edit.
@ P4man - Win 7 is loading ok now, nothing I did so I guess I lucked out.

@ Penguin Guy - I looked for a 64bit ver but the only ones I could find were for AMD processors, or have I missed something obvious?

Edit.
@Penguin Guy - Found it, I did miss something obvious, this is what happens when your capable of losing a game of charades to Stevie Wonder. :P

---

### Post by P4man on 2010-04-20
> **Dray67 said:**
> Installed gparted and it shows the win partition on the left but right at the front there is a 1MiB partition unallocated?

Thats okay.
> 
@ Penguin Guy - I looked for a 64bit ver but the only ones I could find were for AMD processors, or have I missed something obvious?



AMD64 is the name of the architecture, as AMD made it. Intel adopted it later, andnow all modern amd and intel cpu's (except some atoms) support AMD64. there is no such thing as intel64, they are compatible. 64 bit windows is also "amd64". 

Anyway, the 32 bit version will probably suit you well enough. Its rare I use more than 1GB ram on ubuntu, much less anywhere near 4GB.

---

### Post by Dray67 on 2010-04-20
> **P4man said:**
> Anyway, the 32 bit version will probably suit you well enough. Its rare I use more than 1GB ram on ubuntu, much less anywhere near 4GB.

If the memory use isn't an issue what benefit if any would I get from the 64bit version?

---

### Post by Mike54 on 2010-04-20
Because one of these days, you'll give up Windows.  And then you'll be able to take advantage of all the memory.  ;-)

---

### Post by P4man on 2010-04-20
> **Dray67 said:**
> If the memory use isn't an issue what benefit if any would I get from the 64bit version?

Better performance. Compared to x86 (or i686 if you like) AMD64 not only increases the memory addressing to 64 bit, but it also includes some other improvements (in tech talk, more CPU registers). 64 bit code on linux is usually a few percent faster. For certain things like media encoding or file compression the difference can be more substantial, in extreme cases almost twofold, but generally its not really noticable. 

On the downside, you might face some minor issues with flash plugin and compatibility problems with the odd (old) 32 bit only app.

Either way, if this is your first exposure to linux, its nothing to worry about, unless you intend to run multiple virtual machines simultaneously (and could use all your ram) or run some code that really benefits from 64 bit addressing. 

If/when you decide to upgrade or do a reinstall for whatever reason (like messing up your current install), then you might as well go for 64 bit. I doubt you'll notice either way though.

---


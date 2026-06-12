---
title: "GNU GRUB EDIT...Wait, what?"
date: 2010-03-22
forum: General Help
---

### Post by cybernetic toaster pastry on 2010-03-22
I'm still learning a bit about how Linux operates so I'm at a loss on this. Sometimes when I do updates and restart the computer I get a dos type screen that says GNU GRUB editor 1.6 beta ( I think, I cant remember it now) And it tells me I can push TAB for a list of commands. Since I have no idea what is going on during this or why it happens the only command I can use is exit which takes me back to the dual boot screen. I really don't want to reinstall everything all over again. It takes six hours to install Ubuntu and all the updates plus all the packages I need for somethings to work, so any help is very appreciated.

---

### Post by Dantevus on 2010-03-22
Is Ubuntu installed on it's own partition? And is it the only OS you have currently installed?

---

### Post by cybernetic toaster pastry on 2010-03-22
No, I also have Vista (Don't judge me)

---

### Post by Dantevus on 2010-03-22
Lol no judgement here. I had vista before I switched to Linux again and it's really not as bad of an OS as people have said.

I'm thinking there might have been a problem when you installed Ubuntu. I was doing some searching on google for your problem but couldn't find too much information about it. Are you able to get into Ubuntu at all or does it never get past the editor?

---

### Post by coffeecat on 2010-03-22
> **cybernetic toaster pastry said:**
> I'm still learning a bit about how Linux operates so I'm at a loss on this. Sometimes when I do updates and restart the computer I get a dos type screen that says GNU GRUB editor 1.6 beta ( I think, I cant remember it now) And it tells me I can push TAB for a list of commands.

And you get a prompt that says "sh:grub>". Nothing's wrong. You must have had your finger resting on the 'c' key. :wink: If you look at the bottom of the grub menu screen, you'll see a number of options including 'c' for command line and 'e' for edit currently highlighted entry. It's useful for those few occasions when you need to invoke various grub commands. Just ignore them if you don't need them.

And keep your hands off the keyboard until you need to press the enter key! :p

---

### Post by cybernetic toaster pastry on 2010-03-22
Well, you know the screen I'm referring to and I got my hopes up so I rebooted. When the dual boot screen came up I highlighted Ubuntu, made absolutely sure I hit no other buttons when I hit enter and the it took me to the same "edit" screen. I now understand what this screen is but it appears no matter what when I select Ubuntu. I feel as though this is something really stupid I'm just not noticing.

---

### Post by coffeecat on 2010-03-22
> **cybernetic toaster pastry said:**
> Well, you know the screen I'm referring to and I got my hopes up so I rebooted. When the dual boot screen came up I highlighted Ubuntu, made absolutely sure I hit no other buttons when I hit enter and the it took me to the same "edit" screen. I now understand what this screen is but it appears no matter what when I select Ubuntu. I feel as though this is something really stupid I'm just not noticing.

That's very curious. You *should* have to press the 'e' key to edit the entry or 'c' to get a command line, and no other keys should be able to invoke edit or command line. The enter key should simply invoke the grub commands that are in the choice you've highlighted so that you boot up. Which makes me wonder if there is some issue between your keyboard and the BIOS which means that the wrong key codes are being passed to grub by the BIOS. At the moment I don't have anything more sensible to suggest. I've never seen the behaviour you describe.

---

### Post by cybernetic toaster pastry on 2010-03-22
> **coffeecat said:**
> That's very curious. You *should* have to press the 'e' key to edit the entry or 'c' to get a command line, and no other keys should be able to invoke edit or command line. The enter key should simply invoke the grub commands that are in the choice you've highlighted so that you boot up. Which makes me wonder if there is some issue between your keyboard and the BIOS which means that the wrong key codes are being passed to grub by the BIOS. At the moment I don't have anything more sensible to suggest. I've never seen the behaviour you describe.


Trust me it's throwing me through a loop. I understand completely what your saying about the commands and your right it doesn't make sense. The really sad part is that this is the second time it has happend to me. The last I just reinstalled. I've tried a few commands on the "edit" screen and the only two I can get to do anything are "exit" and "reboot" if I try "boot" it says 'no kernel loaded'.  If I have to reinstall once more I might just decide it's not worth it because I never know when I'll try to boot Ubuntu and get this all over again. And I really loved this OS.

Thank you for the help.

---

### Post by coffeecat on 2010-03-23
If you get the 'edit' choice, **not** the command prompt choice, you  are prompted with all the grub code that is responsible for booting the  selected kernel. That gives you the opportunity to edit it for  troubleshooting purposes. To boot from the edited stanza, you press  ctrl-X (if I remember correctly( - you are prompted for the key  combination). You could try pressing ctrl-X (or whatever it is) without  editing. It should just boot.

I would hate to see someone frightened off Ubuntu for what looks to me  like a hardware issue - nothing to do with either Ubuntu or grub.

**Edit:** clarification. Once you're fully booted into Ubuntu (or  Windows) the OS is using its own drivers to detect the output from the  keyboard, which may be why you don't get spurious keyboard effects in  the Ubuntu desktop. Grub (which is not actually part of Ubuntu per se -  it's an independent OS-agnostic bootloader) relies on the BIOS for  keyboard detection. Some BIOSs do strange things with keyboards. I've  come across fairly modern BIOSs which can't detect a USB keyboard unless  you enable 'legacy' USB support. Weird. Can you try booting up with a  PS2 keyboard - if you're using a USB one - to see if this makes any  difference? Because if this is a grub issue, it must be an obscure one. I  can't find anything similar in a Google search.

---

### Post by coffeecat on 2010-03-23
> **coffeecat said:**
> I  can't find anything similar in a Google search.

Well, yes I can. Here:

[https://bugs.launchpad.net/wubi/+bug/484799](https://bugs.launchpad.net/wubi/+bug/484799)

Are you running Wubi? You didn't say. Wubi is a horse of an entirely different colour.

There are a number of fixes and workarounds in that Launchpad thread, but my fix would be to consign Wubi to oblivion and do a "proper" dual-boot install with Ubuntu on its own dedicated partition.

---

### Post by cybernetic toaster pastry on 2010-03-23
I'm not entirely sure what you mean by Wubi. Is that the download on Ubuntu.com because I do have that. I also have the dual boot disk for Karmic Koala that came with a magazine I bought. I tried a while back to use them so I could use more of my hard drive for Ubuntu. I uninstalled Ubuntu with Revo uninstaller which is suppose to remove everything that has to do with the file, however, when I put the disk in and rebooted the only option I get is to completely erase windows and install Ubuntu, well I do get the option to manually partition it but I'm not that good. When I did my wife's computer it gave a 3rd option of a 50-50 partition. Could this be because there may still be remnants of Ubuntu/Wubi on the computer. I only want to keep Windows for a couple applications and this(trouble shooting), other wise I would go with straight Ubuntu.

UPDATE: I am currently on Ubuntu thanks to your link to that thread and especially post number 7 on there.  According to that post I will have to use those commands every time but I guess it's better than nothing. I did do the "sudo update-grub" but I haven't restarted to see what difference that makes.

Thank you for all your help.

---

### Post by coffeecat on 2010-03-24
Apologies for the delay in getting back. I'm glad to see that a post in that Launchpad thread is giving you a workaround. However, that sounds very tedious and simply gives you a way of booting into an old kernel. It seems that the -15 and -16 kernels are the problematic ones. Since then there have been -17, -19 and -20. (-18 must have escaped) kernels but I see no reference to them in the Launchpad thread.

While in Ubuntu, have a look in /boot where the kernel files are kept. Do you have files with 2.6.31-17 (and/or -19, and/or -20) in them? Were you getting this problem when you booted into the -17, -19 or -20 kernel? If you don't have those versions it might be worth updating to get the -20 kernel and then booting into that. Of course, if that causes the problem again you'll have to go through your fix to be able to use the -14 kernel.

Alternatively, post #33 is interesting. It links to:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

It sounds plausible and replacing wubildr might be the answer.

Last thought. Wubi is a good way of trying out Ubuntu, but has its limitations. And this bug is a near-showstopper, which is a great shame. I'm sure it must have put many people off Ubuntu. If you do think of installing Ubuntu on its own native partition side-by-side with Windows (where it will perform better), here's a useful guide:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Two warnings if you do:

This wasn't the case with XP, but sometimes Vista becomes unbootable if you resize its C:\ partition with the Ubuntu partitioner. This is repairable, but inconvenient. It's better to shrink the Vista partition with Vista's own utility first.

Installing a conventional dual-boot replaces the Windows MBR with grub stage 1 (this doesn't happen with Wubi). If you subsequently decide to abandon Ubuntu and delete the Ubuntu partition, you'll make Vista unbootable. Again, this is easily fixed, but something you should be aware of.

If you need any more information about either of these points, just post back.

And good luck!

---

### Post by cybernetic toaster pastry on 2010-03-24
Well, I do believe you have answered every question I had and then some. As to your question about the kernels, when I saw the first line >linux /boot/..ect. in that one post I noticed the -14-generic part of the line and wondered if I could possibly substitute it for another one like kernel 19. I should have used 20 but 19 popped in my head first so I tried it and, well, it worked.

I probaly will partition my hard drive eventually to 1. Get a better experience of Ubuntu. 2. Get more physical memory for Ubuntu. But this will only happen when I finally decide to make the effort to save everything on a thumb drive first.

Thanks again for the excellent help!

---


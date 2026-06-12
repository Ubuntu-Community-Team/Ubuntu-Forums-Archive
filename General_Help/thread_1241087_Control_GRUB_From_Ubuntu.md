---
title: "Control GRUB From Ubuntu"
date: 2009-08-15
forum: General Help
---

### Post by LASTGUY2GETPS2 on 2009-08-15
Okay. I don't know if this is possible but I'll give it a shot.

I have windows and ubuntu installed side by side with GRUB setting Ubuntu as the default boot partition. I have WOL setup on this particular computer. Sometimes when I remote desktop I need access to windows.

So my question is, how can I setup ubuntu to boot into windows on next restart from ubuntu? I guess I want the equivalent of "mac osx startup disk" on ubuntu

MODS if this is the wrong forum subsection please move

---

### Post by Herman on 2009-08-15
There are several different ways to get Windows to boot up by default from GRUB.

One way to do it would be to edit your /boot/grub/menu.lst file in Ubuntu by replacing the number 0 after the default command with the word 'saved', and then add the 'savedefault' command in your Windows boot stanza.

Another way would be to change the number 0 after the default command to the number which corresponds to the entry number fro your Windows operating system entry in your menu.lst file, counting from the top down starting counting from zero.

Yet another way would be to copy and paste your Windows boot entry to a location above the start of your Debain Automagic Kernels List in your menu.lst file.

---

### Post by LASTGUY2GETPS2 on 2009-08-15
Perhaps I was not as clear as I would have liked to been in my orignal post. If I'm not mistaken, I believe those methods would make Windows my default boot partition if no selection is made at the Grub screen. 

What I want to do is to:

1)WOL my computer 
2) Since I can't select Windows OS on grub remotely, load into ubuntu
3) reboot the computer so it opens windows xp for the next reboot only. Subsequent reboots will load ubuntu...

I occasionally will need to use XP but for the majority of times ubuntu will be fine...

---

### Post by Herman on 2009-08-16
Oh, sorry, yes they would would make Windows my default boot partition if no selection is made at the Grub screen. 
Okay. I would consider trying this then, edit your /boot/grub/menu.lst file in Ubuntu by replacing the number 0 after the default command with the word 'saved', and then add the 'savedefault' command in all of your menu.lst boot stanzas.

1)WOL your computer 
2) Since you can't select Windows OS on grub remotely, load into ubuntu
3) run the grub-set-default script, which will edit your /boot/grub/default file for you.
You should give it the number of your Windows boot entry to write there.
4) reboot the computer so it opens windows xp for the next reboot. Subsequent reboots will load whatever boot entry was selected last, so it will keep booting Windows, but as soon as you select Ubuntu then it will keep on booting Ubuntu again until told otherwise.
 
More information, [invoking grub-set-default]("http://www.gnu.org/software/grub/manual/html_node/Invoking-grub_002dset_002ddefault.html") - GNU GRUB (Legacy) Manual.

/usr/sbin/grub-set-default is a script and can be run from your terminal in Ubuntu or from another script set to run at boot-up or shutdown, or set to run a a certain time and/or date by another program.
Alarm clock is a useful program for running scripts or other programs and you can also use Evolution Calendar alarms too, both GUI, just in case you don't crontab.

---

### Post by LASTGUY2GETPS2 on 2009-08-16
Hmmm, that seems like it would work...

Is there anyway I could make a similar script within windows that would edit GRUB?

Thanks for your responses so far!

---

### Post by Herman on 2009-08-16
I haven't tried writing scripts in Windows. When I was a Windows user it didn't occur to me to try it. I'm not sure. I do know we can run dos commands from the command prompt. I haven't heard of Windows users writing and running their own scripts though. I have a book about programming that came with a CD which includes software for programming in Windows, if you buy the right software you can write your own programs for Windows. 

As for editing GRUB from Windows, I'm not sure how you'd do that without compromising your security in Ubuntu.
One idea that might be simpler than editing GRUB from Windows might be to edit the boot loader in Windows. 
You didn't say if you're using NTLDR or BCD. 

If you're using NTLDR then it shouldn't be too hard to edit boot.ini.
Back in the Ubuntu side of things, I'd install LiLo in Ubuntu and install it to Ubuntu's partition boot sector. Then I would use a dd command to take a copy of the Ubuntu (LiLo) boot sector and paste in into the root of the Windows C: drive. Then I would edit boot.ini to boot that boot sector which  will boot LiLo and LiLo will boot Ubuntu. That's one way you could possibly toggle booting Windows or Ubuntu at the Windows boot loader.
That's not the most reliable way to boot Ubuntu though, as it relies on a simple blocklist reference. But it should work well enough, especially if you only have one hard disk.
I can give more details on this procedure if requested.

If you're using BCD then you might find it easier to install EasyBCD and see if there's a way to use EasyBCD to edit BCD to boot Ubuntu. Possibly you can boot Ubuntu directly with Easy BCD but I'm not sure. You should ask the experts at [NeoSmart Technologies]("http://neosmart.net/dl.php?id=1") about that. They might be able to help you, they know far more about BCD than I do.

There's also Win GRUB, you could install WinGRUB in Windows, I have a page about that here, [WinGRUB Page]("http://members.iinet.net.au/%7Eherman546/p9.html").
WinGRUB should be able to be edited by a script or program within Windows, to toggle the boot between Windows or boot LiLo in Ubuntu's boot sector.
(You'll still have GRUB in MBR, but LiLo in the boot sector).

Once you have Ubuntu booted, it would then be relatively easy to run grub-set default again to set the boot back to Ubuntu.

---

### Post by LASTGUY2GETPS2 on 2009-08-16
Thanks! I'm going to look into that!

---

### Post by dbldown768 on 2009-11-13
I'm interested in this as well.  I was wondering if you found a working solution to this problem???

---

### Post by Herman on 2009-11-14
Would these links be at all interesting or useful to anyone? 

[NetworkBoot - *GRUB* Wiki]("http://grub.enbug.org/NetworkBoot")

 [*GRUB* PXE *network boot* - LinuxMCE wiki]("http://wiki.linuxmce.org/index.php/GRUB_PXE_network_boot")

[*PXEBOOT* - *GRUB* Wiki]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=2&ved=0CBAQFjAB&url=http%3A%2F%2Fgrub.enbug.org%2FPXEBOOT&rct=j&q=PXE+boot+%2BGRUB&ei=J2z-SrbOGc6QkQWz7oSADA&usg=AFQjCNFoFydVnO1eAEwEO6eZdgVB2d6JPQ")

---


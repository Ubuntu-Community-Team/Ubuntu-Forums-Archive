---
title: "Overwrite a dual-boot?"
date: 2010-12-07
forum: General Help
---

### Post by CommuneOfLoon on 2010-12-07
I have a computer with dual-boot, but I'd like to just move over to VirtualBox, and I was wondering if it was possible to reformat the XP partition with Ubuntu without reformatting the whole machine.

---

### Post by zvacet on 2010-12-07
If I understand you correctly you want to delete Xp partition.You can do that with Ubuntu live Cd or with [Gparted live CD.]("http://gparted.sourceforge.net/")

---

### Post by argedion on 2010-12-07
Using gparted should help do what you want however you should DO A BACKUP before taking on this task. Also note that you need to be careful not to destroy your boot sequence. Even though you are dual booting removing XP which is probably hda or something of the sort if you delete the partition and that is where grub is you could make your computer un bootable. This could be fixed with a live CD/USB and reistalling grub if you wipe it out.

---

### Post by iann128 on 2010-12-07
What if you have a duel boot with two drives. Windows is on the first drive, and I assume Grub is too. I want to pull the Windows drive out to put it in another computer, and keep the Ubuntu drive where it is. What command would I need to run from the Live CD to install Grub on the Ubuntu drive?

Thanks,
Ian

---

### Post by wilee-nilee on 2010-12-07
The missing information here is, [COLOR="Red"]wait for it now[/COLOR]....... **Is this a wubi install to begin with.**

Don't give solutions until some basic information is confirmed.

Thread starter do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

You can run this script from Ubuntu, but if it is Ubuntu installed inside of XP boot a live Ubuntu as described.

Wubi is called a dual boot on their own page don't assume that it isn't a wubi.

---

### Post by CommuneOfLoon on 2010-12-07
I'm sorry, I'm confused as to what I should be doing? I installed XP first as a 10gb partition, I then installed Ubuntu on the rest of my computer. How do I reinstall the grub? What is wubi? And what is the bootscript telling me? 

I will have to get the bootscript info tomorrow.

And though I'm confused, I appreciate your guys help thus far :)

---

### Post by wilee-nilee on 2010-12-07
> **CommuneOfLoon said:**
> I'm sorry, I'm confused as to what I should be doing? I installed XP first as a 10gb partition, I then installed Ubuntu on the rest of my computer. How do I reinstall the grub? What is wubi? And what is the bootscript telling me? 

I will have to get the bootscript info tomorrow.

And though I'm confused, I appreciate your guys help thus far :)

A wubi install is one done inside a live Windows environment. Many come on the forums not knowing they have one, and if the wrong information is given can create a damaged system. The term dual boot is used with the side by side and wubi, so a confirmation from you is needed so we don't mess you up .

This was just pointing out the missing information, don't worry about the bootscript.

> **CommuneOfLoon said:**
> I have a computer with dual-boot, but I'd like to just move over to VirtualBox, and I was wondering if it was possible to reformat the XP partition with Ubuntu without reformatting the whole machine.

At the least this is confusing what is it you want in a virtual Ubuntu, not a good choice as it really does not run that well in a Virtual, Linux mint 10 I just installed does though, and many other open source do. XP runs nice in a virtual, but there are limitations for 3D I think in all systems in a virtual.

You also need to let us know how much memory=ram you have as a virtual needs a certain amount to work.

Sorry if my post was confusing, it was meant to just make sure that we are all on the same page. And to be so some things need to be confirmed.

---

### Post by zvacet on 2010-12-08
@ [B]CommuneOfLoon

[/B]> How do I reinstall the grub?

See [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by CommuneOfLoon on 2010-12-10
Thanks, Wilee-Nillee.

I do have a Wubi, then; I installed 10gb of XP first (heard it was easier to do that first), and then installed 35gb of Ubuntu on the unformatted partition.

I have .5gbs of RAM.

For the VirtualBox, I intend on installed XP there, not Linux. I'll be running some technical software, on XP and need it to work; is VirtualBox (or VMWare, or other varient) stable with XP SP3 running on it?

Thanks for the link, Zvacet. I understand what I must do to get the grub onto the Ubuntu partition. Now how would I go about reclaiming the 10gbs in the XP partition (assuming you guys say virtualization is stable, which probably should have been my first question).

Thank you guys for all the information (I'm currently having an issue with two harddrives in a home-build, as well, and I think the info I get from the above issue will help me when I decide to tackle the new one :) ).

---


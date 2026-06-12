---
title: "Help With Dual Boot [Restoring Grub]"
date: 2011-03-09
forum: General Help
---

### Post by Reynbow on 2011-03-09
I just would like to double check, before I go and do anything, whether all this is correct.

I had Windows 7 installed as my primary OS.
I then made a 40GB partition for Ubuntu, installed that as a secondary OS.

I now use Ubuntu as my primary OS. I have now removed Windows, because it was pissing me off basically. I would like it back now, however. As a Virtualbox install of it does not quite do everything I need it to do.

Here's what my GParted looks like as of now

[img]http://img.photobucket.com/albums/v633/Sting81/Screenshot-1.png[/img]

Not sure if I should give more space to the Windows partition, is it easily extendable later on down the track? 

Will I need to format it to NTFS or something? Or will the Windows7 installation find it and do it itself?

And finally how do I restore Grub after installing Windows 7? As far as I know, I am using Grub2. (I'm using Ubuntu 11)

Thank you for any help guys.

---

### Post by wilee-nilee on 2011-03-09
You want to preformat the W7 partition to a ntfs, with gparted, this will keep W7 from installing 2 partitions, which in the past has caused partitions next to the install to go unallocated.

To reinstall grub follow this link it defaults to loading grub from a live Ubuntu disc; use the distro you have installed disc.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

As long as you preformat the partition for W7 your safe, but back up the Ubuntu with clonezilla or something.

Actually I just noticed the extended you will have to reduce the size of the extended and put the W7 in a primary outside of the extended. The resize of the extended is easy right click the swap click swap off, then delete it. Right click the extended=sda2 shrink it till it just has the size of the former swap unallocated run that then put a swap in the unallocated, then build the ntfs in a primary outside of the extended.

You can also shrink sda5 if you want when the swap is off to have more space for W7 when you shrink the extended.

---

### Post by Reynbow on 2011-03-10
> **wilee-nilee said:**
> Actually I just noticed the extended you will have to reduce the size of the extended and put the W7 in a primary outside of the extended. The resize of the extended is easy right click the swap click swap off, then delete it. Right click the extended=sda2 shrink it till it just has the size of the former swap unallocated run that then put a swap in the unallocated, then build the ntfs in a primary outside of the extended.

You can also shrink sda5 if you want when the swap is off to have more space for W7 when you shrink the extended.So I'm assuming that to do all of this I will have to boot into GParted live, yes?

---

### Post by wilee-nilee on 2011-03-10
> **Reynbow said:**
> So I'm assuming that to do all of this I will have to boot into GParted live, yes?

Yeah on a live Ubuntu cd or an actual gparted cd, both can be put on thumbs as well.

Should have mentioned the out of the installed Ubuntu use of gparted.

---

### Post by Reynbow on 2011-03-10
Righto, does it matter which one? 
Like, is it better to use the Ubuntu Live USB, cause I prefer to use the GParted USB, dunno, it just seems better lol.

And I'm fairly sure I know how to do what you've described.

---

### Post by wilee-nilee on 2011-03-10
> **Reynbow said:**
> Righto, does it matter which one? 
Like, is it better to use the Ubuntu Live USB, cause I prefer to use the GParted USB, dunno, it just seems better lol.

And I'm fairly sure I know how to do what you've described.

Use what your most comfortable with. ;) The key is turning the swap off always when messing with the partitions, basically.

---

### Post by Reynbow on 2011-03-10
So will the swap be outside the extended...? I'm still somewhat confused on the instructions you gave.

---

### Post by wilee-nilee on 2011-03-10
> **Reynbow said:**
> So will the swap be outside the extended...? I'm still somewhat confused on the instructions you gave.

The swap will only go in the extended. The W7 is the one out of the extended.

Read it carefully there are two options #1 just shrink the extended after removing the swap, when you shrink it you leave enough still unallocated between sda5 and sda2 to put the swap back in. You now have the unallocated 40 or more gig outside of the extended that is where the NTFS goes, put a bootflag on it by right clicking the built NTFS then flags then boot. #2 is just shrinking the sda5 if you want more gigs for W7.
I assume you know how to do a custom install with the W7 media.

---

### Post by Reynbow on 2011-03-10
Okay I think I understand. For me I think it would just be easier to shrink the whole extended partition. I can just out that space I partitioned originally for the win7 back into the ubuntu partition later anyway, right?

I don't have to mess around with the swap or whatever that way.

---

### Post by wilee-nilee on 2011-03-10
> **Reynbow said:**
> Okay I think I understand. For me I think it would just be easier to shrink the whole extended partition. **I can just out that space I partitioned originally for the win7 back into the ubuntu partition later anyway, right?**

I don't have to mess around with the swap or whatever that way.

I'm not sure what you mean here.

---

### Post by Reynbow on 2011-03-10
I can just put that space I partitioned originally for the win7 back into the ubuntu partition later anyway, right?

I mean the unallocated 50GB can be shrunken into the Ubuntu partition, yes?
Basically put the unallocated back into ext4

---

### Post by wilee-nilee on 2011-03-10
> **Reynbow said:**
> I can just put that space I partitioned originally for the win7 back into the ubuntu partition later anyway, right?

I mean the unallocated 50GB can be shrunken into the Ubuntu partition, yes?
Basically put the unallocated back into ext4

That is strange wording, sda2 and sda5 are separate there is no into. I'm going to assume you understand here I think you do.:)

---

### Post by Reynbow on 2011-03-10
EDIT; Ended up creating the GParted live USB and have successfully got all the partitions in order. **Is there any way to restore GRUB when I'm in windows, or at least use the windows boot loader and put Ubuntu into it's list.**

---

### Post by Reynbow on 2011-03-11
So my current GParted now looks like this. Hoping I've done everything right.

[IMG]http://img.photobucket.com/albums/v633/Sting81/Screenshot-1-1.png[/IMG]



So, still wondering if I can just add Ubuntu to Windows bootloader or restore GRUB while in Windows.
I have a program called EasyBCD and as far as I can remember it will give me the ability to Ubuntu into the Windows bootloader... I think lol

---

### Post by wilee-nilee on 2011-03-11
Partitions look good, easybcd2 works, I just am not familiar with it.

You can't reload grub from windows but you can from the live Ubuntu cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Just 3 commands sudo fdisk -l to identify the Ubuntu partition and the next two to load grub to the mbr.

I say use what your most comfortable with though.:)

---

### Post by Hakunka-Matata on 2011-03-11
Guys, does sda3 need a boot flag for Windows installer to find it's home?

---

### Post by wilee-nilee on 2011-03-11
> **Hakunka-Matata said:**
> Guys, does sda3 need a boot flag for Windows installer to find it's home?

You are correct I missed that, thanks. :) I mentioned applying it yesterday but forgot to check.

---

### Post by Reynbow on 2011-03-11
Okay thanks. I've added a boot flag to sda3.
Will acquire a copy of Windows 7 as my current one is a bit iffy I think... lol

Will hopefully have this sorted in the next couple of days when I find the time and energy to work with Windows again... =\
I'm sure you guys know how ... filthy ... it feels to work with Windows.

EDIT: Thanks again for all your help =]

---


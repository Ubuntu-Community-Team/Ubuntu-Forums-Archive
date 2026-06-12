---
title: "New LapTop, 10.04 disk ?"
date: 2011-02-02
forum: General Help
---

### Post by freeediver on 2011-02-02
I have a new lenovo g560 0679 aju, basic model.
I have done basic setup with windows 7 premium.
Now I would sure be grateful if someone could give
me a step-by-step that I could print out that would 
guide me thru the install process?
What I would like to do if possible is to have a 
partition or dual boot system.
I have installed very little at this point figuring
that now will be the easiest time to install a second
OS.
If I am able to do this how would I select Ubuntu to
be the OS I want to use keeping Win7 behind the wall 
so to speak. I have gotten used to 8.04 and really like
Ubuntu but don't really want to wipe my new comp and eliminate
Windows. The inst. tell me there is a hidden partition that
will back up windows and prevent deleting but I don't want to test that.

Thanks

---

### Post by coldraven on 2011-02-02
Did the machine come with restore discs? I mean CDs or DVDs.
If not you probably have to create them yourself. 
Then you are covered for any mistakes that happen now or in the future.
I don't know Lenovo or Win7, there must be instructions for doing that somewhere.

---

### Post by freeediver on 2011-02-02
No this machine does not have any restore disks due to the hidden partition. What is the process for making my own?

---

### Post by coldraven on 2011-02-03
I'm not a Win 7 expert but googling found this
[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)
another link mentioned using this disc to restore a disk image. 
I guess that this is what is on the restore partition. If so then there is probably a way to copy that partition to an external drive as an extra safeguard against loss. Or it may fit on to a DVD if you haven't installed loads of programs.
I can't check on my laptop because I deleted the restore partition and only use Windows in a virtual machine where it is easy to make backups of the whole Windows installation.

---

### Post by Jouke74 on 2011-02-03
Just te be safe, copy the whole disk (only the used space) with Clonezilla to an extrernal disk. It's always good to have a backup.

---

### Post by freeediver on 2011-02-03
I can make a backup restore disk with the info I have now.
Now how is a dual boot setup accomplished starting with a mostly clean machine? I have the 10.04 disk.
Can anyone do a step-by-step so I can print it out?

Thanks

---

### Post by coldraven on 2011-02-04
I'm not going to give you a definitive answer because I'm using 10.10.
Doing a quick google I found this which may be of use 
[http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/](http://www.techhamlet.com/2010/05/how-to-install-ubuntu-10-04/)
However, the main thing is this... if you boot up with the Live (Desktop edition) Ubuntu CD and select "Install" you will eventually get to the Partitioning manager.
It should detect your Win7 installation and give you an option to share the disc. I cannot remember if it will then automatically do the rest. But at any point before **finally committing** you can cancel the install with no changes made.
This would be a window informing you of the changes about to be carried out if you continue the installation. If you are confused stop there!
If you have do manually change your partitions then read the link above in the section "[B][COLOR=#FF0000]If you have an operating system installed :[B][COLOR=Black]"
[/COLOR][/B][COLOR=Black][B]Hopefully someone else will point you in the right direction.
[/B]
[/COLOR][/COLOR][/B]

---

### Post by freeediver on 2011-02-04
Thanks for that link I think it has answered most of my questions.
I sent for a recovery disk and as soon as I have it in hand I will give the install a try. The only question now is according to Lenovo my OS recovery option is behind a hidden partition implying
that it is not detectable by normal means,( ie no recovery disk needed), I sent for one anyway.

Thanks

---

### Post by coldraven on 2011-02-05
I think they mean the Restore partition is hidden from Windows.
To give you an view of your disc setup, boot up with your Ubuntu Desktop CD and select "Try Ubuntu".
Look  under System>Administration for Gparted, this is the program that  the installer uses to make space for an Ubuntu installation.
If it is not in the menu you can install it using Applications>Software Centre.
Don't worry, it is only installing into memory  not your hard disc.
Run  Gparted and you will see all your partitions, take a screenshot with  Applications>Accessories>Take Screenshot and post it here.
Quit Gparted without making any changes, unless you are brave :razz:

When  you eventually decide to install Ubuntu the installer will be shrinking  the largest partition to make room for Ubuntu and creating another  small one for Linux Swap space.

In my experience installing Ubuntu is easy and painless.

---


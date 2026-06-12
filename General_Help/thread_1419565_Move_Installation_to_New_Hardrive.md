---
title: "Move Installation to New Hardrive"
date: 2010-03-02
forum: General Help
---

### Post by R3M3 on 2010-03-02
The HDD on which I currently have my Ubuntu partition(s) (as well as a Windows partition) is dying on me (non-zero bad sector count, with warning pop-ups from Ubuntu). I have already ordered a replacement hard drive*, but I was wondering if there is a simple way to transfer the contents of my current hard drive to my new hard drive in such a way that the new one will be a fully functional replacement (e.g. so that everything will boot and run properly on the new hard drive).

*which is a different size (bigger) than the current drive.

---

### Post by switch10 on 2010-03-02
look for "clonezilla"

---

### Post by R3M3 on 2010-03-02
Um ... is there a simple way *with reasonable documentation* that will allow me to move my filesystems?

Call me crazy, but I'm a little wary about entrusting my data to a program which I don't know how to use (and whose authors aren't organized enough to use separate sections for separate programs in the FAQ).

---

### Post by oldfred on 2010-03-02
I recommend new clean install and copy /home and export the list of all your installed apps and reinstall.

Similar discussion:
[http://ubuntuforums.org/showthread.php?t=1416120](http://ubuntuforums.org/showthread.php?t=1416120)

How to list packages:
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by StuartN on 2010-03-02
> **R3M3 said:**
> Um ... is there a simple way *with reasonable documentation* that will allow me to move my filesystems?

Despite any impression you have from the documentation, Clonezilla is very easy to use and has clear on-screen dialogues.

If you plug the replacement drive in as a secondary then Clonezilla will duplicate the existing drive contents (and duplicate the UUIDs), so you can boot up off from the new drive without any further configuration. Clonezilla will even add the additional space to your partitions at the same time.

---

### Post by R3M3 on 2010-03-02
It appears I misspoke - the Clonezilla website does have documentation after a fashion (in the form of step-by-step instructions for some common use cases), but you have to hunt around a bit on the website in order to find them. (I'd provide links here, but the website uses frames, so I can't grab the address from the location bar.)

However, as the step-by-steps don't seem to give much information outside of "now choose this option", I had to Google search for more info. Most of it is repetition of the "these are the magical incantations to recite"-type step-by-steps, but I did glean likely answers to some of my questions:

*is ext4 supported? (Survey says: Yes, but you have to change the options such that Clonezilla uses the partclone program to do the copy, which may require digging through the advance options)

*does it make a bootable drive? (Survey says: Yes, though this may require doing a whole drive copy, and you probably want to check the advance options, to ensure that the copy MBR & reinstall grub options are selected - Clonezilla should be compatible with grub2, if you have a recent version - and god only knows what happens with other bootloaders)

*does it copy windows partitions in a bootable state? (Survey says: Yes, others have apparently been successful.)

*what happens to the extra space? (Survey says: If doing a whole disk copy, the extra space will be unallocated - if you choose the "Use partition table from source device" option in the Expert Mode. You would then need to use a disk/partition editor like gparted to resize/allocate/format the extra space to be usable. There's a "Create Partition table Proportionally" option which is supposed to scale all the sizes to match, but I didn't see anyone say that option worked for them. - I also have no clue which option is the default in Beginner Mode, so caveat newbie)

I think I know enough about Clonezilla to test things out, but I'm still deeply unsatisfied with things - if didn't have experience reinstalling Grub already, I might not have risked it. 

At least there is always the "screw it, I'm just going to reinstall from scratch" option.

---


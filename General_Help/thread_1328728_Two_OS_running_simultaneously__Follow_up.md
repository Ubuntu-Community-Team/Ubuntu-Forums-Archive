---
title: "Two OS running simultaneously?  Follow up"
date: 2009-11-16
forum: General Help
---

### Post by ibates on 2009-11-16
Further to my earlier post on this subject, I have now downloaded and installed VB 3.0.10.  I have also set up a Win XP Pro SP3 VM which works a treat.

BUT!  Now I know what I really wanted.  (Always a good idea to define at the outset, but in this case, I didn't know what I didn't know).

I really want to be able to access and run my original Windows setup as a Guest.  Windows is installed on my computer C: drive.  It is an IDE HDD.  Ubuntu 9.10 (the host) is operating on its own SATA HDD.  Both are independently bootable HDD.  Currently the boot choice is displayed by GRUB.

In GRUB, the Windows HDD is shown as /dev/sdc1.

I have read the VirtualBox manual and have noted in section 9.10.1 *Access to entire physical hard disk* that the facility to do what I want exists.  But I am not totally comfortable with the syntax of the commands shown in that section.

For example, what is for me to enter, and what is the actual command.

In the command *VBoxManage internalcommands creatrawvmdk -filename /path/to/file.vmdk -rawdisk /dev/sda -register* do I enter anything for the "-filename".  I assume I would nominate the name for the "file.vmdk", for example "CurrentWinXP.vmdk".

Typically, what would be the /path/to/file.vmdk.  The VB install was automatic.

In view of the Windows disk being shown in the GRUB as /dev/sdc1 would it be reasonable to assume that that should be substituted for "/dev/sda"?

Any assistance would be appreaciated.

---

### Post by niteshifter on 2009-11-16
Hi,

You should read [this post]("http://ubuntuforums.org/showthread.php?t=769883") carefully from the Virtualization area here.

It's a tricky thing - can render Windows unable to boot natively - and requires you accept some compromises in functionality.

---

### Post by ibates on 2009-11-16
Thanks for that.

I am not totally sure that this addresses what I am actually trying to do.

The referenced post seems to be concentrating on *installing* VB using the existing Win boot up.

What I want to do is merely be able to boot up Win from within the installed and running VB.  In other words, whilst running Ubuntu, run the installed VB and then be able to boot up the existing Win from its own HDD.  Then, after finishing whatever it was that I want to do with Win, to close it down within VB and deactivate VB.

Am I missing the point here?  Or is what I am trying to do even possible?

---

### Post by mechro on 2009-11-16
> **ibates said:**
> 

Am I missing the point here?

Yes, I think so. What you're referring to in your opening post is Virtual Box's facility to access an existing Windows installation from within VB. You can't "boot" this installation from VB.

If you think about it, if you're in Windows in its own hdd how would you get back to VB?...

---

### Post by t0p on 2009-11-16
A quick google for "how to boot existing windows installation from virtualbox" turned up [this handy-looking thread]("http://ubuntuforums.org/showthread.php?t=888324").

That's what you want, isn't it?

---

### Post by skatinjj on 2009-11-16
I tried making my current install of windows (/dev/sdb) a virtual machine (xp.vdi) and I used the command you mentioned in your first post. It worked but I had to activate windows everytime I switched between the virtual disk and the physical disk.

Also, I tried to hack the windows genuine advantage by removing its file but that made me unable to log into either disk.

I do not believe it is a good idea to try and use a install from a physical disk as it can render the physical install useless.

---

### Post by dcstar on 2009-11-17
> **ibates said:**
> 
........
What I want to do is merely be able to boot up Win from within the installed and running VB.  In other words, whilst running Ubuntu, run the installed VB and then be able to boot up the existing Win from its own HDD.  Then, after finishing whatever it was that I want to do with Win, to close it down within VB and deactivate VB.

Am I missing the point here?  Or is what I am trying to do even possible?

Accessing any HD that the host controls directly from a VM is **BAD NEWS**.

Every single PC OS is designed on the premise that it has sole control of any device directly connected to it, and if you run two things like this both with control of the one resource...... well, work out the potential problems for yourself.

So technically you can do it, but there is a reason every VM company strongly recommends that you do **not** do it.

---

### Post by SeanBlader on 2009-11-17
Doesn't VirtualBox also simulate it's own BIOS, which means that you might have some driver issues with the existing install running as a VM. It's like taking your hard drive and booting it on someone else's system, sometimes it works and you get lucky sometimes you wish you'd died first to save you the trouble of having to get all your data, then format and reinstall.

---

### Post by ibates on 2009-11-17
I think this will be my final post on this issue.  And I think, at long last after reading all the replies, and posts in various other forums as well, that I now understand what I actually want to do.

Amazing isn't it?  The troubles we get ourselves into by not logically describing what we actually want to do.

Up until now I have been referring to "booting" my Windows drive in VB.  It now appears that that is not what I want to do. I merely want to *access* my Windows drive from within VB.  And that is a very different kettle of fish indeed.

The wording in the VB manual, section 9.10.1 actually describes exactly what I wanted to do.  I simply did not understand the terminology used.  I think I do now.

So here goes .....

---

### Post by ibates on 2009-11-27
I have followed the instructions in the VB user manual 9.10.1 to the letter, and it does work.

I do not know why, but it took several attempts, but it finally created a vmdk for the Windows HDD.

So that problem is now solved.

But a new problem has appeared.

When running VB in Ubuntu and then attempting to run the new Windows vmdk, the Windows HDD upon boot up in the VM attempts to run the GRUB loader.  But that is far as it gets, because the GRUB loader can't find the Ubuntu HDD.  It all comes to a grinding halt.

Any suggestions how to overcome this latest hurdle?  I can appreciate the problem, but I can't work out a fix.

---

### Post by ibates on 2009-12-04
Problem solved.

I didn't need to reboot the physical disk in VB, it was there all the time.  But I did have to install the Windows apps I wanted to use in the VM Windows disk.

Then I had full access to everything on the physical disk, and using the VM Windows disk, I could do anything with the physical disk data, even save and delete to/from the disk.

All solved.

---


---
title: "The difficulty with changing from Windows"
date: 2009-11-29
forum: General Help
---

### Post by ibates on 2009-11-29
The is probably little more than a general whinge, but there is a problem at the end.

Over the past year or so, I have seriously attempted to understand and come to grips with Ubuntu.  I am by no means computer illiterate with practical as well as academic qualifications in the art.  But; like most of us, up until recently, it was either DOS or Windows.  Now, as I have already mentioned, I am seriously wanting to get away from Windows, and Ubuntu seemed like the logical choice.

Try as I might, I cannot easily understand what the heck is going on.  I acknowledge it did take years to become proficient with Windows and its quirks, so I don't expect to master a new OS in the first month or so.  But at least with Windows, most programs, or Windows itself, came with fairly comprehensive manuals or notes.  I know Ubuntu does also, but with totally different syntax and philosophies.

And trying to navigate around all this information requires so much time that I don't actually have much time left to put it into practice.

I don't know what can be done about that, but in my opinion, for the sake of Ubuntu becoming a serious competitor to Windows (whichever version), a more basic "handbook" needs to be made available in simple non-expert-ese.

This is just a thought which some sympathetic soul might latch on to.

But; let me highlight a problem which I feel could be typical:

For some time now I have needed to access programs installed in Windows, which unfortunately are not available for Linux systems.  I know I can do this by restarting Linux and booting back into Windows to run the program.  Very messy.

So I posted requests for assistance on this forum, and was advised to go for a VM running in Ubuntu.  VirtualBox was suggested.  So it was downloaded and installed in Ubuntu.  Then following being confronted by numerous obstacles in the pursuit of my ultimate goal, I requested more and more assistance from the forum.  Bit by bit, got answers to most of my queries, and in a manner a bit like pulling teeth, I eventually got VB to run, and my Windows HDD registered as a vmdk.

But now, trying to get access to that Windows HDD in a VM seems impossible.  (Obviously it is not, but I have no idea where to go to find out how).

Whenever I attempt to run the Windows HDD, it commences the boot procedure, but soon comes upon the GRUB file which apparently causes it to look for the Ubuntu HDD.  But, I assume, because Ubuntu is running, I get the following error message:

GRUB loading.
error: no such disk
grub rescue>

And that is where it all stops.

I have not attempted to go any further in case of damage to the Windows HDD (which by the way is backed up but restoration is an activity I do not need to have to go through).

VB is running on the Ubuntu host, not the Windows guest.

And this is the latest gap in what I believe should have been a simple process.  Of course, not a word is mentioned in the VirtualBox manual which I have read and re-read trying to find solutions.

So once again I must ask, has anyone any suggestions?

---

### Post by jm2 on 2009-11-29
Not sure if this would help. There is a program called Wine, which can run some of the windows programs.

There are a few others similar to that, but I can't remember right now.

perhaps that would help?

---

### Post by ed-koala on 2009-11-29
VB ... Visual Basic?  VirtualBox? or something else?  What other programs are you wanting to hang on to?  Run a hard drive?  or access files on the hard drive?

---

### Post by Meskarune on 2009-11-29
wait. you're trying to open programs installed in your windows partition inside a windows virtual machine running on ubuntu?

NOT a good idea. Just re-install the programs you want to use in the windows virtual machine. Or install the programs under wine. I know for a fact that ms word works under wine, and works faster than it does in windows. Photoshop works under wine as well. Though the more I use gimp, the more I've found it to have the exact same functionality. (it just takes time to learn it, so I still switch to photoshop sometimes)

I agree that there should be a simple user manual for users. Something like windows help center would be even better. 

Try checking out the arch linux wiki. It will give you information in a clear way.

---

### Post by capscrew on 2009-11-29
> **Meskarune said:**
> wait. you're trying to open programs installed in your windows partition inside a windows virtual machine running on ubuntu?

NOT a good idea. 
I saw that too.  I don't believe it's possible.  If it was it would be a mess.> 
Just re-install the programs you want to use in the windows virtual machine. Or install the programs under wine. I know for a fact that ms word works under wine, and works faster than it does in windows. Photoshop works under wine as well. Though the more I use gimp, the more I've found it to have the exact same functionality. (it just takes time to learn it, so I still switch to photoshop sometimes)
I use both Windows and Linux (mostly Ubuntu).  There are only a few Windows apps that can't be duplicated in FOSS.  There are however quite a few FOSS apps that I wish were available easily on Windows.> 
I agree that there should be a simple user manual for users. Something like windows help center would be even better.
Unfortunately this can't happen.  

MS controls all of the OS and Office code.  Other developers rely on the MS API too.  I see the positive of that.  The development, maintenance and help is unified and there is only one place to get information.  No anecdotal information needed.  

With FOSS each piece of the distro is created and maintained separately.  Sometimes different apps use the same libraries differently (e.g Samba and Gnome shares are slightly different).  Help can range from great to non-existent.  From amateur to the actual developer; all manner of help is welcome.  

Both sides have good and bad points.  In the end, neither is good or bad; just different.

---

### Post by john newbuntu on 2009-11-30
Just to clarify things here, virtualbox provides a separate environment for you to play with different operating systems like linux, unix and windows.  Since you run virtualbox in linux, linux is considered your host and any operating system that you run in the virtual box is the guest.
You can not access anything outside of the host from within the guest.  In fact you can not even access the host system from with the guest except folders that are marked shared.

So, if you need to run windows in a virtual box, you will have to perform a fresh install of windows from within your Linux virtualbox and then open windows applications from within it.  That leaves you with 2 windows installations on your machine.  Not a good idea.  If you really need a file from windows, it should be as simple as mounting your windows partition from within Linux and copy over any files you need.  Mounting this is as simple as going to places->documents.  You should see something like "30 GB filesystem" or some such number on the left panel.  Just click it, enter your password and you should have all your windows stuff available.
If you need to run windows apps frequently, then you are better off going over to windows at boot time and running apps there.  If you use windows sparingly, then virtualbox might be an option.

---

### Post by ibates on 2009-11-30
And here is the very problem I mentioned at the outset. My reading of the VirtualBox User Manual (para. 9.10.1 *Access to entire physical hard disk*) leaves me with a clear impression that I can create an image of my Windows HDD and that " .... the selected virtual machine will boot from the specified physical disk".  Those words are directly from the VB manual.

Where am I going wrong?

---

### Post by muteXe on 2009-11-30
I am completely confused I'm afraid.

Are there 2 problems here?
1. Booting into your windows partition.
2. Getting a windows virtual machine up and running in virtualbox?

These are 2 separate things, but reading your posts it seems like you think they're related somehow?  You've created a virtual machine in your ubuntu to try and access your files on your windows partition??
Sorry if i've got the wrong end of the stick here.

---

### Post by davidmohammed on 2009-11-30
mutexe is correct

If you want to access data from your Windows HDD then SAMBA will take care of that - you'll need to use ntfs config (from the repository) to mount the windows HDD.

If you want to run Windows programs you've got three choices - 
1. find a Open-source variant that does the same thing.
2. Install the Windows program in Wine.
3. Install the Windows OS first in Virtual Box and then install your programs in the VB session.

Probably a good idea to let everyone know what applications you are trying to run.

---

### Post by ed-koala on 2009-11-30
You cannot "run" a program from your already installed Windows drive from VirtualBox without installing it from within VirtualBox, plain and simple.  And, even if I happen to be wrong, you don't want to do it, you'll have countless problems.

Your choices are simple as stated above.

1.  Duel boot and run your Windows stuff that way.
2.  Install Wine, install your Windows programs using Wine, and run your Windows programs under it (check Wine's web site for compatibility first)
3.  Install VirtualBox, install Windows as a guest in it, then install your Windows programs inside your virtual Windows.

Ubuntu can read an NTFS formatted drive without doing anything so data like music, movies, etc on a Windows drive needs nothing done to be able to enjoy using them.

---

### Post by john newbuntu on 2009-11-30
I did read the section about "*Access to entire physical hard disk*".  The way I understand it is that instead of giving the guest OS a portion of the hard disk drive from your host OS, you can allocate an entire disk that is not used by your guest OS.  It clearly says:

> If your host operating system is also booted from this disk, please take special care to not access the partition from the guest at all.

So, this could be a case where, say, you have 2 hard disk drives.  Lets say the first one has both windows and linux, then you could allocate the entire second drive to virtualbox.

---

### Post by ibates on 2009-12-01
You are all correct and I thank you for the hints.

Upone once again re-reading the VirtualBox manual, nothing there suggests that I should boot the Windows physical disk in the VirtualBox VM.

In fact, all along, I had a clean install of Windows XP SP3 in a virtual machine, and right under my nose (which I couldn't see due to not knowing what to look for), I did have the full access to the entire physical hard disk on which I have always run Windows.

I have now installed that disk as the Primary Slave in the VM, booting from the clean Windows Guest installation in the VM, and then, simple as can be, having access to the physical Windows disk.

The only drawback to this procedure is that I must install whatever Windows applications I might want to use on the Guest VM Windows hard disk.  And even this is not a great problem as there will be no data, nor any tricky programs which I use rarely, and for which I can boot the original Windows physical disk if I need access.

Once again, I thank you for your rapid assistance.  And hopefully, this also illustrates the meaning of my title to this thread.

---

### Post by HeadHunter00 on 2009-12-23
Try not to use virtualbox, instead try finding alternatives or maybe run windows programs under wine.  You should only use virtualbox in an absolute emergency. If want better compatibility, buy crossover suite.

---

### Post by reiki on 2009-12-23
I have VirtualBox installed for this very reason. I have a couple of Windows apps for which there is no linux equivalent. Since they are for specific medical equipment, a linux equivalent is probably not too likely.  I keep a native Windows7 install on the hard drive, but I don't boot to it very often. Sometimes not for months. The VirtualBox solution works pretty well. Yes, it's not necessarily conveneient to reinstall a windows app into the virtual machine, but I usually only have to do it once. Now if I migrate to a new Ubuntu install, I can simply move the VM to teh next installation and I don't have to reinstall those windows apps.

---

### Post by blur xc on 2009-12-23
> **reiki said:**
> I have VirtualBox installed for this very reason. I have a couple of Windows apps for which there is no linux equivalent. Since they are for specific medical equipment, a linux equivalent is probably not too likely.  I keep a native Windows7 install on the hard drive, but I don't boot to it very often. Sometimes not for months. The VirtualBox solution works pretty well. Yes, it's not necessarily conveneient to reinstall a windows app into the virtual machine, but I usually only have to do it once. Now if I migrate to a new Ubuntu install, I can simply move the VM to teh next installation and I don't have to reinstall those windows apps.

I run both windows in VBox and dual boot.  I tried wine, but nothing I tried in it would run.  Applications like Leapfrog Connect, Sansa media converter and updater, lightroom (long shot anyway), lego digital designer, to name a few...  In Vbox, a few would run, but other still would not, like lego digital designer, and the sansa software.  For those, I still have to dual boot.  but for the others, it's quicker to just fire up the vm.  VBox has come a long way in just the last 6 months that I've been using it.  They are doing impressive work over there, and maybe, eventually, the other apps I need to dual boot for will work under Vbox too...

BM

---


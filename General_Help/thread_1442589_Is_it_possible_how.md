---
title: "Is it possible? how?"
date: 2010-03-30
forum: General Help
---

### Post by 664748 on 2010-03-30
[SIZE=2]Alright, ive got ubuntu installed, disk is not partitioned. now i want to try putting up windows, but unfortunately whenever i insert the disk installer of windows it doesnt recognized the disk installed with ubuntu. now my problem is how can i install windows if ubuntu is on that disk? will i partition the disk first? and after partitioning, will that be recognized by windows? i need your help badly...:([/SIZE]

---

### Post by realzippy on 2010-03-30
Generally it is much easier to install windows first;windows
cannot see "linux" and its filesystem.So you should start your ubuntu
and create some free disc space for windows;easiest is to start a Ubuntu Live CD and run *gparted* to shrink your existing Ubuntu partition...
Then install Windows what overwrites your Grub (Linux boot loader) which
you will have to "repair" afterwards so that it "sees" both OS...


...suggest the other way..windows first,then linux,no probs....

---

### Post by 664748 on 2010-03-30
im having problems in installing windows at first, it gives me bios error. thats why i tried using ubuntu. is it also acceptable if ill just use virtual box to have windows over ubuntu instead?

---

### Post by realzippy on 2010-03-30
*is it also acceptable if ill just use virtual box to have windows over ubuntu instead?*

Depends on what you want to do with "windows".....you will not have good 3D acceleration e.g.


Can you specify your "bios error" ?
(bios error should have nothing to do with a non existing OS)

As suggested,you can take the "hard" way:
Run Ubuntu LiveCD,open gparted,shrink ubuntu,then install windows,then set up GRUB....

---

### Post by derekeverett on 2010-03-30
> **664748 said:**
> im having problems in installing windows at first, it gives me bios error. thats why i tried using ubuntu. is it also acceptable if ill just use virtual box to have windows over ubuntu instead?

It is absolutely possible to have Windows run in a virtual machine within Ubuntu. But in my experience this depends heavily on your install media. If it is a full install disk registered to you or some sort of less legal option than it can easily be done. 

However, many OEM copies of Windows don't work in virtual machines. 

At least that's accurate to the best of my knowledge. If I'm wrong hopefully I'm corrected soon.. or at least someone else more knowledgeable could expand on that. I'm not real fond of VM's and my experience is limited.

---

### Post by amite on 2010-03-30
i am using 3 partition on windows and now i want to give more space to ubuntu.so i want to locate a partition to ubuntu which is yet used by windows.is it possible.
if yes,please suggest how?

---

### Post by realzippy on 2010-03-30
> **amite said:**
> i am using 3 partition on windows and now i want to give more space to ubuntu.so i want to locate a partition to ubuntu which is yet used by windows.is it possible.
if yes,please suggest how?

Run Ubuntu LiveCD,run **gparted** to resize/delete/dowhatever with your partitions.

BTW,please open your own thread,you are a threadnapper!!  ;-)

---

### Post by 664748 on 2010-03-30
> **realzippy said:**
> *is it also acceptable if ill just use virtual box to have windows over ubuntu instead?*
 
Depends on what you want to do with "windows".....you will not have good 3D acceleration e.g.
 
 
Can you specify your "bios error" ?
(bios error should have nothing to do with a non existing OS)
 
As suggested,you can take the "hard" way:
Run Ubuntu LiveCD,open gparted,shrink ubuntu,then install windows,then set up GRUB....
 
 
 
the bios error im reffering with is that after the initial installation of windows it would reboot right. now after rebooting it would go to the bootup screen of winxp then afterwards it would show a blue screen showing " windows needs to shutdown... reason bios outdated... bla'bla'bla" and then it would restart and go to that same error page again then again then again.. thats why i installed ubuntu first... i think i will just do the hard way.. but im not yet familiar with doing that since its my first time to try it.. 
 
how will i set up GRUB?

---

### Post by realzippy on 2010-03-30
Know nothing about BIOS "outdated" error.It is very likely that this error will occur also.What about an actual BIOS?

Some ACPI BIOS problem?You have a switch for ACPI in your BIOS?

---

### Post by 664748 on 2010-03-31
> **realzippy said:**
> Know nothing about BIOS "outdated" error.It is very likely that this error will occur also.What about an actual BIOS?
 
Some ACPI BIOS problem?You have a switch for ACPI in your BIOS?
 
yes it is ACPI BIOS problem. i dont have any switch for acpi

---

### Post by Gatorade on 2010-03-31
unless you know what you're doing , I'd strongly recommend against installing windows after Ubuntu. 

as already mentioned, windows will delete your Grub boot loader(this is what gives you the option to choose which OS you want to load when the computer is booting up) and its a major pain in the **** to reinstall it.

there are tutorials on how to do it , but I , being somewhat new to linux myself found it very frustrating to do so I gave up and re-installed windows first and then linux, it was a piece of cake that way.

not sure about the BIOS question.

---

### Post by realzippy on 2010-03-31
*yes it is ACPI BIOS problem. i dont have any switch for acpi*

...normally there is a switch.Have you checked your mainboards vendor
for a newer BIOS?

In some BIOSs there is a "hidden" Sub-bios,enabled by a special key sequence.

---


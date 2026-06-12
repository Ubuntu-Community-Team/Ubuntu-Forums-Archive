---
title: "Hard Drive Partitions"
date: 2006-02-23
forum: General Help
---

### Post by cparsons on 2006-02-23
I am running Hoary and need to wipe my hard drive, and remove all the partitions, so i have a completely blank hdd. how do i go about this???

:-k  :-k  :-k

---

### Post by aysiu on 2006-02-23
Fire up the Ubuntu installer CD and choose to erase the entire hard drive.

---

### Post by cparsons on 2006-02-23
Will try that now, thank you! \\:D/

---

### Post by cparsons on 2006-02-23
Would you be able to specify how i do that exactly - remove everything?

---

### Post by aysiu on 2006-02-23
[QUOTE=cparsons]Would you be able to specify how i do that exactly - remove everything?[/QUOTE] When you get to the partitioning part of the installation, select **Erase entire disk** (see screenshot) instead of **Manually edit partition table**.

The image is courtesy of Herman's excellent dual-boot guide (fifth link of my sig).

---

### Post by cparsons on 2006-02-23
ah, great - this is where i ran into problems last time. you see, when i selected "erase... blah blah" - it would go ahead and delete and re-partition - i need a blank hdd with no partitions, how do i stop it from continuing with the install? :confused:

---

### Post by aysiu on 2006-02-23
[QUOTE=cparsons]ah, great - this is where i ran into problems last time. you see, when i selected "erase... blah blah" - it would go ahead and delete and re-partition - i need a blank hdd with no partitions, how do i stop it from continuing with the install? :confused:[/QUOTE] Ah! I thought you wanted to reinstall with everything clean...

Do you have a live CD (Knoppix... live Ubuntu) handy?

---

### Post by cparsons on 2006-02-23
actually, i do have a live cd. instruct away!:)

---

### Post by aysiu on 2006-02-23
[QUOTE=cparsons]actually, i do have a live cd. instruct away!:)[/QUOTE] Okay, assuming it's a live Ubuntu CD (let me know otherwise), boot it up. 

Then open up a terminal (In Hoary, Applications > System Tools > Terminal; in Breezy, Applications > Accessories > Terminal) and type these commands ```
sudo apt-get update
sudo apt-get install gparted
sudo gparted
``` You should get something like [this](http://gparted.sourceforge.net/screens/gparted_4_big.jpg). Go ahead and delete all the partitions (right-click works, I think) and then commit the changes.

---

### Post by cparsons on 2006-02-23
i don't have an internet connection on that laptop.

---

### Post by aysiu on 2006-02-23
[QUOTE=cparsons]i don't have an internet connection on that laptop.[/QUOTE] Okay. That could be a problem. You don't happen to have a Knoppix CD on you, do you?

By the way, why do you want to wipe the entire hard drive clean and *not* install anything on it?

---

### Post by cparsons on 2006-02-23
nope, i don't have one of those cds.

its a long story, regarding why i want a blank hdd, but basically, my employer has done the dirty on me and stated that i can't run my laptop with ubuntu at work on their network as part of some new protocal. (yuk) and so now i have to install windows 98 on the work laptop. (but i am keeping ubuntu on my personal desktop of course!!!)

---

### Post by mr_mop on 2006-02-23
I'm pretty sure one of the discs here:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
has fdisk on it.
Try that to remove all partitions?

---

### Post by aysiu on 2006-02-23
There are a couple of things you could try.

You could try doing an "expert" install of Ubuntu. I believe in that mode, you can skip to different parts of the process, so you can go straight to partitioning, and then finish without installing anything.

Do you have access *anywhere* to broadband internet and a CD burner? If so, it shouldn't be too difficult to get ahold of Knoppix. Are you familiar with the process of burning ISOs?

---

### Post by jamesr on 2006-02-23
> and so now i have to install windows 98 on the work laptop

One of the Win98SE startup floppies has FDISK (microsoft version) on it or go to a working 98 system and generate a startup disk.  

Start ==> Settings==> Control Panel ==> Add or remove programs ==> 3rd tab along Startup disk and follow instructions. 

Is your boss going to W98 or W98SE ? 

Also the Micro$oft support on W98SE which was extended once, after pressure from Europe and Asia, looks as if it finally end in 2007 and apparently there will no more security updates. I still have users with W98SE systems so it should be interesting. Infact my FAX PC runs W98SE because the drivers for the scanner / SCSI card do not work or are not available for anything later than W98SE

May have to go to linux :D

---

### Post by cparsons on 2006-02-24
"I'm pretty sure one of the discs here:
[http://www.bootdisk.com/](http://www.bootdisk.com/)
has fdisk on it.
Try that to remove all partitions?"

how do i f-disk - is it difficult???

---


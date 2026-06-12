---
title: "USB Startup Disk Creator doesn't respond"
date: 2010-01-19
forum: General Help
---

### Post by Jefferythewind on 2010-01-19
Hi, 
  I have been an Ubuntu user for a few years now, and in the previous versions I have made numerous bootable USB devices, I always thought it was so useful, and I never have had any problems.  
  I just installed version 9.10 the other day, and it seems to be working well, but the USB bootable disk creator is messed up big time.  
  When i try to select an .iso image to add to the source disk image area, it is just unresponsive.  And when i try to do something else, like format a USB device, it says i cannot format because the device cannot be mounted.  But i know its mounted because i can access the contents of the drive.  

  Anyways this was a huge disappointment as I was showing a friend how useful the UBUNTU tools are, and it does this.  Does anyone know anything about this bug?

Thanks.

---

### Post by arubislander on 2010-01-19
I don't think it's a general bug in Karmic, since I've created numerous bootable usb thumb drives with Ubuntu 9.10. It may be somtheting specific to your configuration.

Are you using an .iso image that worked with an earlier version?
Did you try unmounting your usb device before starting up the tool?

---

### Post by Jefferythewind on 2010-01-19
I have not yet tested trying an ISO file that I am sure worked before, but I don't think there should be any problem with the files I am using.  One is an ISO file download from the Lenovo website that makes a bootable drive to update the BIOS of my system.  I open up the file browser to locate the file i want to use, and after i find and click OK, it just does nothing.  There is no file path entered into file path area.

I have also tried removing and re-installing the program multiple times in synaptic.  It behaves the same way every time :-(

---

### Post by Jefferythewind on 2010-01-19
I think i may have found the problem.  No where is the Ubuntu documentation does it say that it will make a bootable device for anything other that Ubuntu systems.  The file i referred to in the previous post would then not work.  Is this correct?

---

### Post by efflandt on 2010-01-19
USB Startup Disk Creator is for Ubuntu based systems, but they can be alternative Ubuntu system.  For example I have used it for Qimo for kids (based on 8.10), 9.04 (or Mint7 based on that), or 9.10 Kubuntu or Ubuntu (or Mint8 based on that), in 32 or 64-bit.  But you don't need to create it from the same bit system (a 32-bit system can use 64-bit iso to make bootable USB).

You might look at unetbootin which has other options and supports other systems.

Since it uses FAT or FAT32 on the USB, a persistent filesystem (casper-rw file) cannot be larger than 4 GB, and if using 4 GB or less USB, make sure the persistent slider is down at least one click from maximum.

---

### Post by Jefferythewind on 2010-01-19
Yeah, i made a bootable USB for Mint before also.  But for the example i brought up earlier about .iso file with my BIOS update, i don't know if it will work.  Anyway if you know anything please let me know, thanks, 

Tim

---

### Post by C.S.Cameron on 2010-01-19
I have also had a few problems with usb-creator in 9.10 with Kingston flash drives.
Sometimes it works, when it doesn't work I get a login screen asking for username and password. ubuntu with a blank password does not work.
I have not had any luck getting u-c to make a Xubuntu Live USB.

Edit:
I take that back about Xubuntu not working with usb-creator.

---

### Post by Monotoko on 2010-01-19
C.S, have you tried downloading another iso/checking the one thats written to that USB?

That problem is commonly found if the iso wasnt downloaded/didnt write correctly

---

### Post by C.S.Cameron on 2010-01-19
It had the right md5sum on my desktop but went bad when the iso was transferred to my laptop.
I'll give it a try once I figure out how to make Xubuntu persistent. the casper-rw partition does not seam to be working.


Edit:
Thanks, usb-creator is working great now.
I was forgetting to type "persistence" in the text.cfg file.
It's working now also.

---

### Post by Jefferythewind on 2010-01-19
OK, i just tried writing a version of ubuntu 9.04 as a USB startup device.  I know i used this file to make a startup before.  The file loads into the software correctly, but at the bottom, it says my usb drive needs to be formated before i use it.  and then when i click format i get an error that says this:

DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

What is the problem here?  I know it is right there.  I just used GParted to format the whole drive into fat32 fs.  please can somebody help me.

---

### Post by C.S.Cameron on 2010-01-19
I have had problems formatting with usb-creator.
I just hit Make Startup Disk and decline to click Format and it seems to work.

---

### Post by arubislander on 2010-01-20
> **Jefferythewind said:**
> Yeah, i made a bootable USB for Mint before also.  But for the example i brought up earlier about .iso file with my BIOS update, i don't know if it will work.  Anyway if you know anything please let me know

You cannot use USB Startup disk creator to make startup disks of any .iso image except Ubuntu and it's derivatives. So, no, your BIOS update .iso will simply not work.

---

### Post by Jefferythewind on 2010-01-20
Yeah, i understand now how the usb creator only works for ubuntu iso files.  But it still doesn't work for me because it says the usb drive cannot be mounted... I have to say that i had to revert to windows to make the bootable usb for me... :-\

---

### Post by Jefferythewind on 2010-02-06
Hi Everybody, I am coming back to my thread here because i have found myself wanting to make a bottable Ubuntu USB for a friend, and I am still having a problem with USB creator recognizing my usb disk.
 After i click, "format", in the creator, i get an error saying the USB cannot be mounted.  Then when i try to open the USB file browser, i get another error saying that there is a job pending on the drive so i can't open it....

  It is kind of weird, but actually i was just messing with it and pressing different buttons, and the button that says "make startup disk" finally became usable.  I clicked it, and it seems to be working.

---


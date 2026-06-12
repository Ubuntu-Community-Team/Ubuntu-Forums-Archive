---
title: "Unable to find Unetbootin"
date: 2011-06-05
forum: General Help
---

### Post by Scunnered on 2011-06-05
I am proposing to download 11.04 on a USB pendrive and find that having downloaded Unetbootin from Synaptic I am unable to locate it in any menu.

Can you also advise if by using this method that I can have a persistant setting as this appears to be essential to a smooth performance.

---

### Post by celticbhoy on 2011-06-05
Unetbootin wont let you create a persistent file, for that you need to use the 'Startup disk creator' from the System -- Admin menu (assuming you are using gnome classic). If you decide you really want to use Unetbootin it is found in the Applictions -- System sub menu (Again assuming you are using classic).

---

### Post by Scunnered on 2011-06-05
**celticbhoy**

Thanks for your reply.  Looks like UNetbootin is not going to resolve my problems.

I had tried Startup disk creator but found that I could not get it to work for me.  When I open it up what I take to be the the area that will set things up to be persistant is greyed out. Can you say how I can overcome this problem.  It shows that there is a slider to set something but I can't change anything.

Thanking you in anticipation

---

### Post by celticbhoy on 2011-06-05
in the USB device selection your USB drive will show twice, select the bottom one, that should allow you to adjust the size of the persistent file, and start the install.

---

### Post by Scunnered on 2011-06-05
**celticbhoy**

Many thanks I will give that a try and report back.

---

### Post by Scunnered on 2011-06-05
**celticbhoy**

So much for that theory.  Loaded the 8GB USB pen drive and it showed only 1 drive. This could be that I have knackered it by various attempts between Startup Disk Creator and Lexar BootIt in order to fix the install as a persistent file.

Found an older and smaller drive 2GB which displayed both drives as indicated but still had all the information greyed out below the drive data. Attempted to see if it would open but nothing again.

Could it be that I might have to do a complete fresh install of 10.04 which would be a real pain in the neck.

What are your feelings in the matter?

---

### Post by celticbhoy on 2011-06-05
I dont think you should have to resort to a fresh install. First try using gparted to delete the current file structure of the 2G drive, create a single partition of type FAT32, and format it. If you still have no luck then rather than re-install your current install, make a live disk (CD) and use it to create the USB drive. I have a netbook with three separate Ubuntu installs, all dif versions, and USB creator only works on one of the installs.

Gparted may not be installed by default, if not its just 'sudo apt-get install gparted' from a terminal.

---

### Post by Scunnered on 2011-06-05
**celticbhoy**

I will have a look at your suggestions and see what happens. I had hoped that the age of miracles was still with us but it looks like they take much longer now.

I am off for a weeks holiday so unless I get lucky before the morning I will have to get back to you much later.

Meanwhile many thanks for your guidance.

---

### Post by celticbhoy on 2011-06-05
> **Scunnered said:**
> **celticbhoy**

I will have a look at your suggestions and see what happens. I had hoped that the age of miracles was still with us but it looks like they take much longer now.

I am off for a weeks holiday so unless I get lucky before the morning I will have to get back to you much later.

Meanwhile many thanks for your guidance.

No problem, hope it works for you

---

### Post by Scunnered on 2011-06-07
**celticbhoy**

With all the wonderful weather on display at home I had the foresight to take my pen drive with me. 

I kept battering my head against the proverbial brick wall attempting to get the Startup Disk Creator to open up the area to effect a persistent file.

Guddled about various forums and found that if the .iso is not instantly displayed in the display that by using OTHER and finding where it was parked will open up the .iso and everything else.  I parked the .iso on the desktop and following the guide found that a persistent download to the USB was possible.

Just got to find the time to prove that my hopes have been realised.

Again my thanks for your kind assistance.

---

### Post by celticbhoy on 2011-06-07
Sorry mate,forgot to mention you need to select the ISo file, unless its in a default directory.

---


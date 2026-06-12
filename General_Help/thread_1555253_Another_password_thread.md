---
title: "Another password thread"
date: 2010-08-17
forum: General Help
---

### Post by geod919 on 2010-08-17
I am trying to install the driver for my lexmark x4650. 
I have the installer running, and it asks for my administrator/root password. I am inputting it correctly, I checked caps lock and all of that. I checked to make sure I was indeed set as the administrator, I am. I don't know if I have the correct root password, if it is not the same as the admin, I have never changed it. It is not the normal ubuntu password screen. 

I'm running 10.04 on an HP laptop.

If I missed anything, I will add to this post, I will help you help me lol.

---

### Post by hyperdude111 on 2010-08-17
Just use the password your your account not root.

---

### Post by geod919 on 2010-08-17
I have been, It does not work.

---

### Post by Quackers on 2010-08-17
Where have you got the driver from and what exactly are you doing that requires a password?

---

### Post by hyperdude111 on 2010-08-17
Which account are you logged in as yourself or root ?

---

### Post by geod919 on 2010-08-17
I am logged in as the sole user. It requires the password to start installing I guess, I'm at 0% on the loading bar.
I got the driver from lexmark.com

---

### Post by hyperdude111 on 2010-08-17
> **geod919 said:**
> I am logged in as the sole user. It requires the password to start installing I guess, I'm at 0% on the loading bar.
I got the driver from lexmark.com

0% so it didn't say the password was wrong, leave it alone it's downloading the driver. The progress bar is wrong in the 3rd party driver program.

---

### Post by geod919 on 2010-08-17
No no, the loading bar is in a different screen lol, It won't start until I enter a correct password, and it tells me my passwrod is incorrect no matter what I do.

---

### Post by ercferret18 on 2010-08-17
Try this:

At a terminal, type in "sudo passwd root" and make a password for root. Then type that into the driver program.

---

### Post by Quackers on 2010-08-17
When you say you "have the installer running" - what does that mean exactly? Did you download the package for deb based linux and run the terminal command? Or is there a Windows-type installer running?

---

### Post by geod919 on 2010-08-17
I am running I guess a windows based installation, I am not inside the terminal, Although it has an open in terminal option, this pops the same two windows, plus the terminal lol.

I will try the sudo password

---

### Post by geod919 on 2010-08-17
That did it, Thank you.

---


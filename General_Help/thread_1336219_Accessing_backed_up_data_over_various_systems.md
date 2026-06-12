---
title: "Accessing backed up data over various systems"
date: 2009-11-24
forum: General Help
---

### Post by Scunnered on 2009-11-24
I have a spare desktop having purchased a laptop on which I run Ubuntu.  I was considering using the desktop as a means of storing approx 30 GB of pictures that my partner wants backed up away from her laptop.  I would back up everything in Ubuntu on the desktop.

Currently both laptops are sharing a wireless connection and a USB connected printer to the Ubuntu laptop.  Her laptop currently has XP as the OS and I am attempting to show her the error of her ways and slowly getting there.  What I would like to know is if I backup the photographs to the desktop and connect it to my router will both of us be able to access the data.

My beginning Ubuntu Linux book is not too helpful in this regard.  It keeps referring to dual boot and accessing Windows, my preference in to do everything in Ubuntu and then let have XP have access.  

Can you please offer guidance on how I should best approach this matter.  I would wish to be able to access all backed up data on both laptops.    

Thanking you in anticipation

---

### Post by Darael on 2009-11-24
If you back up to the desktop and activate the relevant folders as shared, that will set up SAMBA sharing, which will allow both Ubuntu and Windows to reach the files on it.

If that's not clear, please to say so and I'll give a full step-by-step guide.

---

### Post by Scunnered on 2009-11-24
**Darael**

Many thanks for your kind reply.

I took a folder on my laptop and was able to find the share option ok.  On going to the XP laptop I could find the folder on the network but was asked for a password for this.

It was at this point that things fell down. Neither of our passwords would open the folder.  I offered up my usual login on Ubuntu and Brenda offered hers on XP but nothing worked. Can you offer further guidance.

---

### Post by Darael on 2009-11-24
It should be shared such that your username and password will open the folder.  If it isn't, try enabling the "guest access" option near the bottom of the sharing settings section.  In theory, it allows access without a username and password.

---

### Post by Scunnered on 2009-11-24
**Darael**

Your advice worked a treat.  Brenda can now see 4 years of pictures as a slide show.

My sincere thanks for all your kind assistance

---


---
title: "Device Files Don't Exist After Ubuntu 10.04 Install"
date: 2010-11-07
forum: General Help
---

### Post by digiPixel on 2010-11-07
After doing a Ubuntu 10.04 install the PC fails to boot citing a UUID that doesn't exist. Upon examining the dev directory (on the root partition) I discovered to my own horror that the sda device files don't exist! Below is the partition setup:

[LIST]
[*]/dev/sda1     WinXP
[*]/dev/sda2     Ubuntu
[*]/dev/sda5     Home
[*]/dev/sda6     Swap
[/LIST]

Is it possible to copy over existing device files to the root partition? Tried copying over copies from the temporary live CD partition but ended up with the terminal freezing.

The Ubuntu installer finished successfully although it had applied some updates during installation. Everything else exists on the root partition apart from the required device files.

---

### Post by coffeecat on 2010-11-07
The sda files (among others) in /dev are virtual ones generated during bootup. That's OK to not have them there if you are examining the partition from the live CD. If it fails to boot up because of a UUID problem then we need to look at the UUIDs.

Boot up with the live CD. Make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there and post the contents of the RESULTS.txt file. Please note what those instructions say about posting the output in code tags by using the # button above the message field.

That output will contain everything we need to know pertaining to UUIDs and your new installation.

---


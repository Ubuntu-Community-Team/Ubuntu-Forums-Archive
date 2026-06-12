---
title: "Puppy Linux install with Ubuntu"
date: 2011-02-26
forum: General Help
---

### Post by Diametric on 2011-02-26
can anyone tell me how to install puppy linux while logged into Ubuntu?

I've got the .iso on a cdrom, as my bios can't be flashed to allow a usb install - despite the cdrom being set to primary, it still won't boot to it.

So, I've got the .iso on a disk ans wish to set up a dual boot of Puppy and Ubuntu, how can I pull this off?

---

### Post by C.S.Cameron on 2011-02-27
Perhaps stick Puppy on its own partition and make a new menuentry in Ubuntu's grub and point it to puppy.

Check out how MultiBootUSB does Puppy for some insite.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

### Post by oldfred on 2011-02-27
I did what C.S.Cameron posted but manually. I also cheated and had looked at how the script did it. With that info and some experimentation I was able to both boot from a USB and from HD using grub2.

[http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy&page=2](http://ubuntuforums.org/showthread.php?t=1600093&highlight=puppy&page=2)

---

### Post by Diametric on 2011-02-27
> **C.S.Cameron said:**
> Perhaps stick Puppy on its own partition and make a new menuentry in Ubuntu's grub and point it to puppy.

Check out how MultiBootUSB does Puppy for some insite.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Worked like a charm!  Thank you for your reply...

---

### Post by Ecnerwalification on 2011-02-27
Puppies?! Where???????? :D :D :D

---


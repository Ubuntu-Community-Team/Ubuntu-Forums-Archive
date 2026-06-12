---
title: "Trash Can Customization"
date: 2011-06-11
forum: General Help
---

### Post by carmenat250 on 2011-06-11
In Windows 7, you can right click on the trash can, go to properties and set it up so that when you delete a file, it does not go to the trash can, but is instead truly deleted with no recovery.

Is there something similar that can be setup with Ubuntu 10.10?  I didn't see a properties option when I right click on the trash can in Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-06-11
You can try these:

[http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)

---

### Post by nzjethro on 2011-06-11
Not sure about manually configuring it, but as a workaround, check out Autotrash. It lets you purge the trash from your can if it is older than x days, or if it contains x Mb of data. Try setting days to 0, or Mb to 0 to see if that resolves it.

```
sudo add-apt-repository ppa:bneijt/ppa
sudo apt-get update
sudo apt-get install autotrash

```

[http://maketecheasier.com/4-more-ways-to-clean-up-your-ubuntu-machine/2010/08/06](http://maketecheasier.com/4-more-ways-to-clean-up-your-ubuntu-machine/2010/08/06)

---

### Post by flipper T on 2011-06-11
open your home folder

goto edit / preferences / behavior

there is an option to add "delete" on your right - click menu

this does what you want

---

### Post by Frogs Hair on 2011-06-11
> **carmenat250 said:**
> In Windows 7, you can right click on the trash can, go to properties and set it up so that when you delete a file, it does not go to the trash can, but is instead truly deleted with no recovery.

Is there something similar that can be setup with Ubuntu 10.10?  I didn't see a properties option when I right click on the trash can in Ubuntu.

Just so you are aware of it , when you bypass the trash can in win 7 the file can still be recovered with a recovery tool  . You need a utility that includes a file shredder .

---

### Post by flipper T on 2011-06-11
i don't think that the win 7 function that he / she wants to replicate shreds the data either

perhaps OP could clarify

---

### Post by carmenat250 on 2011-06-11
The Win 7 function doesn't shred the file and I'm not overly worried about that myself.

Just want the file to be gone without having to empty the trash bin.

---

### Post by Brian R. on 2011-06-12
Just left click the file and press the delete key on the keyboard.

File gone.

---


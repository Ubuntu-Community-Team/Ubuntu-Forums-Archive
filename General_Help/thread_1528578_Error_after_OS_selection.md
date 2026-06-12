---
title: "Error after OS selection"
date: 2010-07-10
forum: General Help
---

### Post by Seraphina on 2010-07-10
There is a screen that gives 5 options

"Ubuntu Linux"
"Ubuntu Linux Recovery Mode"
"..." <--- Can't remember
"..."
"Ubuntu 10.04 LTS"

I select the bottom one and get the following errors...

"error: no such device 00afa1a4-9756-4dde-bfd3-818f264-37ee"
"error:hd1, 5 cannot get c/H/S values"

I had JUST finished my first Ubuntu installation on a 12GB Hard Drive. There was an 80GB with a failed installation on it that I had removed just before the error occured. I assume that my 80GB drive is "device 00afa1a4-9756-4dde-bfd3-818f264-37ee".

Please, I would finally like to get the week of pain and torment over with.

---

### Post by Seraphina on 2010-07-11
sorry but bump -__-

---

### Post by Pizack on 2010-07-11
Did you edit fstab yourself? If so the UUID of the device might be wrong.  Easy to make a typo there.  If you backed it up (you always should, and be sure to date your backups!) then you can try the old version of fstab.  Fstab can be found by typing ```
sudo gedit /etc/fstab
```

Did you configure Grub2 yourself?  Try booting from the live CD and running ```
sudo update-grub
``` in the terminal.  Let me know if that helps. 

Also, did you specify a mount point when you installed?   If not, then the drive is likely not mounting.  The mount point for your Ubuntu drive or partition should be simply this:```
/
``` 

Others are likely more knowledgable on this than me, and these ARE guesses.  Best of luck.

---

### Post by Seraphina on 2010-07-11
I never added a edited fstab I'm not really knowledgeable enough to do that yet, but the OS is trying to boot from the UUID if the 80GB drive that is currently out of the system. How would I make it boot from the 12GB instead if I know the UUID.

I did however get into Ubuntu/Linux mode, and I am updating everything, so that might help fix my problem as well.

---


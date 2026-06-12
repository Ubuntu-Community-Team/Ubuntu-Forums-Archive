---
title: "please help!!!!"
date: 2010-01-21
forum: General Help
---

### Post by mandakay on 2010-01-21
hiya am new 2 this pls cud sum 1 help me i have a web book ubuntu and i deleted my user name n password as i were guna sell it bt wen i turned it bac on it still asks 4 then,av tryed rebooting it n i got as far as-drop to root shell prompt and now sez -give root password for maintenace(or typeControl-D to continue) bt i cant type anyfin!! pls help as i wud like 2 use my web book again. fanx mands :confused:

---

### Post by llawwehttam on 2010-01-21
If you have deleted the only user and the root is not unlocked then you will probably have to re-install. I thought there was a warning when you remove the last working user account.

---

### Post by mandakay on 2010-01-21
ok fanx sorry 2 bother u!

---

### Post by pyedog on 2010-01-21
I don't know the answer to this problem myself but I'm sure reinstalling Ubuntu isn't the easiest, and certainly not the only, option.

Can something not be done using a Live-CD without a reinstall?

---

### Post by Mickser_52 on 2010-01-21
Sorry don't understand text-speak. Is it allowed in forums. Maybe you could provide a translation Matthew:o

---

### Post by Simian Man on 2010-01-21
You can unlock the root account, and/or create users by booting into single user mode.  There are instructions on how to do this [here]("http://www.debuntu.org/recover-root-password-single-user-mode-and-grub").

BTW your posts are almost impossible to read.

---

### Post by JiuJitsu500 on 2010-01-21
Yeah... grammar is something to take into consideration when talking with/to others you do not know, even through text :) But no judgement....

Follow those instructions above to unlock Root, and create a new user once you're in... System > Admin > Users and Groups :)

I could have misunderstod this whole post though :D

---

### Post by Simian Man on 2010-01-21
> **JiuJitsu500 said:**
> Follow those instructions above to unlock Root, and create a new user once you're in... System > Admin > Users and Groups :)

I could have misunderstod this whole post though :D

Actually, you'd want to add yourself as user and reset your password from the command line.  Then you won't have to login to the GUI as root (if Ubuntu even allows that):

```
# useradd -m -G users,audio,lp,optical,storage,video,wheel,power -s /bin/bash username
# passwd username

```

You can unlock the root password like the instructions in the link I posted to avoid this kind of thing in the future, but adding yourself back is the important thing.

---

### Post by mandakay on 2010-01-21
sorry for useing text speak i will try to write propley thank you so much- i will try this later, thank you manda

---

### Post by JiuJitsu500 on 2010-01-21
That's why you have an Ubuntu drip and I only have 5 cups :) would the GUI not work then if you could get root unlocked and to the desktop?

---

### Post by teward on 2010-01-21
Unlocking root doesn't necessarily allow you to use a GUI login.  The laptops I service use 9.04, and I had to manually configure the GUI to allow for root login through it.  Normally, root can't login through GUI, only through CLI.

---


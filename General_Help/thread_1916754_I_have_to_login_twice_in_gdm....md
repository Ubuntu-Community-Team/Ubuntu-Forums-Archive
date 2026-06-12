---
title: "I have to login twice in gdm..."
date: 2012-01-28
forum: General Help
---

### Post by samepate on 2012-01-28
Hello,

(sorry if the question has already been asked, I haven't found any answer yet...).

I am using Ubuntu 11.10 64 bit on my PC, and I have a problem in gdm, it seems to be related with my graphic card (nvidia) because when I type my password, I have strange dots flashing at the top left of the screen and the login fails. It asks me the password again and then it works fine. Sometimes (not often), it works the first time.

I have tried to reinstall gdm (and I put lightgdm when the installation process asks me to choose between gdm and lightgdm) but nothing changes.

Do you have any idea how I could fix this problem?

Thanks in advance!

---

### Post by cbowman57 on 2012-01-28
Have you already run Additional Drivers to see if they offer a newer & possibly better driver?

I know I used to have a similar problem when the installation process would install version 173 which my card didn't care for.  Updating to a newer version worked for me when it occurred.

---

### Post by samepate on 2012-01-29
Thanks for the reply. I have tried to reinstall the package nvidia-current (which installs the latest driver for my Geforce GT220 : version 290.10) but it doesn't change anything. Should I install a previous driver?

The thing is I don't understand why the first login sometimes fails and the second ALWAYS works...

---

### Post by cbowman57 on 2012-01-29
I would try 3 things.
purge lightdm (apt-get purge)
purge & reinstall gdm
try a different vid driver

One other simple thing to try, before my other guesses is from grub menu append nomodeset to the kernel commandline.

---

### Post by samepate on 2012-01-29
Thanks again, I think you have found a workaround.

I have tried to append nomodeset to the kernel commandline in grub menu but it didn't change anything. Then I have purged lightdm, then purged gdm and reinstalled it and now it starts with gdm and works fine. I will try to reinstall lightdm later but for the moment it doesn't look stable to me. I don't want to change my video driver just for lightdm, because everything else works fine.

Thanks again!

---

### Post by cbowman57 on 2012-01-29
Glad you found something that works.

Pretty sure lightdm is installed by default on 11.10 & 12.04 but it was an add-on for 11.04.
gdm works great & there are better tools to customize it than there are for lightdm right now, if you're into that.

---


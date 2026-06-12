---
title: "Lost password"
date: 2010-04-16
forum: General Help
---

### Post by helpcomm on 2010-04-16
I want b able to recover or reset the password that i lost. I have ubunto installed with windows vista. I used the following link for guidance:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
I tried recovery mode in grub it always asks me the same thing :
"Give root password for maintenance". I also tried to edit and boot the kernel unfortunately it did not work. So i never have a prompt, it still asks me for the password.

Any suggestions?

---

### Post by KeyserSoze93 on 2010-04-16
Put in an Ubuntu CD, and boot into the live desktop.

Open a terminal, and type:

```

sudo su -

```

On the Live CD desktop, you should see an icon for your local hard disk. See where it's mounted (like /media/DISK.)

Then, type:

```

chroot /media/DISK

```

Now you should be able to type

```

passwd

```

And change the root password of your installed system. One root's password is set, you can log in as root, and change your user password if you need to.

---

### Post by aysiu on 2010-04-16
> **helpcomm said:**
> I want b able to recover or reset the password that i lost. I have ubunto installed with windows vista. I used the following link for guidance:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
I tried recovery mode in grub it always asks me the same thing :
"Give root password for maintenance". I also tried to edit and boot the kernel unfortunately it did not work. So i never have a prompt, it still asks me for the password.

Any suggestions?
Scroll down to the YouTube video at the bottom of the tutorial.

In the future, don't set a root password. That way you won't be prompted for a password when you boot into recovery mode.

---


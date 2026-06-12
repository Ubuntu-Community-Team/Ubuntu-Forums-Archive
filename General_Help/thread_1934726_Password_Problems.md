---
title: "Password Problems"
date: 2012-03-02
forum: General Help
---

### Post by CTWilkinson on 2012-03-02
Hello all, im new to ubuntu and would like some assistance,
I said my user to have no password(I now know this was a bad idea). I'm now trying to give myself a password but I can't however I do still have a root password I believe, anyone able to help me change my user's password? I've tried holding down shift on reboot and going to the root/shell area.

thanks for any help

---

### Post by winh8r on 2012-03-02
Keep tapping the shift key as you start the machine.

You will enter the Grub Menu

use the arrow keys on the keyboard to

select the Linux Kernel nearest the top of the list with the words (recovery mode) beside it and hit enter

At the blue screen, navigate down to the "drop to root shell prompt" option

hit enter 

you are now running as root

enter the following

```
sudo passwd CTWilkinson
```

or whatever your username on the machine is

you will be asked to type in a new password

and then asked to type it in again to confirm

you will then receive confirmation that your password has been changed successfully

make sure you note down your password somewhere safe if you are likely to forget it.

Hope this helps you

---

### Post by Acker2012 on 2012-03-02
Sorry CTW, no help from me. I have a similar problem.
In terminal I can execute sudo commands and use my user password,
but can't give myself super user/root privilege.
I answer su with my user password and get authentication failure.
Can anyone help to get me access to my own machine?

Thanks

Acker

---

### Post by Acker2012 on 2012-03-02
Hi winh8r,
I just did that and got the ~# prompt and it spat me out.
Said Authentication Token Manipulation Error - password unchanged.

And indeed I'm back and tried and it is not changed.

Thanks for any help in this.

Acker

---

### Post by winh8r on 2012-03-02
You might need to use this command first before you can change the password:

```
sudo mount -n -o remount,rw /
```

this is because the filesystem is mounted as read-only and needs to be writable.

---

### Post by Acker2012 on 2012-03-02
Thanks my friend. Did that at the root prompt after shift key startup/grub selection etc.
And it changed my password and kept me at # prompt.
Then restarted, come to my user password, enter my new one and all's good,
back at the desktop.
Open a terminal and execute su at $ prompt and enter new password and get
Authentication Failure.
?????
Keyed in sudo mount -n etc, what you said, entered my password for sudo and back to $prompt.
Try su again and password again, still Authentication Failure.

Any ideas?

Thanks
Acker

---

### Post by winh8r on 2012-03-03
You only need to use the 

```
sudo
```

command to gain elevated privileges.


Have a read through this document for more info:

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

hope this helps you.

---

### Post by Acker2012 on 2012-03-04
Thank you for that. Enlightening.
I was able to do what I wanted without being in a root shell, but instead
extended privileges to myself and it worked.
That link you gave is well worth keeping in mind.
Thanks again.

Acker

---


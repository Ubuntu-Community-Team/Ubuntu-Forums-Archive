---
title: "Can't Enter @ Symbol in Password"
date: 2010-10-30
forum: General Help
---

### Post by pat_pfw_23 on 2010-10-30
After upgrading from 10.04 to 10.10, my laptop wouldn't boot into the GUI. I followed some steps that someone had posted at was able to get X back and working. Now, my laptop lost power without being shut down. I let it fix my disks, and I'm now back in the command line and can't get X working. Here's the weird thing...in the command line, I can enter my username ok, but it won't accept my password. I've figured out that it is the @ symbol in my password that messes things up. (I figured this out because when I typed something in the username, like "test" and then hit the @ key, it erases "test". I imagine it does the same thing and erases my password.) Does anyone have any ideas?

---

### Post by sisco311 on 2010-10-30
To get an @ symbol type u40 while holding down Ctrl+Shift. Or boot into recovery mode and reset your password.

[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

### Post by pat_pfw_23 on 2010-10-30
Thanks for the reply!

I tried using Unicode, and I couldn't get it to work. 

I've searched around on how to reset your password and it seems they all tell you to select the "root" option in recovery mode. They are immediately taken to a shell, but when I do it, it asks "give root password for maintenance", taking me back to the problem. Is that how you reset your password?

If it helps in any way, I've also tried an external keyboard, and I've tried switching the terminal to tty2, 3, etc.

---

### Post by sisco311 on 2010-10-30
Well, yes, if you have a root password, in single user mode you are prompted for it.

To start a root shell without being prompted for a password at the grub menu highlight the recovery mode option, press e for edit, replace the **ro single** options with **rw init=/bin/bash** from the end of the **linux** line and press Ctrl+x to boot.

Before reseting the password you may have to remount /:
```
mount -o remount,rw /
```

If the reboot command doesn't work, press Ctrl+Alt+Del.

---

### Post by pat_pfw_23 on 2010-10-30
Ok, I'm now in the root shell, but when I do "passwd patrick" (my username is patrick) it tells me I have an "authentication token manipulation error". I tried remounting and Ctrl+Alt+Del, too. According to [here]("http://mohammednv.wordpress.com/2008/01/08/authentication-token-manipulation-error-when-changing-user-passwords-in-linux/") it says I may have a problem with my username not being in /etc/shadow. I used vi, and it couldn't find any file.

Anymore ideas? Thanks!

---

### Post by sisco311 on 2010-10-30
Boot a Live CD, mount the root partition and edit the <mount/point>/etc/shadow file. The hash for a blank password is **00as1wm0AZG56**. So edit your user's entry to look like this:
```
patrick:**00as1wm0AZG56**:14900:0:99999:7:::
```

For details check out the youtube video from the psychocats tutorial.

---

### Post by pat_pfw_23 on 2010-10-30
Ok, thanks! I'll give it a try...I have to download the Live CD. I'll let you know how it goes. Thanks again for all of your help!

---

### Post by pat_pfw_23 on 2010-10-30
Thanks, I got my password successfully changed! I ended up having to go back to recovery mode and follow [this thread]("http://ubuntuforums.org/showthread.php?t=1145828") to make myself a sudo user because after I changed my password, it wasn't allowing me to use an sudo privileges. I still can't get X to start up, but I think I'm going to give up and just do a fresh install. 

Thanks for all your help!

---

### Post by WanderingAlbatross on 2011-10-18
You should mark this as solved, since the initial problem was solved, and it provides some useful details.

---

### Post by sisco311 on 2011-10-18
> **WanderingAlbatross said:**
> You should mark this as solved, since the initial problem was solved, and it provides some useful details.

Done & thread closed for necrobumping. :evil:

---


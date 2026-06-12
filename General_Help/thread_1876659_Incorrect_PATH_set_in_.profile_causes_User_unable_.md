---
title: "Incorrect PATH set in .profile causes User unable to login"
date: 2011-11-06
forum: General Help
---

### Post by MrJay on 2011-11-06
I am a new user to Linux though I have used Unix in many years ago.

While under the supervision of an experienced Linux user, I was told to edit the .profile file in my home directory to add environment variables for my development environment.

Unfortunately, they didn't tell me until afterward that I needed to add $PATH at the end of the PATH variable line.

I think because of that I could not use the ls, cd, tar, etc commands. So i restarted my computer thinking that could help.

Now I cannot access my admin account.

So is there a way to get my guest account to access that file to make the correction or should i just reinstall Linux?

---

### Post by wojox on 2011-11-06
Reboot, hold down the left shift key, choose recovery mode and drop to a root shell. You will have to edit the file with nano or vi.

---

### Post by MrJay on 2011-11-06
Cool, thanks

---

### Post by MrJay on 2011-11-06
Unfortunately, since my home directory is encrypted, when I run ecryptfs-mount-private to mount the home directory, it will not let me because "Encrypted private directory is not setup properly"

So I assume there is no way to resolve this so I can correct the .profile file

---

### Post by llamabr on 2011-11-06
> **MrJay said:**
> Unfortunately, since my home directory is encrypted, when I run ecryptfs-mount-private to mount the home directory, it will not let me because "Encrypted private directory is not setup properly"

So I assume there is no way to resolve this so I can correct the .profile file

I'm not too sure about that error, but if you cant do it from a secure shell, if you know your password, you should be able to mount the partition using a livecd which you can then use to edit your .profile.

---

### Post by MrJay on 2011-11-08
> **llamabr said:**
> I'm not too sure about that error, but if you cant do it from a secure shell, if you know your password, you should be able to mount the partition using a livecd which you can then use to edit your .profile.

Unfortunately, I couldn't get to the home directory because I had opted to encrypt it. Since i had used the Alternate version so I could get the option to encrypt the whole drive, I'm not sure if that could cause the problem.

Anyway, I wind up reinstalling from scratch. Since I didn't have anything moved to my Linux machine yet, it was the fastest choice for me. Because I didn't have a live CD to use and my boss wanted me to get my workspace up and running as soon as possible.

Thanks for all the feedback and help.

---

### Post by MrJay on 2011-11-10
Hey folks, I'm back.

I did a second installation and that worked out better. Until this morning, the same problem occurs cannot login as the user from the login screen.

So I dropped to a root shell under the recovery mode. Went to .profile under the home directory for the user. I can open the .profile file in nano, but it had read-only permissions.

I tried 'chmod 777 .profile' but the permission is still read-only.

I'm not even sure changing the .profile file will work. But I need to use my work laptop.

---

### Post by MrJay on 2011-11-11
Since while I am in recovery mode, the file system is in read-only mode, I searched for related problems.

I followed the directions on [this thread]("http://ubuntuforums.org/showthread.php?t=1870817%3Cbr%20/%3E")

Unfortunately, executing the following doesn't change anything:```
# mount -o rw,remount /
```And I cannot use ```
useradd newuser
``` to create a new user.


Since the file-system is read only I can't change anything.

---


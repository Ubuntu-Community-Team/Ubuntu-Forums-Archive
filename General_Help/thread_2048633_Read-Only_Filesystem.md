---
title: "Read-Only Filesystem"
date: 2012-08-27
forum: General Help
---

### Post by corn89 on 2012-08-27
It has been awhile since i last posted to this community, but I've recently decided to take it up again.

I've got a problem that I would like to gain some insight on.

After much Googling, I was unable to find anything, so now here i am.

I am trying to edit the xorg.conf file in order to set the refresh rate because the monitor is telling me that it is set too high. I am able to get to the terminal in the recovery mode, but when I do, I am told that the filesystem is read only. If I can edit that file, then I can get back into the GUI.

TL;DR, I need to write to the filesystem while in the recovery mode.

---

### Post by black veils on 2012-08-27
in the recovery mode menu, there is another item about network and mounting, go there first to mount with read/write permissions.

alternatively you could just enter the following command where you were trying before  ```
mount -o remount,rw / 
```

---

### Post by corn89 on 2012-08-27
Thanks, I will give it a try.

---

### Post by corn89 on 2012-08-28
Ok, so it turns out that I was trying to edit xorg.conf by typing
"sudo nano /etc/X11/xorg.conf"

This was trying to create a new text file rather than edit the existing one because it was unable to find the file.

Once I realised this, I browsed to the directory and typed "sudo nano xorg.conf" into the terminal while I was in the correct folder.

I was only able to edit xorg.conf after i mounted the filesystem. Because of this, the information that was posted earlier was helpful.

Once I was able to edit xorg.conf, I changed both the HorizSync and VertRefresh so that the maximum allowed refresh rate was 75.

After this, I was able to get to the login screen, but I was unable to login. I would enter the password and press login. the screen would then turn black, and return me to the login screen again shortly after.

I was able to fix this by logging into the guest account. I logged in to the guest account and created a new profile. I then deleted the account that couldn't login, but kept the files for the account. I then recreated the account with the same account name.

Once I did this, I was able to login, but I was unable to use sudo in the terminal. I fixed this by adding the account to the sudoer list from the recovery console since it was the only way to get root access.

---

### Post by black veils on 2012-08-28
thats some crazy stuff. so you did this because you wanted to change refresh rate? you can mark the thread as solved by using** thread tools** drop-down menu from just above the thread.

---

### Post by corn89 on 2012-08-28
Yeah, for some reason, the refresh rate was being set too high by default, so in order to use any monitor while using the GUI, I had to force it to be set to anything below 75 hz.

I've set it to solved.

---


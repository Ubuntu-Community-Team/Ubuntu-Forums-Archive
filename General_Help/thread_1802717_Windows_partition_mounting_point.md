---
title: "Windows partition mounting point"
date: 2011-07-12
forum: General Help
---

### Post by NikitaUtiu on 2011-07-12
Is there any way to specify the mounting point of the windows partition(/dev/sda2 in this case) and make it mount on startup?

Thanks in advance, NikitaUtiu. :)

---

### Post by tredegar on 2011-07-12
First, make a mountpoint
```
sudo mkdir /mnt/windows
```
Add a new line to /etc/fstab like this one
```
/dev/sda2 /mnt/windows  ntfs-3g  defaults  0 0
```
Just this once (because fstab will not be read until the *next* boot)
Make it mount
```
sudo mount -a
```

---

### Post by ~!geek!~ on 2011-07-12
I don't use command line to solve this problem. Sometimes things messes up when its about  storage devices. Instead I like to use a software called storagedevicemanager or something like that. 
You may install it from the repository using command:
> sudo apt-get install pysdm
After installing it, start it as root user:
> sudo pysdm
It will open a gui window. Configure from there. Its intuitive enough.

---

### Post by NikitaUtiu on 2011-07-13
Well I added /dev/sda2 to the fstab and everything works as intended. Thank you for your help! :P

---

### Post by Mark Phelps on 2011-07-13
Just a word of friendly advice ...

If the Windows OS you're mounting is Win7, take care to NOT make any filesystem changes from inside Ubuntu.

While that might not cause any problems, Win7 is very fragile about changes being made from outside -- and has been know to become corrupted.  And, when it does, it refuses to boot after that.

So, you be safest if you mounted your Win7 OS partition read-only.

---


---
title: "Mount Directory To RAM?"
date: 2010-06-07
forum: General Help
---

### Post by NightwishFan on 2010-06-07
Is there a way I can temporarily mount a directory read-only to RAM? I read about creating a tmpfs to /dev/ram0 and mounting the folder there, though the tutorial seemed to have extra steps such as editing /etc/fstab, which I do not need to do. Can anyone outline a way to do this easily?

---

### Post by jocko on 2010-06-07
Try this command:
```
sudo mount /dev/ram0 -t tmpfs [COLOR=Blue]/path/to/dir[/COLOR]
```

---

### Post by NightwishFan on 2010-06-07
How do I access it?

---

### Post by jocko on 2010-06-07
> **NightwishFan said:**
> How do I access it?
?

---

### Post by NightwishFan on 2010-06-07
Ok, nvm I see. My mistake. I have to just copy the folder to the new tmpfs at every mount. No problem.

No nvm it did not work, I will figure this out.

---

### Post by jocko on 2010-06-07
> **NightwishFan said:**
> Ok, nvm I see. My mistake. I have to just copy the folder to the new tmpfs at every mount. No problem.

No nvm it did not work, I will figure this out.
What did not work?

---

### Post by NightwishFan on 2010-06-07
No I got it, thanks! I did:
```
sudo mount /dev/ram0 -t tmpfs /media/ramfs/
```

Than copied the folder I wanted to there. Reason I am doing this is I want the read speed of RAM on a particular directory.

Edit: Sorry for being a bit confusing, I actually had to leave so I was trying to figure this out really quick.

---

### Post by jocko on 2010-06-07
An even easier way would be to use the already existing ramdisk (/dev/shm). Just copy the folder there (but remember that any change you make to files in the ramdisk will be lost when you reboot or unmount the ramdisk).

---

### Post by NightwishFan on 2010-06-07
Thanks thats what I was looking for.

Edit, nvm, is it just a directory?

Editedit: Yup, got it. Thank you for all the help.

---


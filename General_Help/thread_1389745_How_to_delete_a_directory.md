---
title: "How to delete a directory"
date: 2010-01-24
forum: General Help
---

### Post by Mr Nemo on 2010-01-24
I'm trying to delete the mythtv directory in my /Home directory. I tried rm and rmdir with sudo but that didn't work and I got an error message that said the directory wasn't empty. Then I tried 'sudo -Rf rmdir mythtv', but I keep getting an invalid option error. -R was for recursive right? Is there someway to remove this directory?

---

### Post by drs305 on 2010-01-24
> **Mr Nemo said:**
> I'm trying to delete the mythtv directory in my /Home directory. I tried rm and rmdir with sudo but that didn't work and I got an error message that said the directory wasn't empty. Then I tried 'sudo -Rf rmdir mythtv', but I keep getting an invalid option error. -R was for recursive right? Is there someway to remove this directory?

Use "rm -R /path/directory", combined with sudo if you absolutely must. The "f" option may also be necessary for certain operations. Read about "rm" in the man pages (man rm).

Be very carefull if you are using sudo with this command, as you can wipe out your entire system with a single typo.

---

### Post by Mr Nemo on 2010-01-24
I still get the invalid option error with that.

---

### Post by drs305 on 2010-01-24
> **Mr Nemo said:**
> I still get the invalid option error with that.

Using nautilus as root may be a safer way, since you can see the directory and are less prone to errors:
```
gksu nautilus
```
Highlight the folder and use SHIFT-DEL to remove the folder. If you don't use SHIFT-DEL it will end up in root trash and will continue to take up space until you empty root's trash bin. The downside of SHIFT-DEL is that once something is deleted, you can't get it back.

---

### Post by Mr Nemo on 2010-01-24
Alright that worked, thanks a lot. Any reason I couldn't delete it through the terminal?

---

### Post by drs305 on 2010-01-24
I saw in your first post you had the switches before the command, which would produce an error as well. 

Added:
*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Mr Nemo on 2010-01-24
Oh I see what you mean about the options. Thanks again.

---

### Post by kjohri on 2010-01-25
> sudo -Rf rmdir mythtv

I think the command should have been 

```
sudo rm -fr mythtv
```

Invalid option error would have been because you passed option "-Rf" to sudo and not to rm.

---


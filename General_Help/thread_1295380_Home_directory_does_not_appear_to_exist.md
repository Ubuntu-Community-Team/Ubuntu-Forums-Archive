---
title: "Home directory does not appear to exist"
date: 2009-10-19
forum: General Help
---

### Post by pgar23 on 2009-10-19
Hi,
     To get straight to the problem: I have been following a tutorial from makerech.com/.../... About changing the splash screen at bootup. The tutorial suggested downloading SPLASHY and a few other programs. After downloading splashy, when I would open the repos it would report an error of broken dependencies for the program. So I removed it from my system. Then, I downloaded a GUI-based program for backing up my system called Back-in-time. I tried changing all of my directories to be readable, writable, and executable to everyone since I am the only person using my laptop. 

Now, when I boot my system, I receive an error stating:
```

your home directory is listed as: '/home/python' but it does not appear to exist. Do you want to login with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.
```I have tried loggin in with the root directory. It takes me to the login screen and after entering my  Username and my  password the computer stalls after the login screen. It is just a blank black screen.

Before the comp started malfunctioning, Made a snapshot backup, but I wouldn't know where it was saved nor how to restore the backup.

Any advice or suggestions??

---

### Post by pgar23 on 2009-10-19
Bump.   Sorry to bump early but I am unable to use my laptop, I am at a friends house using his comp and he will be going to sleep soon. I would like to get my machine back up and running. Any help is appreciated. Thanks community.

---

### Post by pgar23 on 2009-10-19
The backup was name 2009-10-19 or 2009-19-10..either one. But how do I get my computer back to a working manner?

---

### Post by mechro on 2009-10-19
I've not read it all but this thread is marked as solved...

[http://ubuntuforums.org/showthread.php?t=950733](http://ubuntuforums.org/showthread.php?t=950733)


Hope it helps. Good Luck.

---

### Post by renkinjutsu on 2009-10-19
Is your username python? If it's not, then all you have to do is change the /home directory back to your original.. to do that:

restart the computer, to get to the grub menu (you may have to press ESC)

at the grub menu, select recovery and boot into that.

There should be a menu that allows you to login as root

when you're logged in, do this ```
usermod -d /home/*user* _*user*_
# replace "user" with your actual username
``` That should set your home directory back to what it's supposed to be, now you can reboot ```
reboot
```

---

### Post by pgar23 on 2009-10-19
yes my username is python Not jus my username bt my actual name. LOL

---

### Post by renkinjutsu on 2009-10-19
hmm.. check if anything is even in the /home directory

log in as root (instructions above) and ```
ls -la
``` to see all folders and permissions... If you find something that might be your old home folder, then you're in luck

---

### Post by pgar23 on 2009-10-19
Succesfully solved my problem by following [ THIS THREAD ]("http://ubuntuforums.org/showthread.php?t=524986")

Thanks for the help guys!

---


---
title: "Mounting Location Difficulties"
date: 2009-10-08
forum: General Help
---

### Post by johnny_archer on 2009-10-08
I have a laptop that is dualbooted vista and Ubuntu Jaunty Jackalope 9.0.4 and I was normally able to access the windows partition of my hard drive from ubuntu. I somehow ended up accidentally changing the mountlocation of the windows partition somewhere in settings and I cannot figure out what i did. All I remember is trying to figure out how to permanently mount the windows partition and typing in something into a menu and closing it, being used to windows and not remembering that ubuntu saves automatically when it closes. help?

---

### Post by jeremyswalker on 2009-10-08
The default mount points are defined in /etc/fstab. Check there to see if it looks as it should.

> ...ubuntu saves automatically when it closes.
I'm not sure what exactly you mean by this.

---

### Post by alphaniner on 2009-10-08
I think he means that with Windows, if you close a window or dialog without clicking OK or Apply, the changes are unsaved.  Whereas in Ubuntu, the choices are often Revert or Close.  And if you click Close, or close the window with the **X** in the title bar, the changes are saved.

---

### Post by johnny_archer on 2009-10-08
When you close a preference window in ubuntu it automatically saves what you changed. In windows there is an usually an "apply" option and if you close it nothing happens. 

Thanks, but do you know what the default mount point should be and how to change it if it is wrong? I am new to this if you can help it would be appreciated.

---

### Post by jeremyswalker on 2009-10-08
After re-reading your problem, I'm guessing you never got it to be permanently mounted? If this is the case, it won't be in fstab anyway.

If you want it to be mounted automatically, add an entry for it in /etc/fstab.

For example, if your windows partition is /dev/sda1 and you want to mount it at /home/<user>/Windows, you would add the following to /etc/fstab:
```
/dev/sda1   /home/<user>/Windows   ntfs   defaults   0   0
```

You would have to replace /dev/sda1 with the correct partition for your Windows installation. You would replace /home/<user>/Windows with your desired mount location. Afterwards, it should be mounted everytime the system is started.

---

### Post by johnny_archer on 2009-10-08
again newbie question, how do you edit the fstab file through terminal?

---

### Post by jeremyswalker on 2009-10-08
Either:
```
sudo gedit /etc/fstab
```

Or:
```
sudo nano -w /etc/fstab
```

---

### Post by jeremyswalker on 2009-10-08
I also just stumbled across this post which may help you. I have no experience with this method, though.

[HowTo: Automount NTFS Drives]("http://ubuntuforums.org/showthread.php?t=785263")

---

### Post by johnny_archer on 2009-10-08
okay, so ive input the line to the fstab file now when i try to acces the windows partition it says im not privileged what should i do from here?

---

### Post by johnny_archer on 2009-10-08
wait nevermind i totally figured it out. thank you so much for your help.

---

### Post by jeremyswalker on 2009-10-08
Not a problem at all. I'm glad you figured it out. Congrats!

---


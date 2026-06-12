---
title: "Prompted for username and password at startup"
date: 2010-08-30
forum: General Help
---

### Post by mazzizo on 2010-08-30
Sorry for the misleading title, but, it's not for the typical username and password that I use to log into my computer. It's actually prompting me, upon startup/reboot to have me insert my name and password, in what appears to be the command prompt. I am still a noob with Ubuntu and Linux in general, so I have no idea what I did to make this happen. It's not terrible and zomg if it doesn't get fixed I'll die, but it is slightly inconvenient to have to "sudo /etc/init.d/gdm start" every time I reboot my computer. Anyone know what I have to do to fix this?

I would also like to apologize if this has been covered in another topic, but I could not find anything on it.

Thanks

---

### Post by oldos2er on 2010-08-30
Do you mean to say you're getting a text login? Did you ever have a working graphical login, and perhaps did something to change it?

---

### Post by mazzizo on 2010-08-30
> **oldos2er said:**
> Do you mean to say you're getting a text login? Did you ever have a working graphical login, and perhaps did something to change it?
Yes, I am getting a text login, and when I first installed Ubuntu it was working fine. I did change the background image for the login screen though. But at the moment, I cannot for the life of me remember what I did or used for that.

---

### Post by oldos2er on 2010-08-30
I don't use gdm (the graphical login thingy), but you might try ```
sudo dpkg-reconfigure gdm
``` to get it back to the default state.

---

### Post by mazzizo on 2010-08-31
> **oldos2er said:**
> I don't use gdm (the graphical login thingy), but you might try ```
sudo dpkg-reconfigure gdm
``` to get it back to the default state.
Gave that a try, did not work :( Thank you for the reply/efforts though

---

### Post by wojox on 2010-08-31
Try this 

Login

```
sudo dpkg-reconfigure xserver-xorg
```

Type your password

Follow the prompts....the defaults should get you up and running.

---

### Post by mazzizo on 2010-08-31
> **wojox said:**
> Try this 

Login

```
sudo dpkg-reconfigure xserver-xorg
```Type your password

Follow the prompts....the defaults should get you up and running.
Typed it in exactly how you have it here, after i put in my password, didnt prompt me for anything, just put me back to type in another command. no errors or anything. Also restarted to see if it had done anything, and nothing changed.

---


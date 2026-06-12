---
title: "Ubuntu 9.10 &quot;freezes&quot; at startup"
date: 2010-02-05
forum: General Help
---

### Post by shimawn on 2010-02-05
Hello everyone, my ubuntu starts up fine but it freezes before i can do anything. I have the "enter password for default keyring to unlock" message pop up at start up but my keyboard and mouse are unresponsive. The cursor in the message box blinks and the clock still works, but i can't do anything. 
I've had ubuntu for a while now and this has just started happening. Any help is much appreciated.

---

### Post by lidex on 2010-02-05
Boot into a live session (CD) and use nautilus to delete this file ```
~/.gnome2/keyrings/default.keyring
```, and ***ONLY*** this file, from your HDD. Or in a terminal: ```
rm ~/.gnome2/keyrings/default.keyring
```
If you get permission error:
```
sudo rm ~/.gnome2/keyrings/default.keyring
```

---

### Post by llawwehttam on 2010-02-05
As your post count is so low I guess your new so 'welcome to the forums'

The below method is correct.

> **lidex said:**
> Boot into a live session (CD) and use nautilus to delete this file ```
~/.gnome2/keyrings/default.keyring
```, and ***ONLY*** this file, from your HDD

Just to clarify ~/ means your home folder so 

~/ is the same as /home/yourusername/ .

Hope you manage to fix it.

---

### Post by NertSkull on 2010-02-05
This may or may not be of any use.  But for I've discovered that sometimes installing some of the upgrades (new headers) has caused issues with me.  So when I get to the grub menu, I choose an older version of the header (not recovery ones) and go back to the old ones and things work again.  Then I can do more troubleshooting.  

May not have anything to do with what your issue is though.

---


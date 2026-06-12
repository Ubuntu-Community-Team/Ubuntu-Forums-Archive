---
title: "How to get rid of &quot;keyring&quot; stuff?"
date: 2010-09-10
forum: General Help
---

### Post by MakOwner on 2010-09-10
How do I get rid of this keyring crap?

I have autologin set up on a laptop so that I boot up and I don't have to enter a password.  Why would I want to have to enter yet another password to just to connect to my wireless network?

I'd like to have the keyring junk go away and have the passphrase for the wireless network stored so at boot up the laptop connects without entering a series of passwords.  

This worked under the 9.x versions and has stopped working since the installation of 10.4

---

### Post by 3rdalbum on 2010-09-11
Auto login is a bad idea on portable computers.

You can change your keying password to blank for it to be automatically unlocked even with auto login.

Ubuntu 9.x were exactly the same in this regard.

---

### Post by gadolinio on 2010-09-11
I've had that kind of issue when opening Evolution: I had to type that keyring everytime it was launched. I read the following solution in these forums i think, and it worked. I had to go to /home/USERNAME/.gnome2/keyrings/, and delete the existing keyring files (actually moved them, just in case something went wrong). Hope this helps...

---

### Post by stinkeye on 2010-09-11
If you right click on network connections and edit your wireless connection
and tick a box in the bottom left **make available to all users**
you won't get the keyring prompt when connecting to a network.

---

### Post by MakOwner on 2010-09-11
> **stinkeye said:**
> If you right click on network connections and edit your wireless connection
and tick a box in the bottom left **make available to all users**
you won't get the keyring prompt when connecting to a network.

3rdalbum: I know, I'm ashamed.  But this laptop doesn't leave the docking station and if someone can fire it up without me there, I have much worse problems than a losing root on my laptop.

I have checked the "make available to all users" and we'll see if that works.  I thought it was already checked, but when I went to verify, sure enough, it wasn't.  Hopefully that fixes it!

---


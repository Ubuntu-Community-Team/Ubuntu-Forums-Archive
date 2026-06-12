---
title: "Logging as a root automatically"
date: 2011-10-04
forum: General Help
---

### Post by Claxton2 on 2011-10-04
I have customized Ubuntu to boot only in text mode (removed all GUI), but I do need to log in before using the terminal.

How do I log in as a root automatically and disable logging in prompt at start-up ?

thanks

---

### Post by CatKiller on 2011-10-04
Just don't.

Logging in as root at all is a seriously bad idea. Automatically logging in as root is off the scale.

---

### Post by snowpine on 2011-10-04
Welcome to the forums! I see that this is your first post. If you hang out on the forums for a while, you will learn that what you're asking is not recommended/supported.

A good place to start reading is the Sticky threads at the top of the Security sub-forum: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by collisionystm on 2011-10-04
> **Claxton2 said:**
> I have customized Ubuntu to boot only in text mode (removed all GUI), but I do need to log in before using the terminal.

How do I log in as a root automatically and disable logging in prompt at start-up ?

thanks

[http://tombuntu.com/index.php/2010/01/01/enable-automatic-login-in-ubuntu-9-10-server/](http://tombuntu.com/index.php/2010/01/01/enable-automatic-login-in-ubuntu-9-10-server/)

---

### Post by prodigy_ on 2011-10-04
> **collisionystm said:**
> [http://tombuntu.com/index.php/2010/01/01/enable-automatic-login-in-ubuntu-9-10-server/](http://tombuntu.com/index.php/2010/01/01/enable-automatic-login-in-ubuntu-9-10-server/)
This. You will also need to either re-enable root: ```
sudo passwd -u root
sudo passwd root
``` or edit /etc/sudoers and add **sudo -i** somewhere in your shell startup files.

However, at the risk of being Captain Obvious, I second the warnings of the above posters. The whole idea is wrong on so many levels... At the very least make sure this abomination isn't open to untrusted networks in any possible way.

---


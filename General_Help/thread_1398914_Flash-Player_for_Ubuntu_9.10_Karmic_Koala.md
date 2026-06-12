---
title: "Flash-Player for Ubuntu 9.10 Karmic Koala?"
date: 2010-02-05
forum: General Help
---

### Post by Akatsuki26 on 2010-02-05
I just don't understand how to install the flashplayer, so I can watch Youtube videos and play Flash games...

I am a COMPLETE beginner, so please go easy on me and try to understand...

One guy told me to write this code in the terminal:

"sudo apt-get install flashplugin-nonfree"

That's what I did, but then I got this as a response:

[sudo] password for "myname": (I entered it here)
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Can anyone help? How can I finally install it?

Thanks a lot!

---

### Post by Grenage on 2010-02-05
Don't double-post.

Did you have the package manager open at the time? If not, reboot and enter the command again.

---

### Post by Akatsuki26 on 2010-02-05
Thanks for the answer. Sorry, didn't know about the doule-post thing.

What do you mean by packet manager. The Synaptic Packet Manager?

Thanks.

---

### Post by Grenage on 2010-02-05
Bingo.  If you have that open, it will stop apt-get from working correctly - they both work off the same system.

---


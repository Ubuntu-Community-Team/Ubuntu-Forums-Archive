---
title: "In SERIOUS problem please HELP!"
date: 2010-04-17
forum: General Help
---

### Post by badnaam on 2010-04-17
I was trying to get my brand new xubuntu install on a Dell Latitutude get going with a kvm switch. I shut down the machine -> connected the kvm cable -> powered it back on and the keyboard/mouse work fine in the login screen, HOWEVER, I just can't get past the login screen, it keeps refreshing the screen even if my authentication is correct.

I unplugged the usb kvm cable, restarted but the problem does not go away.

I can't login to recovery mode (press esc during GRUB load), it doesn't offer any recovery options, goes straight to the login screen.

I have a project due Monday, I am so in trouble..please help!

---

### Post by itiswhatitis on 2010-04-17
Maybe log in then reconnect the KVM?

I had a USB KVM that was throwing weird inputs that I wasn't typing.  Made it very hard to enter my password.

---

### Post by camdude on 2010-04-19
Well...I have some bad news for you; it sounds like some system files in xubuntu got corrupted. Your best bet would be to reinstall xubuntu (but dont wipe the partition) unfortunately, its already Monday...

---

### Post by nexes128 on 2010-04-19
Can you try a live cd to copy your data off?
Also grub doesn't always come up first try, make sure your hitting Esc as soon as your bios screen disappears and try it a couple times

Edit: Almost forgot if you manage to get in with either the live cd or recovery take a look at /var/log/auth.log there will probably be some error message in there about pam

---


---
title: "Find package name for installed program?"
date: 2010-12-13
forum: General Help
---

### Post by scubscub on 2010-12-13
Hello, I have Openoffice 3 installed from outside the repositories and I want to roll back to 2.4 which is better integrated into Ubuntu.  (I suppose I've learned my lesson about that).  I understand I can uninstall with something like the following command:

sudo apt-get remove {package name}.

How do I find out what the "package name" is for the version of Openoffice I have installed?  Since it's not in the repositories, it doesn't show up in add/remove, etc.

???

---

### Post by dabl on 2010-12-13
```
sudo apt-cache policy openoffice.org
```

will show you the installed version number.  But I don't think that matters for your purposes.  What you need to do is

```
sudo apt-get remove --purge openoffice.org
```

That should rip it all out.  Then you can use synaptic to install it from the Ubuntu repos.

---

### Post by scubscub on 2010-12-13
Thanks for getting back so quick, dabl,

I tried the purge command and unfortunately got:

Package openoffice.org is not installed, so not removed

Then I tried the policy command and got this:

openoffice.org:
  Installed: (none)
  Candidate: 1:2.4.1-1ubuntu2.4
  Version table:
     1:2.4.1-1ubuntu2.4 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
     1:2.4.0-3ubuntu6 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages


Apparently it did not see the non-repository 3.0 in there.... but it's there...

---

### Post by Krytarik on 2010-12-14
Open "Synaptic" via "System -> Administration" and search for the packages there, better choose "Name and Description".

---

### Post by scubscub on 2010-12-14
Thank you, that did the trick -- as it turned out, the package name was openoffice.org3 .  And successfully removed.

---

### Post by idi0tf0wl on 2010-12-14
A method I've found to be extremely helpful for just this task is setting the Deskbar applet to one of my panels. In my case, it's in a hidden panel and is set to come up at a particular keystroke. Just the same, searching applications there will reveal an application's package name,and it has the added benefit of being a launcher!

Cheers!

---


---
title: "I think I did something wrong related to PATH ..."
date: 2009-10-23
forum: General Help
---

### Post by PewterHydra on 2009-10-23
I was [installing LaTex]("http://www.tug.org/texlive/quickinstall.html") (TeX Live, not that it probably matters) and the install script complained about permissions, so I ran it as root. 

Then I completed the following instructions (still as root): 

> Then, except on Windows, you must add the TeX Live binary directory to your PATH:
  PATH=/usr/local/texlive/2008/bin/i386-linux:$PATH
(Use the syntax for your shell, your own chosen directory, and your own system name instead of i386-linux.)

The default is to configure for A4 paper. To make the default be 8.5x11 letter-size paper, you can use the &#8216;o&#8217; command before i(nstalling), or run tlmgr paper letter after installation (and setting your PATH). 

After the second bit there (with the tlmgr) a bunch of stuff crashed. I rebooted Ubuntu and discovered that most of my applications can't access their profiles... Firefox, Pidgin, not even Bash. My default keyring doesn't prompt to be unlocked, and bunch of other stuff is behaving irregularly. 

PATH looks normal: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games


I'm not sure how to proceed.

---

### Post by PewterHydra on 2009-10-24
... apparently the only thing to do at this point is manually go through and reset the permissions on the relevant folders for everything that doesn't work. 

*sigh* 

Not my most brilliant day...

---


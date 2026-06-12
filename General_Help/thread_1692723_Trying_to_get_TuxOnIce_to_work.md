---
title: "Trying to get TuxOnIce to work"
date: 2011-02-21
forum: General Help
---

### Post by Miltnoid on 2011-02-21
Hey guys, I've been following the instructions at [http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-tuxonice-in-ubuntu.html) to download TuxOnIce.

However, I'm having some difficulties completing them.  It says "Add the following PPA to your sources list"
I don't know exactly what this means, but I guessed it meant go to Ubuntu Software Center, go to edit -> Software Sources, and add those two lines to the Other Software tab.

My next issue was the immediately next instructions.  I tried typing in "gp[FONT=monospace]g --k[/FONT]eyserver keyserver.ubuntu.com -recv DEC8FAAC" in terminal, but that just gives me the message "gpg: can't open `DEC8FAAC'"

The first time I did this, with root priveledges, btw, it gave me the output "gpg: directory `/root/.gnupg' created
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/root/.gnupg/secring.gpg' created
gpg: keyring `/root/.gnupg/pubring.gpg' created
gpg: can't open `DEC8FAAC'"

Anybody know what's going on here or have any suggestions?  Thanks!

---

### Post by gordintoronto on 2011-02-21
You're following instructions which are 18 months old. If you have a current Ubuntu, they don't apply.

Do you have issues with hibernating your computer? I'm not sure why a person would want to use hibernate instead of normal shutdown. OK ,it might save you a couple of dozen seconds. So what?

---

### Post by Miltnoid on 2011-02-22
It's a laptop, so the ability to hibernate is pretty useful for me.

sudo s2disk was working for a while, but recently stopped.

---


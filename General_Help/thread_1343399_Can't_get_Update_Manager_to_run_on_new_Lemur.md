---
title: "Can't get Update Manager to run on new Lemur"
date: 2009-12-01
forum: General Help
---

### Post by grikdog on 2009-12-01
Karmic 64 came pre-installed on my daughter's new laptop, a System76 Lemur Ultrathin.  It's weird, but I can't get an authorization dialog to come up.  That means Update Manager won't run to completion.  Just sits and spins its wheels.  The laptop is working fine in other respects, including wireless, although we did have to upgrade a Qwest modem to get wireless-N working.

I've looked at permissions and authorizations, and the principle (i.e., only) user seems to have admin privileges, but might as well not.  The account like a normal user account.  Any suggestions on how to proceed with debugging this issue?

I've been using Ubuntu for a few months, but still regard myself as a newbie in most respect.  Please help.

---

### Post by dcstar on 2009-12-01
> **grikdog said:**
> Karmic 64 came pre-installed on my daughter's new laptop, a System76 Lemur Ultrathin.  It's weird, but I can't get an authorization dialog to come up.  That means Update Manager won't run to completion.  Just sits and spins its wheels.  The laptop is working fine in other respects, including wireless, although we did have to upgrade a Qwest modem to get wireless-N working.

I've looked at permissions and authorizations, and the principle (i.e., only) user seems to have admin privileges, but might as well not.  The account like a normal user account.  Any suggestions on how to proceed with debugging this issue?

I've been using Ubuntu for a few months, but still regard myself as a newbie in most respect.  Please help.

Try launching the app in a terminal and note any messages.

---

### Post by grikdog on 2009-12-02
> **dcstar said:**
> Try launching the app in a terminal and note any messages.

That's interesting.

sudo chown -R tara:tara *
sudo: unable to resolve host tara-laptop
[sudo] Enter password:

This runs to completion.  So I tried

sudo /usr/bin/update-manager

which is now running correctly.

"tara-laptop" is the default name of the Lemur on the "network" which is nonexistent except for wireless.  Would having two laptops on the same wifi signal somehow create an unintentional network?

ADDITIONAL INFORMATION:

The problem seems to be gksu, which tries to launch the authorization dialog, fails to resolve the (default?) tara-laptop host, and bails.  I'm pretty sure the problem is that "tara-laptop" computer name.  How do I change or fix that?


Thanks for your help!

---

### Post by dcstar on 2009-12-02
> **grikdog said:**
> 
.........
The problem seems to be gksu, which tries to launch the authorization dialog, fails to resolve the (default?) tara-laptop host, and bails.  I'm pretty sure the problem is that "tara-laptop" computer name.  How do I change or fix that?


/etc/hostname
/etc/hosts

---

### Post by Paul Stone on 2009-12-03
Ahso!

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

### Post by grikdog on 2009-12-08
> **Paul Stone said:**
> Ahso!

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

And that, your excellent Dudeness, has SOLVED MY PROBLEM!!! Thanks!

I might add that Karmic Koala /etc/hosts file looks like it was written on a Macintosh (no line feeds) and contains only a message repeated once more about localhost.localdomain and stuff not working that requires network support.

I added TWO lines:

127.0.0.1 localhost
127.0.1.1 myhostname

---


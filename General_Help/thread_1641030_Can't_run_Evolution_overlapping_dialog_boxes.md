---
title: "Can't run Evolution: overlapping dialog boxes"
date: 2010-12-08
forum: General Help
---

### Post by Mander on 2010-12-08
I can't seem to run Evolution.  Whenever I try to open it, I get a box asking for the password for my email account as well as a box asking whether I want Evolution to be the default mail client.  The answer in either box is not acknowledged, and the only was I can figure out to close it is to "killall evolution".

I'm having a hard time searching for bug reports--nothing seems to come up with the terms that I have used.

How can I reset this?  I kind of want to try out the Contacts manager feature and the MS Exchange compatibility, but I use Thunderbird for my main email and I don't want Evolution to be the default.  

Incidentally I'm actually using Fedora 13 but I imagine most of the commands I might need are the same.

---

### Post by wojox on 2010-12-08
You all updated?

```
su -c 'yum update'
```

Try running evolution from the terminal and see if that tells you anything.

---

### Post by Mander on 2010-12-14
Well, this is what I got:

```

(evolution:2699): e-data-server-DEBUG: Loading categories from "/home/mander/.evolution/categories.xml"
(evolution:2699): e-data-server-DEBUG: Loaded 31 categories

(evolution:2699): e-utils-WARNING **: Something called e_alert_dialog_constructed() with a NULL parent window.  This is no longer legal, please fix it.
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'

```

I tried to follow the fix listed [here]("http://ubuntuforums.org/archive/index.php/t-866735.html") but it didn't quite work.  So I got fed up with it and just deleted the whole entry for the profile in the gconf-editor key.

After this I was able to un-check the box that makes it ask whether you want it to be the default client, and then I set up a dummy account.

---


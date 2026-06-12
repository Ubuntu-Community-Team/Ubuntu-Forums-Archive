---
title: "How to Lock Firefox 15 Preferences?"
date: 2012-09-17
forum: General Help
---

### Post by Azdour on 2012-09-17
Hi all

I need some help locking my Firefox 15 preferences.

From Firefox v3 up to v14 I have been able to lock the preferences without any problems ([http://kb.mozillazine.org/Locking_preferences](http://kb.mozillazine.org/Locking_preferences)), but Firefox 15 has me stumped...

Here's what I have done that used to work with Firefox v14:

[LIST]
[*]Firefox v15 lives in /usr/bin/firefox
[*]Placed my encoded mozilla.cfg in /usr/lib/firefox
[*]Created the local-settings.js file in /usr/lib/firefox/defaults/pref
[/LIST]

In local-settings.js I have:
```

pref("general.config.filename", "mozilla.cfg");

```

When I go to about:config and look up general.config.filename it does not exist. So for what ever reason it is not reading the local-settings.js file

---

### Post by ajgreeny on 2012-09-17
Just to see what happens I have just changed the permissions of the ~/.mozilla/firefox/profile.default/prefs.js file to read only in nautilus.  Any attempt to change preferences that I then tried was apparently accepted in the firefox Edit->Preferences menu dialog box, but on restarting FF all was back to the same as before; no changes were saved.

I did not try making changes in the about:config page, but I assume the same would happen.

You would simply need to change permissions back to read/write if you wanted to update FF or make any changes yourself, and it would be very easy to do that with a simple script, which you could double click to execute.

---

### Post by Azdour on 2012-09-17
Hi,

Thanks for the reply. 

I need to use mozilla.cfg so that it is enforced for all users on that machine. User accounts come and go and this was a far simplier way for me to admin the machine.

---

### Post by GeForce 9500GT on 2012-09-17
This is a interesting topic! Thanks for sharing!=D>

---


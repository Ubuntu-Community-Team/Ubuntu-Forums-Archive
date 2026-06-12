---
title: "problems opening firefox"
date: 2009-11-01
forum: General Help
---

### Post by M0GEJ on 2009-11-01
I have just updated to karmic and can now only get onto firefox if I type ~/firefox/firefox   into the terminal.  Any ideas of how I can sort this?

cheers

---

### Post by lovinglinux on 2009-11-01
If you can launch Firefox with ~/firefox/firefox is because the is a Firefox manually installed on your home directory, which I do not recommend. Look in your home and delete the Firefox folder residing there.

Also, try to launch Firefox Profile Manager and create a new clean profile. First close any opened Firefox, then run this:

```
firefox -P
```

This will start the Profile Manager, from where you can create and launch a new clean profile. That should be enough to fix it.

If that doesn't work, then go to Synaptic, search for Firefox, select the packages **firefox** and **firefox-3.5** and mark them for re-installation. Then, click apply.

---

### Post by M0GEJ on 2009-11-01
I tried all that and now can't open firefox at all.  The icon is still there though :?

---

### Post by lovinglinux on 2009-11-01
> **M0GEJ said:**
> I tried all that and now can't open firefox at all.  The icon is still there though :?

Try to launch with this command:

```
firefox-3.5
```

---

### Post by M0GEJ on 2009-11-01
That works:). Just need to work on getting the icon thing sorted now:)

---

### Post by lovinglinux on 2009-11-01
> **M0GEJ said:**
> That works:). Just need to work on getting the icon thing sorted now:)

Edit the launcher and make sure it's command is **firefox %u**. It is probably pointing to the old home installation right now.

---

### Post by M0GEJ on 2009-11-01
I assume I am doing something wrong as I try that and get:
Failed to execute child process "firefox" (No such file or directory).

---

### Post by lovinglinux on 2009-11-01
> **M0GEJ said:**
> I assume I am doing something wrong as I try that and get:
Failed to execute child process "firefox" (No such file or directory).

Try to change it to **firefox-3.5** instead.

---

### Post by M0GEJ on 2009-11-01
Perfect! All sorted now.  Thanks for all your patience:)

---

### Post by lovinglinux on 2009-11-01
> **M0GEJ said:**
> Perfect! All sorted now.  Thanks for all your patience:)

np

---


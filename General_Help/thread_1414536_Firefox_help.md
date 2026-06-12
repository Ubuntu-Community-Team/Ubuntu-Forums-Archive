---
title: "Firefox help"
date: 2010-02-23
forum: General Help
---

### Post by charlton2142 on 2010-02-23
Hey Im having some trouble with firefox. I recently reformatted my computer and Im just putting everything back together again. Im currently running ubuntu 9.10 and firefox 3.6. As of right now its not remembering any of my passwords or usernames I went into the preferences and the box is ticked to remember password and there are no exceptions. This is somewhat of a problem because when I log into my megavideo account it will not leave me logged in so that I could watch the movie. 

Please help me resolve this problem thank you 

josh

---

### Post by eriktheblu on 2010-02-23
Are you accepting cookies?

---

### Post by charlton2142 on 2010-02-23
yeah I seem to be

---

### Post by lovinglinux on 2010-02-23
Password storage is not related with staying logged in. This is a cookie job.

To fix the password problem install [Password Exporter](https://addons.mozilla.org/en-US/firefox/addon/2848) and export your current passwords if you have any.

Then make a backup of the folder ~/.mozilla/firefox. It is a hidden folder under your home directory. Then close Firefox, open that folder and locate your profile folder inside it (probably a folder ending with .default). Delete the files **key3.db** and **signons.sqlite** (this will completely reset your stored passwords). Start Firefox and test if it stores the password now. If yes, then import the passwords from the exported file with Password Exporter. 

If you can't stay logged in, then try to delete the file cookies.sqlite (close firefox first).

---

### Post by charlton2142 on 2010-03-08
Thanks for all your help it was actually one of my addons Im not sure which one so I just took off some random ones until it started working

---


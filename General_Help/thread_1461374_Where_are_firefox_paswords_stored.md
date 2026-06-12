---
title: "Where are firefox paswords stored?"
date: 2010-04-24
forum: General Help
---

### Post by hakermania on 2010-04-24
hi, I would like to ask where are the firefox's passwords stored. In which directory/file.
I use UBUNTU 9.10
thank you

---

### Post by lidex on 2010-04-24
You can access them from firefox "Edit>Preferences>Security"
Click on the "Saved Passwords" button in the popup box click "Show Passwords" to view. The actual file is in your Firefox profile directory- either 'key3.db' or 'permissions.sqlite'

---

### Post by lovinglinux on 2010-04-25
Firefox user settings are saved under ~/.mozilla/firefox/<profilename>

The files you are looking for are **signons.sqlite**, which is the database with the passwords, and **key3.db**, which is where the master passwords and encryption keys are stored. If you need to make a backup, then you need to copy both files. You won't be able to view your passwords by opening **signons.sqlite** (with an sqlite manager), because they are encrypted.

If you need to simply view your passwords, then follow the instructions on the post above.

If you need to export them, then use [Password Exporter](https://addons.mozilla.org/en-US/firefox/search/?q=Password+Exporter) extension.

What exactly you want to do?

---

### Post by hakermania on 2010-04-25
Actually, becauz I have to many accounts in sites, I want to access them via a C++ program, so I wnted to know where the files are stored to read them from the program and output them so I can read them without the need of opening firefox...

---


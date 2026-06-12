---
title: "Chorme Error: Your profile could not be opened correctly"
date: 2010-07-07
forum: General Help
---

### Post by spikoley on 2010-07-07
When I open Chrome I receive the error: 

> Your profile could not be opened correctly.

I have found solutions that work, but they delete all my profile information.  This is will not work for me because I want to keep the profile data.  I narrowed it down and the problem with with the Web Data file which is a  SQLite database.  From my research it sounds like the Web Data file gets locked.  How can I unlock this file?  The [command below]("http://www.google.com/support/forum/p/Chrome/thread?fid=46cbd32bea7f4fec00048665de6e82de&hl=en") is suppose to unlock the DB, but I have not had any success with it.


```
IFS="
"
for I  in `file ~/.config/chromium/Default/*|grep SQL|cut -f1 -d:`; do echo '.dump' | sqlite3 $I > ${I}.sql && rm $I && sqlite3 $I < ${I}.sql && rm ${I}.sql ; done
```

Any ideas on how to unlock the Web Data file data base?

---

### Post by spikoley on 2010-08-01
Any ideas?  I would like to save that profile.

---

### Post by spikoley on 2010-08-04
The SQLite DB is corrupted.  Does anybody know how I can repair it or get access to it so I can recover some data?  It won't open in sqlite3 or sqlitebrowser.

---

### Post by Lefke123 on 2010-10-30
Maybe a bit late to provide a solution here, but the thread still ranks pretty high on Google.

The following solution worked for me (without deleting anything):
```

killall chrome
sudo chmod u+rwx -R ~/.config/google-chrome/
sudo chown user:user -R ~/.config/google-chrome/

```
Overkill? Perhaps, but fixed it for me!

---

### Post by betterhands on 2011-11-13
> **Lefke123 said:**
> Maybe a bit late to provide a solution here, but the thread still ranks pretty high on Google.

The following solution worked for me (without deleting anything):
```

killall chrome
sudo chmod u+rwx -R ~/.config/google-chrome/
sudo chown user:user -R ~/.config/google-chrome/

```
Overkill? Perhaps, but fixed it for me!

thanks.  has this issue today for the first time and this worked for me.

---


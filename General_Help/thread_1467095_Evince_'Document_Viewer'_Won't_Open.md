---
title: "Evince 'Document Viewer' Won't Open"
date: 2010-04-30
forum: General Help
---

### Post by jdorenbush on 2010-04-30
As the title says, Evince will not open. Initially I was having problems with Evince not retaining settings ([https://bugs.launchpad.net/ubuntu/lucid/+source/evince/+bug/503372](https://bugs.launchpad.net/ubuntu/lucid/+source/evince/+bug/503372)), but now it just won't open. I tried a reinstall of the software and that didn't fix it.

Thoughts?

---

### Post by gigaSproule on 2010-04-30
I just had this issue. I tried running it from terminal, but it said that some file did not exist, so I just removed the package and reinstalled it. It says that it will uninstall ubuntu-desktop as well, so just accept it.

```
sudo apt-get remove evince
sudo apt-get install evince
sudo apt-get install ubuntu-desktop
```

---

### Post by jdorenbush on 2010-04-30
Yeah, I saw that message too. I wasn't sure if removing Ubuntu-Desktop would cause problems. I was a little worried to proceed.

I ended up installing Adobe Reader, which appears to be working okay. I'm not sure if using Evince is even necessary now. Is there any advantages with Evince over Adobe Reader?

---

### Post by gigaSproule on 2010-04-30
Not that I know off. I don't like Adobe Reader, but that is purely because I had a bad time with it once and it would open and crash constantly. I think evince opens more file types.

---

### Post by Chronon on 2010-04-30
Yes, Evince does more file types and runs a lot lighter than Adobe's Reader.

---

### Post by gigaSproule on 2010-04-30
So an all round better product then.

---

### Post by jakslev on 2010-05-01
> **gigaSproule said:**
> I just had this issue. I tried running it from terminal, but it said that some file did not exist, so I just removed the package and reinstalled it. It says that it will uninstall ubuntu-desktop as well, so just accept it.

```
sudo apt-get remove evince
sudo apt-get install evince
sudo apt-get install ubuntu-desktop
```

Thanks that did the trick and saved me from a (maybe fruitless) reinstall!
Please tag this question as solved - and for the asker we can only recommend getting Adobe uninstalled and doing this. Until Adobe creates a version of Photoshop and Illustrator for Linux they have no place on our machines ;o)

---

### Post by kircher on 2010-05-01
I had this same problem as well. Seems like a dodgy way to fix it though.

---

### Post by gigaSproule on 2010-05-03
It's just uninstalling and reinstalling. Nothing I wouldn't do on another system. Obviously something has conflicted and just needs to be corrected.

---

### Post by moffa on 2010-05-03
If I try to run it through the command line:

** (evince:8538): WARNING **: Error creating last_settings file: Error opening file '/home/username/.gnome2/evince/last_settings': No such file or directory

Segmentation fault

---

### Post by moffa on 2010-05-03
Just ran update-manager and the fix is available.

---

### Post by gigaSproule on 2010-05-03
Is this trying to uninstall, reinstall or running?

EDIT: Need to read other pages in future...

---

### Post by mheartwood on 2011-11-23
Tried running it from the command line /usr/bin/evince. This is what I get:

(evince:2604): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


** (evince:2604): WARNING **: Error creating last_settings file: Error opening file '/home/marie/.gnome2/evince/last_settings': No such file or directory

---

### Post by mheartwood on 2011-11-23
Fixed my own problem using the command line. Here's how:

$ cd ~
$ mkdir .gnome2/evince
$ chmod 0777 .gnome2/evince
$ cat /dev/null > .gnome2/evince/last_settings
$ chmod 0777 .gnome2/evince/last_settings

---


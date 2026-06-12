---
title: "Reinstalling"
date: 2010-06-24
forum: General Help
---

### Post by ubunterooster on 2010-06-24
Okay, so I borked something...yes, again. 

But I have a separate /home partition this time. If I reinstall /, will all my settings on /home be the same? From what I read, I think this means yes, but what happens to all installed programs? I mean, I thought that just the configuration files of programs were stored in /home, so do I need to reinstall all apps? Anything I seem to be missing?

---

### Post by zvacet on 2010-06-25
Yes, your setting will be safe.During install mark partition on witch your home is as /home but **do not format it!**Yes, you will have to install apps again.If you want exactly same system then 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages 
```

You will find text file named my-packages in your home directory.Save it somewhere or e-mail it to yourself and after reinstall put that file in your home directory and type in terminal

```
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install
```

---

### Post by ubunterooster on 2010-06-25
Understood, Thank you.

Oh, and nice signature.

---

### Post by dcstar on 2010-06-25
There is no need at all to use the command line, just use the "Save Markings" function in Synaptic on the original install and the "Read Markings" function on the new install. Put the file in your /home.

---

### Post by ubunterooster on 2010-06-25
[sarcasm]But using the CLI is _so_ much more fun. [/sarcasm] 

Thanks

---


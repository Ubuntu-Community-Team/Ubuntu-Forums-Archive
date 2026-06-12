---
title: "have a program/document/image etc... start up with Ubuntu?"
date: 2011-12-15
forum: General Help
---

### Post by justinrpg on 2011-12-15
I know it is possible to do this in Windows, is it possible to have something start up with the OS in Ubuntu like you can in Windows? I want a Gedit document to start up with Ubuntu... this document contains text that I copy and paste on websites (mainly Facebook) frequently!

---

### Post by drmrgd on 2011-12-15
Sure!  In the system settings panel there should be a section called something like Start Up and Shutdown (I'm on Kubuntu and can't quite remember what it's called in Ubuntu).  You can add programs and scripts to this area, which will auto start when you load the OS.  Should be fairly easy to figure out once you find it.

---

### Post by lechien73 on 2011-12-15
Yes, you can add the command line:

```
gedit /path-to-document
```

into Startup Applications. Obviously replace "/path-to-document" with the path and filename of the document you want to open.

In 11.10 Startup Applications is found under the shutdown and settings menu (the little cog icon on the right-hand side). On versions prior to Unity, you could find it in **System -> Preferences -> Startup Applications**

---

### Post by justinrpg on 2011-12-15
there is nothing like that in system settings!!!!!!!!! and I don't know anything about the coding the second user is talking about!!!!!!!

---

### Post by justinrpg on 2011-12-16
You guys are so mean because you aren't helping me at all!!!!!! Get off you lazy butts and help!!!!!

---

### Post by jerome1232 on 2011-12-16
Okay I was about to post a screenshot by screenshot guide, but forget it. I don't give up my volunteer time to help someone with that kind of attitude. I still have the screenshots if you decide to become sociable.

---

### Post by pretty_whistle on 2011-12-16
> **jerome1232 said:**
> Okay I was about to post a screenshot by screenshot guide, but forget it. I don't give up my volunteer time to help someone with that kind of attitude. I still have the screenshots if you decide to become sociable.
Can't blame you.  I just changed my mind too.

---

### Post by justinrpg on 2011-12-16
ok, I am sorry for being mean!! but I get picked on no matter where I go! there is even a whole website out there dedicated to trolling me!! and I get agitated because people have been mean to me constantly for over a month now! you see where I am coming from?

---

### Post by pretty_whistle on 2011-12-16
> **justinrpg said:**
> ok, I am sorry for being mean!! but I get picked on no matter where I go! there is even a whole website out there dedicated to trolling me!! and I get agitated because people have been mean to me constantly for over a month now! you see where I am coming from?
I understand.

Here's how to put stuff on autostart:

In nautilus, bring up home folder

press ctrl + h to show hidden folders and look for .config, you'll see it.  Then look for autostart folder:
/.config/autostart


This works in 11.04.  If you don't have 11.04 it may still be the same file path.

---

### Post by jerome1232 on 2011-12-16
Click on the Ubuntu Logo in the top right of your screen

Begin typing "Startup Applications" without the quotes, You should see a program called "Startup Applications", click it.

Click Add
Type anything for name
Type "gedit /path/to/you/file" for the command, no quotes
Put anything for the comment.
Click add.

You should be good to go. You can click the thumbnails below to see close ups of me going through the process.

---

### Post by jerome1232 on 2011-12-16
I just wanted to add if ever you can't find something in Ubuntu, that search feature in the dash is your best friend. It's never failed me.

---

### Post by justinrpg on 2011-12-16
how do I know the correct t path of the document? in windows it is right click properties and it will display the full path... how do I find the full path of the document in Ubuntu?

---

### Post by jerome1232 on 2011-12-16
Same thing in Ubuntu, right click the file, hit properties, it's listed as "location"

---

### Post by Habitual on 2011-12-16
> **justinrpg said:**
> You guys are so mean because you aren't helping me at all!!!!!! Get off you lazy butts and help!!!!!

[Fix it your damned self.]("http://ubuntuforums.org/forumdisplay.php?f=331&nojs=1#goto_forumsearch")

> **jerome1232 said:**
> ...I don't give up my volunteer time to help someone with that kind of attitude. ...

+1

---

### Post by jerome1232 on 2011-12-17
> **Habitual said:**
> [Fix it your damned self.]("http://ubuntuforums.org/forumdisplay.php?f=331&nojs=1#goto_forumsearch")



+1

He did apologize, no need to rub salt in it.

---


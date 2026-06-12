---
title: "fstab, ext4 and utf8"
date: 2012-02-18
forum: General Help
---

### Post by Lockheed on 2012-02-18
I want to enable utf8 on my ext4 partition. Why. you might ask? Here's an example:
```
$ dir
-\ Ministry\ Of\ Sound\ -\ Chilled\ 1991-2008\ Disc\ 1.log
-\ Ministry\ Of\ Sound\ -\ Chilled\ 1991-2008\ Disc\ 1.m3u
13\ -\ Tim\ &#65533;&#65533;&#65533;Love&#65533;&#65533;&#65533;\ Lee\ -\ One\ Night\ Samba.mp3
14\ -\ The\ Karminsky\ Experience\ Inc\ -\ Exploration.mp3

```
Files like this cannot be written to, and rarely read. 

Right now my fstab has this partition set on 'defaults'. I know that ext4 is supposed to come with utf8 enabled, but it does not seem to be. If I add utf8 option to the mount line in fstab, the partition mounts in read-only mode and the system doesn't boot up.

So, how can I solve this?

---

### Post by TeoBigusGeekus on 2012-02-18
Open the /etc/xdg/xfce4/mount.rc file, find the ext4 section and uncomment/append
```
utf8=true
```
Save, reboot, post back.

---

### Post by Lockheed on 2012-02-18
No such file. Using xfce 4.8, if it makes a difference.

---

### Post by TeoBigusGeekus on 2012-02-18
Then [this]("http://askubuntu.com/questions/28635/how-to-add-utf-8-support-to-my-hard-disk-in-fstab") perhaps?

---

### Post by Lockheed on 2012-02-18
I'm on Arch and don't have this command.

---

### Post by TeoBigusGeekus on 2012-02-18
Oh hi there, I'm on Arch as well.

Check your /etc/rc.conf file. Is the locale setting correct?
Here's mine:
```
LOCALE="en_US.UTF-8"
```

---

### Post by Lockheed on 2012-02-18
Here's mine:
```
$ locale
LANG=en_GB.UTF-8
LC_CTYPE=en_GB.UTF-8
LC_NUMERIC=en_GB.UTF-8
LC_TIME=pl_PL.UTF-8
LC_COLLATE=C
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES=en_GB.UTF-8
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT=pl_PL.UTF-8
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

---

### Post by TeoBigusGeekus on 2012-02-18
Strange...
Is the locale enabled?
Open the /etc/locale.gen file and check if this line
```
en_GB.UTF-8 UTF-8 
``` 
is uncommented. 
If not, do it and then run
```
sudo locale-gen
```

---

### Post by Lockheed on 2012-02-18
Yes, it is , I wouldn't count on a run-of-the-mill solution here ;)

---

### Post by TeoBigusGeekus on 2012-02-18
I don't know what to say mate, sorry.
Perhaps you'd have better luck in the Arch Linux Forums.

---

### Post by Lockheed on 2012-02-18
Maybe, but theirs is a slow forum.

Here's an example of the issue in three different forms:
[http://tinyurl.com/7kdg5r4](http://tinyurl.com/7kdg5r4)

---

### Post by TeoBigusGeekus on 2012-02-18
Perhaps the creator of these mp3s used an exotic and far out encoding - I'm no expert on this subject.
Although my system supports utf8, I do sometimes encounter file/folder names with strange characters in them (especially if their origin is a bit ambiguous - nudge, nudge).

---

### Post by Lockheed on 2012-02-18
I did a little test and created a folder using only Polish special characters. None of them got displayed. All I got was string of "????".

---

### Post by TeoBigusGeekus on 2012-02-18
Which font do you use?

---

### Post by Lockheed on 2012-02-18
Doesn't matter. It occurs in various programs using various fonts.

---

### Post by TeoBigusGeekus on 2012-02-18
Could you write something on a text file (just some jibberish - but with junk characters) and attach it here?
(Just out of curiosity, ignore me if you want to...)

---

### Post by Lockheed on 2012-02-18
That won't give you much, because characters appear perfectly fine in text files.

But here's a new discovery. If I create a folder with Krusader, it is all screwed up, but if I use the same characters in pcmanfm, the folder name is created perfectly fine. Most of the files I have provblems with are created by Nicotine.

---

### Post by TeoBigusGeekus on 2012-02-18
A kde setting then?
Can't help you there, I'm allergic to kde...

---

### Post by Lockheed on 2012-02-18
kde sux, that's why I do not have it. And I don't think nicotine-plus is a kde app, so kde is not the troublemaker here.

---

### Post by TeoBigusGeekus on 2012-02-18
[See the last post]("http://forum.krusader.org/viewtopic.php?p=10451").
A bit old but it could still apply...

EDIT: See also [this]("http://www.nicotine-plus.org/ticket/223").
EDIT2: Title of thread states xfce - I ask you if you use kde; total brainfart, sorry...

---

### Post by Lockheed on 2012-02-18
This  might suggest that in reality only en_US.UTF-8 supports UTF8.

---

### Post by TeoBigusGeekus on 2012-02-18
There's only one way you can find out...

---


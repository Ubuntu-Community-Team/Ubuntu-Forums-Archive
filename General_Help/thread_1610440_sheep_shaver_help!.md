---
title: "sheep shaver help!??"
date: 2010-10-31
forum: General Help
---

### Post by penguin1029 on 2010-10-31
hello! i need some help i need to do this: 
> Due to a change in how programs in Linux are allowed to use memory, before using SheepShaver you need to set a variable in the file 
/etc/sysctl.conf 
Add this line: vm.mmap_min_addr = 0
but when i add the line in my text editor it says i cant save!!! 
please help!!!!
 :( :(

---

### Post by trikster_x on 2010-10-31
in terminal type:
```
gksudo gedit /etc/sysctl.conf
```

---

### Post by spiky001 on 2010-10-31
dose it say permission denied

---

### Post by penguin1029 on 2010-10-31
> **trikster_x said:**
> in terminal type:
```
gksudo gedit /etc/sysctl.conf
```

It worked but now when i press start this happens in the terminal 

```
SheepShaver V2.3-Pre (Jan 17 2008) by Christian Bauer and Mar"c" Hellwig
Segmentation fault

```
then sheepshaver exits?!
bump

---

### Post by penguin1029 on 2010-10-31
Bump

---

### Post by trikster_x on 2010-10-31
That looks like it is a problem caused by sheep shaver itself.  And when you say press start, I assume you mean you have logged in to Ubuntu and are using the program through a command line?

Oh, and there is no need to bump if it has been less than a few hours.  Most people who are looking to give help will dig a few pages into the forums to see if there is anyone who still needs an answer.

---

### Post by penguin1029 on 2010-10-31
> **trikster_x said:**
> That looks like it is a problem caused by sheep shaver itself.  And when you say press start, I assume you mean you have logged in to Ubuntu and are using the program through a command line?

Oh, and there is no need to bump if it has been less than a few hours.  Most people who are looking to give help will dig a few pages into the forums to see if there is anyone who still needs an answer.

Yes Through the command line 
and thanks for the bump advice  
i got sheep shaver the deb from (i didn't compile)
[http://ubuntuforums.org/showthread.php?t=670336](http://ubuntuforums.org/showthread.php?t=670336)

---

### Post by trikster_x on 2010-10-31
Bad news:
[http://ubuntuforums.org/showthread.php?t=1334190&page=3]("http://ubuntuforums.org/showthread.php?t=1334190&page=3")

Looks like there has been more trouble getting this to run on the latest versions of Ubuntu than just a conf file.  There is mention of a .deb file on the last page, so maybe try that one out.

---

### Post by penguin1029 on 2010-10-31
> **trikster_x said:**
> Bad news:
[http://ubuntuforums.org/showthread.php?t=1334190&page=3]("http://ubuntuforums.org/showthread.php?t=1334190&page=3")

Looks like there has been more trouble getting this to run on the latest versions of Ubuntu than just a conf file.  There is mention of a .deb file on the last page, so maybe try that one out.

i got this error 
```
Installing package...
dpkg: error processing /tmp/fileUgzV1W.deb (--install):
 cannot access archive: Permission denied
Errors were encountered while processing:
 /tmp/fileUgzV1W.deb

```

---


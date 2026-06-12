---
title: "chown not working and ubuntu version unclear"
date: 2010-02-08
forum: General Help
---

### Post by elektros75 on 2010-02-08
hi, 

like all noobs, of which i'm still one since i've only had ubuntu for about 3 weeks now,  i installed it somehow skipping the home directory.  so i tried to follow these steps...

[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/#comment-146998](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/#comment-146998)
 however i initially screwed up my home dir location, and am glad to say that restarting the laptop and running recovery fixed the problem.


however i still cannot copy any files to the newhome directory and i don't know if it's because of the problem that my user name is listed in the permissions tab as 'patrick - Patrick'... and i keep getting errors, i assume it’s because there’s a couple of spaces…


 ```
patrick@patrick-laptop:~$ sudo chown patrick – Patrick:patrick /media/newhome
chown: cannot access `-’: No such file or directory
chown: cannot access `Patrick:patrick’: No such file or directory
patrick@patrick-laptop:~$ 
```
 i also tried this…  



```

patrick@patrick-laptop:~$ sudo chown patrick:patrick /media/newhome
```
but nothing seems to happen, and the permissions stay the same
 am i doing something wrong???   if not, how do i change my owner name to "patrick" and is that even possible in ubuntu


the other question is, which version of ubuntu am i running, i initially installed 8.10, and i upgraded to 9.04 after talking to a friend about a week ago...  I don't remember upgrading to 9.10, but my update manager says “Your system is up-to-date” and that the package info was updated an hour ago… it used to give me an option to upgrade to 9.10, does this mean I’m using 9.10 instead of 9.04???




sorry to ask, i'm just confused

---

### Post by elektros75 on 2010-02-08
ok, i ran
```
 ls -l
```
and it is just 
```
patrick:patrick
```
but i'm still not seeing any changes with the chown command

---

### Post by Leppie on 2010-02-08
the correct way to use chown is the way you tried the 2nd time:
```
sudo chown patrick:patrick /media/newhome
```could you post the contents of your fstab? most probably there's something there which will shed a light on why you cannot chown the folder.
```
cat /etc/fstab
```

to get your installed release version:
```
lsb_release -cd
```

---

### Post by audiomick on 2010-02-08
> **elektros75 said:**
> ...f the problem that my user name is listed in the permissions tab as 'patrick - Patrick'... [/CODE]
I can't break it down for you, but that is normal and correct, not a problem

 >   i also tried this&#8230;  
```

patrick@patrick-laptop:~$ sudo chown patrick:patrick /media/newhome
```Look at
```
man chown
```there is info about syntax in there. From what I could gather, your command is telling chown to change ownership to patrick and group to patrick. I think, but am not sure, that the group should be "users". You will have to check that out yourself.

[QUOTE]the other question is, which version of ubuntu am i running, go to
system> administration> system monitor and look on the first tab.

edit: damn, Leppie beat me again...

---

### Post by Leppie on 2010-02-08
> **audiomick said:**
> From what I could gather, your command is telling chown to change ownership to patrick and group to patrick. I think, but am not sure, that the group should be "users". You will have to check that out yourself.
patrick : patrick (without the spaces, but this script puts a smiley if i write it the correct way) is ok if he wants to set permissions only to himself (every user account has its own explicit group as well). if other users need to be able to access this folder as well, the user group (or a group added specifically for this purpose) is more appropriate.

> **audiomick said:**
> edit: damn, Leppie beat me again...
you're getting too old... :tongue:

---

### Post by Bachstelze on 2010-02-08
Is /media/newhome FAT32 or NTFS? Those filesystems do not support UNIX-style permissions, so chown and chmod won't work on them.

---

### Post by audiomick on 2010-02-08
> **Leppie said:**
> patrick : patrick (without the spaces, but this script puts a smiley if i write it the correct way)put code tags around it. No more smileys...

> you're getting too old... :tongue:
thanks for that....;)

---


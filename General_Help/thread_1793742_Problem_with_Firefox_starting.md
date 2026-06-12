---
title: "Problem with Firefox starting"
date: 2011-06-30
forum: General Help
---

### Post by NewJack on 2011-06-30
Hello all,

Tried starting FF & for some reason it pops up in the taskbar with "Starting Firefox Web Browser", then nothing.  I already tried uninstalling & reinstalling to no avail.

I tried to start FF from the Terminal & got this error message:

> Traceback (most recent call last):
  File "/usr/lib/firefox-5.0/xulapp-profilemigrator", line 459, in <module>
    update_stamp (options.profile + '.last-version', options.series if migrator.ask_again == False else migrator.last_series.raw)
  File "/usr/lib/firefox-5.0/xulapp-profilemigrator", line 437, in update_stamp
    fd = open (stampfile, 'w')
IOError: [Errno 13] Permission denied: '/home/joe/.mozilla/firefox.last-version'

Not sure where to go from here.  Any help is appreciated.  Thanks!

Joe

---

### Post by vehemoth on 2011-06-30
Have you tried backing up your profile and using the purge command
```

sudo apt-get purge [package name]

```

---

### Post by JPAdv on 2011-06-30
One thing you could do is try removing the .mozilla folder in your home directory.

1. Make sure you are in your home directory by typing:
```
 cd ~
```

2. Type ** ls ** and make sure the .mozilla folder is in your home directory.

3. Then type:
```
 sudo rm -r .mozilla 
```

This should remove the .mozilla folder and its contents.

4. Try installing or reinstalling firefox and open it.

I hope this helps.

---

### Post by NewJack on 2011-06-30
Thanks guys.  I'll give that a try when I get home & report back with results.

Joe

---

### Post by WorMzy on 2011-06-30
Have you launched firefox with "sudo" at any point? Because that can mess up your config file permissions.

Simply run
```
sudo chown $USERNAME:$USERNAME ~/.mozilla
```

and it should be fixed.


In the future, *don't* use sudo for graphical applications. Use gksu or gksudo instead. You shouldn't need to run firefox as root in the first place.

---

### Post by NewJack on 2011-07-03
JPAdv - That did the trick.  Thanks alot!

Joe

---


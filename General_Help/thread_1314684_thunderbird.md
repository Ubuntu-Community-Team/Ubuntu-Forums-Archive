---
title: "thunderbird"
date: 2009-11-04
forum: General Help
---

### Post by t12121 on 2009-11-04
I have lost my profiles on thunderbird.  I know the default information is still there by looking at the folder structure.  But when I load up thunderbird it acts like I just installed it.  I tried using thunderbird -profilemanager and using default there but it loads the same thing.  Any ideas on how to fix this???  I had some things set up custom and would be a pain to start over again.  

PLease help 
Tom

---

### Post by scout4536 on 2009-11-04
Did u recently upgrade thunderbird?

---

### Post by t12121 on 2009-11-04
> **scout4536 said:**
> Did u recently upgrade thunderbird?

Not that I know of.  Was working earlier today.  But it did crash I might have has thunderbird open I really dont remember.  (computer getting old is my guess)

---

### Post by Giblet5 on 2009-11-04
Did you alter the ownership on ~/.mozilla-thunderbird or its subfiles/directories?

```
sudo chown -R $LOGNAME:$LOGNAME $HOME/.moz*
```

will fix it if that's the problem.

---

### Post by t12121 on 2009-11-04
> **Giblet5 said:**
> Did you alter the ownership on ~/.mozilla-thunderbird or its subfiles/directories?

```
sudo chown -R $LOGNAME:$LOGNAME $HOME/.moz*
```

will fix it if that's the problem.

tried it did the same thing

---

### Post by Giblet5 on 2009-11-04
Worth a shot though...

Open a terminal window and enter the following commands: ```
cd .mozilla-thunderbird
ls -l
echo =====================================
cat profiles.ini
``` and select/copy the output.

Then post the output.

This is probably a very easy one, BTW.


PS: Here is mine ```
$ ls -l
total 12
-rw-r--r-- 1 pw pw  335 2006-09-13 09:05 appreg
drwxr-x--- 8 pw pw 4096 2009-11-04 14:49 **[COLOR="DarkRed"]n4kek34a.default[/COLOR]**
-rw-r--r-- 1 pw pw   94 2006-09-13 09:05 profiles.ini

$ cat profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=**[COLOR="DarkRed"]n4kek34a.default[/COLOR]**
```

See how that works?

---

### Post by t12121 on 2009-11-04
cd .mozilla-thunderbird
[email]jerry@jerry:~/.mozill[/email]a-thunderbird$ ls -l
total 8
drwx------ 6 jerry jerry 4096 2009-11-04 17:17 mkrb887k.default
-rw-r--r-- 1 jerry jerry   94 2009-11-04 17:15 profiles.ini
[email]jerry@jerry:~/.mozill[/email]a-thunderbird$ echo =====================================
=====================================
[email]jerry@jerry:~/.mozill[/email]a-thunderbird$ cat profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=mkrb887k.default

---

### Post by Giblet5 on 2009-11-04
Well, it looks OK from here.

That folder and the profiles.ini entry are all there is to a Tbird profile, and you're set up to use the only profile.

When did you last do a backup? Is it worth going back that far?


I have other systems at my disposal and I sync Tbird to those other systems once per hour via this script ```
#!/bin/sh

if [ -z "$1" ] ; then
  echo "Usage: tbird-xfer hostname"
  exit 1
fi

cd $HOME
rsync -aurptz .gnupg .mozilla-thunderbird $1: && exit 0

exit 1
```

---

### Post by t12121 on 2009-11-04
Backup?  whats that?  But really I dont have anything that I cant get again.  Just annoys me to re-setup my custom folders and such.  just takes a while to remember how I had the stuff set up.

---

### Post by oldfred on 2009-11-04
Look here for all sorts of help on thunderbird problems:
[http://kb.mozillazine.org/Category:Issues_%28Thunderbird%29](http://kb.mozillazine.org/Category:Issues_%28Thunderbird%29)

and one of those pages is this:
[http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared](http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared)

---

### Post by t12121 on 2009-11-05
Thanks all I just re-did everything and it seems to be back working. thanks for the assist anyway!

Tom

---

### Post by bonnieuehh1 on 2011-01-13
> **t12121 said:**
> I have lost my profiles on thunderbird. I know the default information is still there by looking at the folder structure. But when I load up thunderbird it acts like I just installed it. I tried using thunderbird -[[COLOR=#000000]profilemanager[/COLOR]](http://www.******.net/is/relationships/celebrity-diamond-earrings.html) and using default there but it loads the same thing. Any ideas on how to fix this??? I had some things set up custom and would be a pain to start over again. PLease help TomI'll take a try right now, I've got the same problem, I've been looking for the answer for long time.

---


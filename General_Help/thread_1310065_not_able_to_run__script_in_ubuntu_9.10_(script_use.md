---
title: "not able to run  script in ubuntu 9.10 (script used to synchronize firefox profile)"
date: 2009-11-01
forum: General Help
---

### Post by imlinux on 2009-11-01
i used to run my firefox mounted on ram using this [guide]("http://ubuntuforums.org/showthread.php?t=1120475"), on previous versions of ubuntu, but on new ubuntu 9.10,i am not able to run the script its says error in line 17 and 18 
here is the script 
```
#!/bin/bash

# Change this to match your correct profile
PROFILE="xxxxxxxx.default"

cd "${HOME}/.mozilla/firefox"

if test -z "$(mount | grep -F "${HOME}/.mozilla/firefox/${PROFILE}" )"
then
    mount "${HOME}/.mozilla/firefox/${PROFILE}"
fi

if test -f "${PROFILE}/.unpacked"
then
    rsync -av --delete --exclude .unpacked ./"$PROFILE"/ ./profile/
else
    rsync -av ./profile/ ./"$PROFILE"/
    touch "${PROFILE}/.unpacked"
fi

exit
```

---

### Post by imlinux on 2009-11-02
any help guys ? i cant figure out whats wrong.please test it

---

### Post by philippe_carlo on 2009-11-02
Did you actually fill in the correct profile name in the script?

Seems line 17 is the rsync call.
Go to the profile directory
```
cd "${HOME}/.mozilla/firefox"
```
and try to run 
```
rsync -av ./profile/ ./"$PROFILE"/
```
form that directory (replace "$PROFILE" including the quotes with the correct profile name).

See what happens, you may get a more detailed error message.

---

### Post by imlinux on 2009-11-02
> **philippe_carlo said:**
> Did you actually fill in the correct profile name in the script?

Seems line 17 is the rsync call.
Go to the profile directory
```
cd "${HOME}/.mozilla/firefox"
```
and try to run 
```
rsync -av ./profile/ ./"$PROFILE"/
```
form that directory (replace "$PROFILE" including the quotes with the correct profile name).

See what happens, you may get a more detailed error message.

but this is already given at start of script that PROFILE is xxxxxxxx.default (which mine is ux4m1zlc.default)
```
PROFILE="xxxxxxxx.default"

```
or do i need to change it in every line

---


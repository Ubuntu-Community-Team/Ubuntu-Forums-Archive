---
title: "i could use some sed help"
date: 2012-09-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-09-06
i can't stand regular expressions :lolflag:
i am trying to use sed to insert a line before exit 0 in /etc/rc.local
if it was not for the comment with exit 0 in it i would be good to go
this is what i have
```
cat /etc/rc.local | sed 's/exit 0/sh myscript\nexit 0/'
```this is not even a global replace and it is replacing more than one...
i only want to replace the 1st one that does not have a line starting with "#"
i would prefer the new line to have a & (sh myscript &) an the end but i cant seem to pull that off at all

---

### Post by steeldriver on 2012-09-07
this seems to work

```
echo -e "# exit 0\nexit 0" | sed 's/^[^#]*exit 0/sh myscript \&\n&/'
# exit 0
sh myscript &
exit 0
```(the first & is escaped i.e. \& to give literal &; the second back substitutes the matching exit 0)

or you could use the 'i' command

```
sed '/^[^#]*exit 0/i \
sh myscript \&'
```

---

### Post by pqwoerituytrueiwoq on 2012-09-07
thanks, but why did \& not work for me earlier... seems to work now :?

---


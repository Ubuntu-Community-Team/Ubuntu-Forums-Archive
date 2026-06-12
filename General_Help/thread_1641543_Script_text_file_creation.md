---
title: "Script text file creation"
date: 2010-12-09
forum: General Help
---

### Post by JasonFWard on 2010-12-09
I am writing a script to download, install and configure a package that isn't in a DEB or any Ubuntu archive.

I have done most of the work now, but I want the script to be able to create a series of configuration, and so far I've been doing this with ```
echo something >> some.conf
``` only I've a lot of it, loads infact and its getting messy and hard to read.

I wondered if I could use sed to read in the script I've written and using markers inserted into it, copy part of the script into another file.

Having said that, my sed skills are nil, nada, zilch, so first of all, is what I want to do even possible?

---

### Post by DaithiF on 2010-12-09
either use a here document:

```
echo <<EOF >> somefile
All this text
will get appended to your file
up to but (not including)
the marker
EOF
```

or yes, you could use sed:

```
sed -n '/marker1/,/marker2/p' somefile >> anotherfile
```

---

### Post by JasonFWard on 2010-12-09
Thats great, thanks, I've also found the bash construct

{
echo something
echo something else
echo another something
} > something.conf

---


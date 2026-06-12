---
title: "cut command last field"
date: 2011-09-22
forum: General Help
---

### Post by tyoli on 2011-09-22
hi there,

i'm trying to write a script and i have a problem with the cut command. so basically i want this:

[CENTER]
azerty qwsdcf 123.25-hdf
qsdfh dfhrhe
sdfg sdg sdg sdgze 145
zegtz
[/CENTER]

to be like this:
[CENTER]
azerty%20qwsdcf_version_123.25-hdf.ext
qsdfh%20dfhrhe_version_.ext
sdfg%20sdg%20sdg%20sdgze_version_145.ext
zegtz_version_.ext
[/CENTER]

but i can't select the last field with the cut command any help thanx.

---

### Post by papibe on 2011-09-22
I think 'awk' can help more with that. For example:
```
$ awk '{print $NF}' yourfile
123.25-hdf
dfhrhe
145
zegtz

```
Hope it helps,
Regards.

---

### Post by tyoli on 2011-10-01
> **papibe said:**
> I think 'awk' can help more with that. For example:
```
$ awk '{print $NF}' yourfile
123.25-hdf
dfhrhe
145
zegtz

```
Hope it helps,
Regards.

hi, thanx for replying, but that isn't completely what i'm looking for you see i don't just need the last string but to test it like this if i have a string like so:
[CENTER]stringa stringb stringc[/CENTER]
if stringc is alphanumeric 
then 
[CENTER]stringa%20stringb%20_version_stringc.ext[/CENTER]
else
[CENTER]stringa%20stringb%20stringc%20_version_.ext[/CENTER]
fi

so the awk thing need to test for alphanumeric value in stringc.

---

### Post by papibe on 2011-10-01
Hi tyoli,

My assessment is that you can solve that problem using awk. My intention was to point to in that direction so you would evaluate it, and if you saw possibilities, research about it.

As in my previous post, I going to give you another example that may get you closer:
```
$ awk '{ if ($NF ~ /[0-9]/) print $NF; else print "none alpha" }' yourfile
123.25-hdf
none alpha
145
none alpha

```
I hope this post gives you some value,
Kind Regards.

---

### Post by tyoli on 2011-10-09
> **papibe said:**
> Hi tyoli,

My assessment is that you can solve that problem using awk. My intention was to point to in that direction so you would evaluate it, and if you saw possibilities, research about it.

As in my previous post, I going to give you another example that may get you closer:
```
$ awk '{ if ($NF ~ /[0-9]/) print $NF; else print "none alpha" }' yourfile
123.25-hdf
none alpha
145
none alpha

```
I hope this post gives you some value,
Kind Regards.
thanks that's exactly what i'm looking for.

---

### Post by papibe on 2011-10-09
:) Great! Please mark the thread solved when you have the chance.
Regards.

---


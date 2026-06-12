---
title: "Trying to unistall bandwidthd"
date: 2010-12-05
forum: General Help
---

### Post by squishjt on 2010-12-05
Looking for a little help uninstalling a program called bandwidthd. It recommends that i update before removal, but also doesn't work, here's the error I get....

[[IMG]http://img441.imageshack.us/img441/9467/screenshot1uv.png[/IMG]]("http://img441.imageshack.us/i/screenshot1uv.png/")

Any ideas how i can remove it?


[IMG]http://yfrog.com/c9screenshot1uvp[/IMG]

---

### Post by TeoBigusGeekus on 2010-12-05
Reinstall it and then purge it again.
```
sudo apt-get install --reinstall bandwidthd; sudo apt-get purge bandwidthd
```

---

### Post by squishjt on 2010-12-05
Thanks for the quick reply TeoBigusGeekus, heres what I got.

[[IMG]http://img405.imageshack.us/img405/5255/screenshot2tk.png[/IMG]](http://img405.imageshack.us/i/screenshot2tk.png/)

---

### Post by TeoBigusGeekus on 2010-12-05
Another apt-get session is running. Do you have synaptic package manager open?
If not, reboot and try again.

---

### Post by squishjt on 2010-12-05
Doh, yup i had left synaptic package manager open, heres what i got this time..

[[IMG]http://img819.imageshack.us/img819/6006/screenshotiiz.png[/IMG]](http://img819.imageshack.us/i/screenshotiiz.png/)

---

### Post by gandaran on 2010-12-05
try using synaptic package manager to fix broken packages

---

### Post by squishjt on 2010-12-05
> **gandaran said:**
> try using synaptic package manager to fix broken packages


Just tried that again gandaran, SPM says it has fixed all dependency issues however I get the same error as first post. Thanks for trying though mate.  Happy holidays.

---

### Post by squishjt on 2010-12-06
any more ideas guys?

---


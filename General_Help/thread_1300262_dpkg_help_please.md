---
title: "dpkg help please"
date: 2009-10-24
forum: General Help
---

### Post by FrankQC on 2009-10-24
I've been looking around the Internet and can't seem to find what I'm looking for.

Basically, when I type 'dpkg -l', it gives me a list of installed softwares (i.e. xfce4, etc).

I completely removed xfce4 from my system, but when I do 'dpkg -l' it says that the packages are still installed. So I do 'apt-get remove <package name>' and it says it's not installed.

Is it because my dpkg list is out of date and needs to be updated?

thanks!

---

### Post by cilynx on 2009-10-25
Can you show us the output of:

```
dpkg -l|grep -i xfce
```

---

### Post by falconindy on 2009-10-25
Depending on how you removed XFCE, you may have left behind configuration bits. You'll need to use 'apt-get remove --purge <package>'. You can also use Synaptic to great effect here. In the lower left, you'll see some buttons. Click on the one labelled "Status", and then above the buttons in the list, click on "residual config". You'll probably see things you thought were long gone. Select them all, right click and "mark for complete removal".

---

### Post by blwizard on 2009-10-25
Do "sudo apt-get autoremove" and check again?

---


---
title: "Flash problem"
date: 2012-04-10
forum: General Help
---

### Post by cogier on 2012-04-10
I have an old Shuttle computer in my garage that runs Ubuntu 10.04 and all of a sudden Flash has stopped working.

I decided, after many failed attempts to sort the problem, to reinstall 10.04.

A full installation later, updated to 10.04.4, Ubuntu Restricted Extras loaded and Medibuntu repository enabled and still no Flash

I have other computers running 10.04.4 and Flash works well.

Attached is the output of lshw should it help.

Any ideas?

Thanks.

---

### Post by kc1di on 2012-04-10
> **cogier said:**
> I have an old Shuttle computer in my garage that runs Ubuntu 10.04 and all of a sudden Flash has stopped working.

I decided, after many failed attempts to sort the problem, to reinstall 10.04.

A full installation later, updated to 10.04.4, Ubuntu Restricted Extras loaded and Medibuntu repository enabled and still no Flash

I have other computers running 10.04.4 and Flash works well.

Attached is the output of lshw should it help.

Any ideas?

Thanks.

go to /usr/lib/mozilla/plugins and make sure that flashplugin-alternative.so or flashplayer is there or a link to it. If not do a system search for it and make a link to it into this folder.

If it is there let us know we will go from there.

Another thing you may want try is go to Firefox>tools>addons and add the add on flash aid it will install the adobe flashplayer on the system and give that a try.

---

### Post by lovinglinux on 2012-04-10
Try these:

[Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

[http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by cogier on 2012-04-10
kc1di, thanks for these tips but everything seemed to be in place but Flash still refused to work

lovinglinux, thanks as well. Flash-aid did lots of downloading etc but the outcome was the same. I followed the instructions in the link you provided and I have been able to get Flash to work in Chrome (which is great and all that I need), but it wont work in Firefox or Opera! As this is only an old machine I use now and then I am marking this as "Solved"

Thank you both for your input.

---


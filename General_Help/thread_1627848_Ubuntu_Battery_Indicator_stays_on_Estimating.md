---
title: "Ubuntu Battery Indicator stays on Estimating"
date: 2010-11-21
forum: General Help
---

### Post by rasfl3 on 2010-11-21
Hello. I have an HP Pavilion dv1659us Notebook PC. The Ubuntu Indicator Battery Indicator stays on Estimating for the time of the battery remaining. How can I solve this issue. I appreciate any assistance received.

---

### Post by rasfl3 on 2010-11-22
bump

---

### Post by Isaac356 on 2010-11-23
I, too, am having this problem, but my computer is a system76 pangolin. It seems to have started around the 10.10 upgrade. Hopefully, someone out there knows what might be going on and how to fix it.

I should note that other things, like the battery screenlet, work correctly. The indicator applet is the only thing that doesn't work for me.

---

### Post by rasfl3 on 2010-11-25
Yep, the only thing it doesn't show for me is the estimated time, the percentage and all the other battery details show up. Hopefully an update will be pushed out to fix the issue or somebody can provide us with a fix.

---

### Post by onaridge on 2010-11-25
In the meantime you can use the battery indicator on Docky if you use Docky. That's my work around for now.

---

### Post by rasfl3 on 2010-12-07
I don't use it but I'll look into it. Thanks!

---

### Post by rugbeeprop on 2011-01-02
Hi, 

Try this [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258)

> 
[Fabián Rodríguez]("https://launchpad.net/%7Emagicfab")             wrote             on 2010-10-26:                                                             [ #91]("https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258/comments/91")                                                        Steps to apply @Brian's PPA update:
1) From a terminal window:
sudo add-apt-repository ppa:brian-rogers/power
sudo apt-get update
sudo apt-get upgrade
2) Reboot
3) Login normally, click on the battery icon

        



---

### Post by Isaac356 on 2011-01-02
> **rugbeeprop said:**
> Hi, 

Try this [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258)

Worked for me!

Thanks!

---

### Post by drazgo on 2011-01-20
> **rugbeeprop said:**
> Hi, 

Try this [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258)

Worked like a charm! Thank you so much! :p

---

### Post by drazgo on 2011-01-20
> **rugbeeprop said:**
> Hi, 

Try this [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/629258)

Worked like a charm! Thank you so much! :p

---

### Post by jacebenson on 2011-07-08
Thanks for the quote rugbeeprop.

Worked for me too.

Now if my laptop would just shut off when I tell it to.

---


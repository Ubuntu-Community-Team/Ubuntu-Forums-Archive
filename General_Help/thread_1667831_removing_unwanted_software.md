---
title: "removing unwanted software"
date: 2011-01-15
forum: General Help
---

### Post by watgrad on 2011-01-15
Hello,
I installed Softmaker Office 2008 a while ago and would now like to remove it.

To install, I had to force the installation architecture (I run 64 bit, the application was a 32 bit...).

The normal methhods I would use to remove software son't seem to apply in this case... I can use apt-get remove, the software centre, or synaptic to find and remove the software packages...

I can 'see' the package called "softmaker-office-2008" with dpgk --list

I just want to know how to remove it...

Thanks for any help you can provide...

---

### Post by DanneStrat on 2011-01-15
If you go into synaptic and click the status button in the lower 

left corner then you can see all the installed packages on your 

system. Are you able to find it there?

---

### Post by watgrad on 2011-01-15
Hi - no it doesn't show up there...
John

---

### Post by DanneStrat on 2011-01-15
Have you seen this?

[http://www.softmaker.com/english/tipslinux_en.htm](http://www.softmaker.com/english/tipslinux_en.htm)

You could try to list your packages with 

```
sudo dpkg --get-selections
```

and then remove it with

```
sudo dpkg -r name of package
```

---

### Post by watgrad on 2011-01-15
Yes - that worked perfectly.  Thanks!

---

### Post by DanneStrat on 2011-01-15
> **watgrad said:**
> Yes - that worked perfectly.  Thanks!

You're welcome!

---


---
title: "grafic problem, broken nvidia driver or so"
date: 2009-11-18
forum: General Help
---

### Post by hag01 on 2009-11-18
Hi alltogether,

I am quite a Newbie to Linux, however I think this topic is rather not-newblie-like so I post it in here.

I have had the newest version of Kubuntu on my Dell Inspiron 6400 with a Geforce Go 7300 and all Upgrades but no drivers for the nvidia Geforce card.

Since I wanted to use a second monitor, i planned to install the software, so went to the hardware driver program and activated the recommended nvidia option. there was no reaction on it, so i did it later again, getting a system error.
When I rebooted, the nvidia driver failed to load, as the recovery option showed me, and I am left with no graphical interface in the promt. There, I can't handle the problem on my own.

I mainly use Windows on my Notebook and Kubuntu runs on a second partition, I hardly use it so far, but the plan is to emigrate slowly from Windows in my private work.

I hope you guys can help me,

Cheers

---

### Post by mechro on 2009-11-18
If you can boot from a LiveCd, navigate to **etc/X11** in your Kubuntu installation and rename your **xorg.conf** file to anything else (rename it so you'll recognise it as a back-up if required).

Reboot your Kubuntu installation and it should reconfigure your X system to use the original working configuration.

If you can get it working again you can do a bit more research on your nvidia driver problem.

---

### Post by hag01 on 2009-11-18
I don't have a live-cd here, can't I do it from the promt?

---

### Post by mechro on 2009-11-18
> **hag01 said:**
> I don't have a live-cd here, can't I do it from the promt?

Er... oh dear! ... command line stuff... I'll have a go... try...

```
mv /etc/X11/xorg.conf /etc/X11/xorg2.conf
```

... and you might need to sudo that.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg2.conf
```

---

### Post by hag01 on 2009-11-18
now it works and i am back in the graphical interface as before. this promt-issue solved, thanks mechro!

---


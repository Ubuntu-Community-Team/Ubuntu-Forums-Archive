---
title: "How do I reinable the boot splash on Acer Netbook?"
date: 2010-05-08
forum: General Help
---

### Post by reluttr on 2010-05-08
When booting my netbook I get this error instead of the splash.

"acer-wmi: unable to detect available WMID devices"

is there a way of forcing it to show the splash instead of the error?

Also, some of the graphical bits such as the pop up volume bar and brightness bar are very choppy.

---

### Post by reluttr on 2010-05-08
Ok I fixed the choppy GUI... basically you have to go into the software catalog and install Compiz and enable advance graphics under the Appearance settings window.

I am still looking into the boot issue though, some have suggested doing a disk check though. Ill post if I get it to work.

---

### Post by _0R10N on 2010-05-08
If you want to get rid of text messages during boot, you can install Startup Manager

```
sudo aptitude install startupmanager
```Once it's installed, you can run it form a terminal by simply executing

```
startupmanager
```A window will popup, there you will found an option saying "Show text during boot". Uncheck it.

Since usplash isn't recommended for Lucid anymore, if you want to restore to original splash settings, you can install the package ubuntu-desktop

```
sudo aptitude install ubuntu-desktop
```Kind regards!

---

### Post by Pjotr123 on 2010-05-08
Better disable Acer WMI:

Accessories - Terminal

type (copy/paste):
```

gksudo gedit /etc/modprobe.d/blacklist.conf

```

Press Enter.

Add the following lines, at the end of the text in that text file (use copy/paste):

```

# makes Acer Aspire One run better
blacklist acer_wmi

```

Save, exit, reboot.

---

### Post by reluttr on 2010-05-11
Hrmm... still haven't had any luck enabling the plymouth boot animation. 

Blacklisting acer_wmi seems to have gotten rid of the error though.

---


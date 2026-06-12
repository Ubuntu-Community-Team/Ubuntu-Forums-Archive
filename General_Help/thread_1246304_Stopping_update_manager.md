---
title: "Stopping update manager"
date: 2009-08-21
forum: General Help
---

### Post by gforster on 2009-08-21
I have a lab of 30 computers that are constantly showing the pop-under for updates. I would like to turn off updates completely and manually manage them. I know there is an answer, but I can't seem to find the right search terms to find it!

---

### Post by pastalavista on 2009-08-21
In the System > Administration menu click Update Manager and in the lower left corner click "Settings". Uncheck all the boxes.

---

### Post by gforster on 2009-08-21
thank you.  Now. . .is there a command-line way to do the same (so i can do it on multiple computers through ssh)?

---

### Post by Grannun on 2009-08-21
yes, type these two commands for any computer in this order

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by michy99 on 2009-08-21
> **Grannun said:**
> yes, type these two commands for any computer in this order

```
sudo apt-get update
sudo apt-get upgrade
```

Umm... how will that *disable* the updates?

---

### Post by Grannun on 2009-08-21
that doesn't disable it, that's how you update via the command line

---

### Post by gforster on 2009-08-21
OK, maybe I wasn't clear. I would like to be able to disable the checking of updates via command-line rather than the gui method. Does anyone know how to do that?

---

### Post by Grannun on 2009-08-21
well, you can only update via the command line if you have root access, so controlling permissions is one way since I assume most of the users do not have access to sudo.

---

### Post by kanikilu on 2009-08-21
> **gforster said:**
> OK, maybe I wasn't clear. I would like to be able to disable the checking of updates via command-line rather than the gui method. Does anyone know how to do that?

That setting is configured in the following file:

/etc/apt/apt.conf.d/10periodic

If you want to disable all automatic updates, I think you just want to set all 4 options in there to "0".

You could probably do a search/replace with sed, but my *sed-foo* is weak ;) so the easiest way I can suggest would probably be to just SCP the replacement file over to each machine.

---

### Post by michy99 on 2009-08-21
Maybe if you make /etc/cron.daily/apt non-executable?```
sudo chmod a-x /etc/cron.daily/apt
```

---


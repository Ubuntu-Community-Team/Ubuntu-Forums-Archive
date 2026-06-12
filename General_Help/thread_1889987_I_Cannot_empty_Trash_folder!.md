---
title: "I Cannot empty Trash folder!"
date: 2011-12-02
forum: General Help
---

### Post by uhuru53 on 2011-12-02
Since I installed Ubuntu 11.10 on a 8GB pendrive, I need free disk space, but I Cannot empty Trash folder!

 sudo rm -r /root/.local/share/Trash/files
rm: impossible remove "/root/.local/share/Trash/files/danieluvi/.mozilla/firefox/irndj1vf.default/Cache/7/9A/85658d01": input/output error
rm: impossibile rimuovere "/root/.local/share/Trash/files/danieluvi/.cache/dconf/user": is a directory

---

### Post by gordintoronto on 2011-12-02
Don't use the command line for this! Run the Nautilus file manager.

---

### Post by uhuru53 on 2011-12-03
> **gordintoronto said:**
> Don't use the command line for this! Run the Nautilus file manager.

I did it!

Same result:

```
Error executing  stat of file "/root/.local/share/Trash/files/danieluvi/.mozilla/firefox/irndj1vf.default/Cache/7/9A/85658d01": input/output error
```

Anybody else out there?

Please!

---

### Post by gordintoronto on 2011-12-03
Your flash drive is toast.

---

### Post by bluexrider on 2011-12-03
why are you trying to empty the ROOT trash instead of USER trash?

---

### Post by oldtimer7777 on 2011-12-03
> **bluexrider said:**
> why are you trying to empty the ROOT trash instead of USER trash?

Try bleachbit

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by uhuru53 on 2011-12-04
> **bluexrider said:**
> why are you trying to empty the ROOT trash instead of USER trash?

Simply because it was full of Mb and I need them on a USB 8GB pendrive installation.

---

### Post by uhuru53 on 2011-12-04
> **oldtimer7777 said:**
> Try bleachbit

sudo apt-get install bleachbit
sudo bleachbit

tried, same input-output error.

thanks.

---

### Post by uhuru53 on 2011-12-04
> **gordintoronto said:**
> Your flash drive is toast.

toasted?

so it's impossible delete toasted files?

---

### Post by cap10Ibraim on 2011-12-04
the easiest thing is to boot other machine or OS , plug the usb navigate to that folder and delete it
aslo is moving them issue the same problem message ?
after all , you may trying to access some bad sectors on your flash , can you open these files for read and write ?

---

### Post by bluexrider on 2011-12-04
try sudo apt-get install nautilus-gksu

This will give you permissions to work in nautulus under root (right click folder) run as administrator then delete

---

### Post by fdrake on 2011-12-04
boot from your usb-install and type:
```

gksudo nautilus

```
if it says command not find use for this time sudo instead.
and delete the files you are looking for.

facci sapere se ci sono altri errori! :P

---


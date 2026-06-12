---
title: "Problem with dpkg --configure --a"
date: 2009-09-25
forum: General Help
---

### Post by choallin on 2009-09-25
Hi guy's!

I have installed ubuntu 9.04 new on my laptop. After running the Synaptic i've got an error message, in which i was told to run the "sudo dpkg --configure -a" comand. Of course i've done so...
Unfortunatly i've got an error message in the terminal window too. There message is:
"failed to run depmod
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von Linux -restricted module..."

I know that this is german, so i will translate it:
dpkg: depency problems avoid configuration of linux -restricted modul"
I hope you can help me.

bye
choallin

---

### Post by 3rdalbum on 2009-09-25
I hate this, it can be a real pain to get the package manager working again if it gets interrupted.

Try this:

```
sudo apt-get install -f
```

It might also help if we had the output of this command:

```
sudo dpkg --audit
```

You might need to manually install the packages that are the dependencies of linux-restricted-modules.

---

### Post by lisati on 2009-09-25
There should be only one dash before the "a" as follows:
```
sudo dpkg --configure -a
```
(or was that a typo just in the thread title?)

---

### Post by choallin on 2009-09-26
Thanks for the help. Unfortunatly i don't have inet at my home in the moment, so i couldnt answer earlier.

I've tried the install -f comand. It's not working. I get the message:
errors were encountered while processind:
linux-image-2.6.28.15-generic
linux-restriction-moduls-2.6.28.15-generic
linux-image-generic
linux-restricted-moduls-generic
linux-generic
all of them because of depency problems...

After that i've tried the --audit command and got following message:
The following packages have been unpacked but not yet configured.
They must  be configured using --configure package.
After that the same moduls are listed.

I already tried to use --configure but i get a depency problem.

I hope this will help you, helping me ;-)

btw the --a is just a typo. i meant -a.

so long
choallin

---

### Post by wojox on 2009-09-26
Try and clear the archive:

```
sudo apt-get clean
```

Then:

```
sudo apt-get install -f
```

---

### Post by choallin on 2009-09-27
I've tried the comand. but it is not working.

After that i've tried this: sudo dpkg --configure linux-image-2.6.28-15-generic and got following message:
WARNING: /lib/moduls/2.6.28-15-generic/kernel/drivers/block/cciss.ko is not an elf object
failed to run depmod.
dpkg error processing linux-image-2.6.28-15-generic (--configure)
subprocess post installation script returned error exit status 1

Unfortunatlly i dont know what to do. Is there an opportunity to download the linux image and install it manuell? Or do you have a better idea? 

so long
choallin

---

### Post by choallin on 2009-09-28
*push*
I would really be thankful if anyone has an idea that will work out...

---


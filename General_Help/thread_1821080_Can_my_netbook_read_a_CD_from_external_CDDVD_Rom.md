---
title: "Can my netbook read a CD from external CD/DVD Rom?"
date: 2011-08-08
forum: General Help
---

### Post by Wejdan on 2011-08-08
Hello,

I'm having an issue running a CD via external CD/DVD player (LG portable super multi-drive)

My netbook is:  eee pc 1005P
Im running:  Ubuntu netbook remix 10:10

I've tried the following:
> run
```
sudo mkdir /media/cdrom0; gksudo gedit /etc/fstab

```add this line:
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```Save the new file and reboot, should now be ok.

as I was told on Launchpad..
It was shown in media as ""CDrom0" but couldn't be mounted.. I received, while trying to open or mount the device, > Unable to mount location
mount: special device /dev/scd0 does not exist


Can anyone help.. I really need it to be fixed within 3 days :(
or at least, I need to know if it's not possible so I stop trying

thanks in advance

---

### Post by lkjoel on 2011-08-08
Could you give me the output of this Terminal command?
```
ls /dev | grep cd

```

---

### Post by Wejdan on 2011-08-08
sure
```
pktcdvd
```

---

### Post by lkjoel on 2011-08-08
[FONT=Verdana]Try this in a Terminal window:[/FONT][FONT=monospace][FONT=Verdana]
[/FONT][/FONT]```
[FONT=Verdana]sudo sed -i 's:/dev/scd0 /media/cdrom0 udf,iso9660  user,noauto,exec,utf8 0 0:/dev/pktcdvd /media/cdrom0 udf,iso9660  user,noauto,exec,utf8 0 0:g'[/FONT] [FONT=Verdana]/etc/fstab[/FONT]
```
[FONT=monospace][FONT=Verdana] Then reboot[/FONT]
[/FONT]

---

### Post by Wejdan on 2011-08-09
it's like I'm doing nothing.. no output

---

### Post by Wejdan on 2011-08-09
The CD worked when I first started the system, when I changed it it stopped working I received the same thing as in the main post (unable to mount ...etc)
I restarted, unplugged & then plugged & changed the CD but, none worked

---


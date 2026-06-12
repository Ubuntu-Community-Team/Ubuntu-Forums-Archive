---
title: "Running out of disk space"
date: 2011-05-11
forum: General Help
---

### Post by ggarza78 on 2011-05-11
This is the third time that this happen to me.

When I am working with Virtualbox (with a vdi of 35GB), since I am using Ubuntu 11.04, suddenly I have a message telling me that I am running out of disk space. 
This is weird because when I analyze my disk I have around 80GB not 172GB as what the image says.

Here is the image of disk analyzer
[http://img836.imageshack.us/img836/8721/screenshot003yn.jpg]("https://dl-web.dropbox.com/get/Public/web/screenshot_003.jpeg?w=2e07236e")

df -h
S.ficheros            Tam.  Usado Disp. % Uso Montado en
/dev/sda5              37G  4.4G   31G  13% /
none                  1.9G  700K  1.9G   1% /dev
none                  1.9G  1.2M  1.9G   1% /dev/shm
none                  1.9G  428K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
/dev/sda1             184G  175G   39M 100% /home


I don't know what could be causing this problem.

---

### Post by drs305 on 2011-05-11
The image isn't loading. DUA can be a bit misleading, but I can't tell you specifically without seeing the link.

But it's your /home parition that is full. Empty your trash, and you can review this link to help find out what's filling up your partition:
[HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by ggarza78 on 2011-05-11
I Tried that but did not work.

---

### Post by drs305 on 2011-05-11
> **ggarza78 said:**
> I Tried that but did not work.

Did you go through the guide? For instance, running the commands to see if you have any large files in /home? 

And to confirm, the problem is with your normal OS disk space, and not a problem with the size of the VM you created (that is, it's not that the VM is running out of room)?

---

### Post by ggarza78 on 2011-05-11
/home/ggarza/.xsession-errors.old

92.1 GB

Is it safe to delete it?

---

### Post by drs305 on 2011-05-11
Yes. 

Remember to empty your trash afterwards or it will still take up space. Monitor to see if you continue to get xsession errors or the problem may return.

---

### Post by ggarza78 on 2011-05-11
Thank you, I have to investigate why this file had grown that big.

---


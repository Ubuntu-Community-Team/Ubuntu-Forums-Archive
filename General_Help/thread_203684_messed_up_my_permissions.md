---
title: "messed up my permissions"
date: 2006-06-25
forum: General Help
---

### Post by waldorf on 2006-06-25
So this is the situation.

Ubuntu (my primary OS) is on hda5

I've got FC5 is on hda3.

I'm trying out FC5 and wanted to be able to get to my documents etc on hda5 so while in FC5 I used this <http://www.psychocats.net/ubuntu/mountlinux.html> guide to mount and get permissions to hda5 (Ubuntu).

OOOPS big mistake!

I have full access to hda5 (Ubuntu) from FC5 (hda3), but now I can't boot into Ubuntu on hda5. It hangs with error messages:  

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others.

How do I undo this mess!

---

### Post by Ramses de Norre on 2006-06-25
Can you login to terminal? (ctrl-alt-F1)
If so do this: ```
sudo chown -R username /home/username/* && chmod 644 /home/username/.dmrc 
```
If you can't get to terminal go into recovery and do the same (without the sudo).

---

### Post by waldorf on 2006-06-25
Thanks for the quick reply, but t doesn't seem to be working

I tried it both as

sudo chown -R waldorf /home/waldorf/* && chmod 644 /home/waldorf/.dmrc 

and seperately 

sudo chown -R waldorf /home/waldorf/*
sudo chmod 644 /home/waldorf/.dmrc

---

### Post by Ramses de Norre on 2006-06-25
Maybe try with ```
sudo chown -R waldorf /home/waldorf/
``` thus removing the *, I don't know what could be wrong if that doesn't work either..

---

### Post by waldorf on 2006-06-25
Thanks again.

Okay. now I get this error:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log .... bunch of stuff
/etc/gdm/Xsession: Beginning session setup ...
mkdtemp: private socket dir: Permission denied

any other thoughts.

many many thanks again

---

### Post by waldorf on 2006-06-25
I'm also getting an error that GDM could not write to your authorization file

---

### Post by Ramses de Norre on 2006-06-25
That would be the cause of the errors then, does ```
chmod 644 /home/waldorf/.*authority
``` help?

---

### Post by waldorf on 2006-06-25
Thanks for taking the time, but in the end I've decided to just do a reinstall.

I was too worried that I was just making a bigger mess of things.

Thanks again - greatly appreciated

---


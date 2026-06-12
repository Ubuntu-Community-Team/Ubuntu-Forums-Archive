---
title: "/etc/init.d/samba gone"
date: 2010-05-06
forum: General Help
---

### Post by Wolf-Ekkehard on 2010-05-06
After a Kubuntu upgrade from Karmic to Lucid on a 32 bit i686 my samba script in /etc/init.d/ was gone.  Is that simply a bug or something going wrong during the upgrade, in which case I restore the script from backup, or is there a new way to start/stop/restart... samba in Lucid?  Samba is working just fine after the upgrade BTW, both for print and file sharing over a mixed network.

Any help would be appreciated.

---

### Post by Wolf-Ekkehard on 2010-05-17
I guess this is turning slowly but surely into an ask-only forum.  If I cannot get an expert's attention, could any kind soul who has samba up and running under Lucid please post the result of ```
cat /etc/init.d/samba
```

Thanks in advance

---

### Post by CharlesA on 2010-05-17
It is an upstart job now.

Try this:

```
sudo smbd start && sudo nmbd start
```

---

### Post by Wolf-Ekkehard on 2010-05-18
Thanks! I tried this, but samba didn't re-process the smb.conf file with these commands :-(  Also, I couldn't find the "start" parameter as a valid option in the man pages of neither smbd nor nmbd.  Any other way to make samba re-read its configuration file?

---

### Post by Darkness Des on 2010-05-18
I'm not sure about making samba re-read the configuration file, or why that's happening, but the way to start and/or stop the Samba daemon is 
```
sudo /etc/init.d/smbd start
```or

```
sudo /etc/init.d/smbd stop
```

---

### Post by Wolf-Ekkehard on 2010-05-18
This actually looks like it is restarting the service.  It also spits out a kind tutorial that one may use "restart" to do the same thing. So```
sudo restart smbd && sudo restart nmbd
``` does the trick.  There used to be a "reload" option to the /etc/init.d/samba script, but since restarting the services also works, this is what I'm gonna do.

Again, thanks a bunch guys!!

---


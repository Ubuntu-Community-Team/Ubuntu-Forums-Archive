---
title: "deny host"
date: 2010-08-25
forum: General Help
---

### Post by capo1949 on 2010-08-25
Hi All
I have deny host installed and working on my laptop, running Lucid.

On attempting to install it on my desktop, also running Lucid I get the following message when trying to start the service
graham@graham-desktop:~$ sudo service denyhosts start
[sudo] password for graham: 
starting DenyHosts:    /usr/bin/denyhosts.py --daemon --config=/usr/share/denyhosts/denyhosts.cfg
sh: /usr/bin/denyhosts.py: not found

Its very strange as on the laptop denyhosts.py is not used

Thanks in anticipation

---

### Post by LightningCrash on 2010-08-25
check the file /etc/init.d/denyhosts

There should be a line called DAEMONCTL (line 26 on mine)

mine reads like so:
DAEMONCTL=/usr/share/denyhosts/denyhosts_ctl.py

You might have to change it.
How odd.

---

### Post by capo1949 on 2010-08-25
Hi 
Thanks for your response.
There is no DAEMONCTL mentioned
But these are 
###############################################
#### Edit these to suit your configuration ####
###############################################

DENYHOSTS_BIN = [COLOR="Red"]"/usr/bin/denyhosts.py"[/COLOR]
DENYHOSTS_LOCK = "/var/run/denyhosts.pid"
DENYHOSTS_CFG = "/usr/share/denyhosts/denyhosts.cfg"

What are the entries on your system please and what Ubuntu release are you using

I checked my laptop and the file is completely different there with the DAEMONCTL entry as you listed

It looks as if I have a difernt denyhosts on the desktop? and yet they are both downloaded from Synaptic

---

### Post by capo1949 on 2010-08-25
Hi
I purged the deny hosts with apt-get and then did a search for denyhosts in the file system and found a pile of files still there, which I manually removed.

Reinstalled denyhost with apt-get started the service and it worked.

Conclusion is there was some sort of conflict

Thanks all for your input

---


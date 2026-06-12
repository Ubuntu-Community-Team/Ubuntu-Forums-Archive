---
title: "missing rc.d file"
date: 2010-06-08
forum: General Help
---

### Post by tropdoug on 2010-06-08
I am running Lucid 64bit on my laptop and been trying to install a canon printer driver LBP3200 on it. 

There are some comprehensive tutorials that I have been following and they worked on my desktop. However the last thing I have to do is ```
 sudo update-rc.d ccpd defaults 50
``` which gives me the error
```
 update-rc.d: warning: /etc/init.d/ccpd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/ccpd already exist.
```I checked in /etc and I do not have the rc.d dir! I have rc0.d through to rc6.d and rcS.d dir, but no rc.d one. 

Is this normal? and if so how can I get the correct file to start/stop the ccpd daemon for the printer? 

at the moment the print command brings up the printer icon for about ten seconds and then it disappears and nothing happens. 

Love some help please.

---

### Post by Brandon Williams on 2010-06-09
There is no /etc/rc.d directory on Debian systems.

After running update-rc.d, is there a symlink in /etc/rc2.d/ that points to /etc/init.d/ccpd? If the answer to that question is yes, then are you able to run /etc/init.d/ccpd as root? Go to a root prompt with 'sudo -i' and then run the script with '/etc/init.d/ccpd start'. Does it work? If not, what are the errors?

---

### Post by tropdoug on 2010-06-22
Thanks for that Brandon, I forgot to come back here. I solved it, but I can't remember what I did after I realised the above as well. 

Thats not very good cos now I can't help anyone else that may be facing the same. Hopefully no else is as dumb as I am.

---


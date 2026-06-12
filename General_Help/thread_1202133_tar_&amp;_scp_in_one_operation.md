---
title: "tar &amp; scp in one operation?"
date: 2009-07-01
forum: General Help
---

### Post by gvanto on 2009-07-01
Hi guys I was wondering what the method is for doing all of this in one command:

I have 2 hosts, communicating via ssh. I have a folder on host A, which I want to tar up, and scp to host B.

Is there an easier way to do it (ie. one command line?) than to achieve this than actually 1) creating tar of myFolder, then scp-ing across, then extracting on host B, then removing both tar.gz files on both A and B (since no longer needed) ?

I think I saw it once done but cant remember was ages ago.

Help much appreciated !!!!!!!

g

---

### Post by geirha on 2009-07-01
```
tar cf - folder/ | ssh user@hostB "cd /place/to/extract/; tar xf -"
```

And of course if you want to compress it to save bandwidth, add the z option to the tars.

---

### Post by gvanto on 2009-07-08
AWESOME thank you geirha, wicked command !!!

I love linux ...

:-)

---

### Post by sd@ksu on 2012-07-08
Thanks a lot...

---

### Post by sd@ksu on 2012-07-08
FYI:
This really helped...I had my firewall on and was unable to get ssh work..searched around and found how t odo that:
# enable firewall and allow ssh through it
```
sudo ufw enable
sudo ufw allow ssh 
```

# disable firewall
```
sudo ufw disable 
```

---

### Post by sd@ksu on 2012-07-08
This might help someone:
[https://help.ubuntu.com/11.04/ubuntu-help/net-firewall-ports.html]("https://help.ubuntu.com/11.04/ubuntu-help/net-firewall-ports.html")
and
[https://help.ubuntu.com/11.04/ubuntu-help/net-security.html]("https://help.ubuntu.com/11.04/ubuntu-help/net-security.html")

---

### Post by oldos2er on 2012-07-08
Closed. Please don't bump old threads.

---


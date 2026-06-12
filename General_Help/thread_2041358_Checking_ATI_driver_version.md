---
title: "Checking ATI driver version?"
date: 2012-08-12
forum: General Help
---

### Post by cogset on 2012-08-12
I'd like to find which ATI proprietary driver version I have currently on my system (manually installed),all the commands I know > 

[LIST]
[*]  fglrxinfo
[*]  glxinfo |grep string
[*]  cat /var/log/Xorg.0.log | grep 'Driver Version'
[/LIST]
 report some information,except a mundane version number as 12.6,which is actually what I'm looking for:is there any way to get this information?

---

### Post by papibe on 2012-08-12
Hi cogset.

I'm not familiar with the ATI driver, but you can use the apt tools to see which package version are you running.

For instance, to see my version of the Nvidia driver:
```
apt-cache policy nvidia-current
```
The result would be:
```

nvidia-current:
  Installed: **[COLOR="Red"]195.36.24-0ubuntu1~10.04.3[/COLOR]**
  Candidate: 195.36.24-0ubuntu1~10.04.3
  Version table:
 *** 195.36.24-0ubuntu1~10.04.3 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-updates/restricted Packages
        500 http://mirror.anl.gov/pub/ubuntu/ lucid-security/restricted Packages
        100 /var/lib/dpkg/status
     195.36.15-0ubuntu2 0
        500 http://mirror.anl.gov/pub/ubuntu/ lucid/restricted Packages

```
Hope that helps. Let us know how it goes.
Regards.

---

### Post by cogset on 2012-08-14
Thanks,after trying what I think may be the equivalent  for my graphic card,I'm still not getting the kind of info I'm after,which is a very basic info along the lines of  "Driver version  12.6" or something like that:this may have to do with the fact that I've installed the ATI driver manually following these instructions [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide) and not through Synaptic.

```

fglrx-amdcccle:
  Installed: 2:8.961-0ubuntu1
  Candidate: 2:8.961-0ubuntu1
  Version table:
 *** 2:8.961-0ubuntu1 0
        100 /var/lib/dpkg/status
     2:8.723.1-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Packages
     2:8.723.1-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ lucid/restricted Packages
```

---

### Post by cogset on 2012-09-03
Well it's actually here,as I've just found out : System-->Preferences-->AMD Catalyst Control Center-->Information :oops: no real need to dig around in a terminal ...

---

### Post by ratcheer on 2012-09-03
> **cogset said:**
> Well it's actually here,as I've just found out : System-->Preferences-->AMD Catalyst Control Center-->Information :oops: no real need to dig around in a terminal ...

And you will get a rude surprise the next time you have upgraded the driver. amdcccle will still show you the old driver version; it's a well known bug.

To fix it, you will have to delete file /etc/ati/amdpcsdb *with the X server not running*. You will have to do this every time you upgrade fglrx.

Tim

---

### Post by cogset on 2012-09-05
I spoke too soon ;) apparently...thanks for pointing out this.
So this has to be done in a console,and a new file is generated at the next reboot in normal mode?

---

### Post by ratcheer on 2012-09-05
> **cogset said:**
> I spoke too soon ;) apparently...thanks for pointing out this.
So this has to be done in a console,and a new file is generated at the next reboot in normal mode?

Yes.

Tim

---


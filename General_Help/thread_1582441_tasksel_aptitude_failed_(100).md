---
title: "tasksel aptitude failed (100)"
date: 2010-09-26
forum: General Help
---

### Post by psycho5 on 2010-09-26
hi, whenever i try to install anything from tasksel, it gives me that error... aptitude failed (100) what does that mean?

---

### Post by andrewthomas on 2010-09-26
could you post the output of a tasksel operation that failed within  code tags?

---

### Post by psycho5 on 2010-09-27
```

sudo tasksel
[sudo] password for oj: 
xserver-xorg					install
tasksel: aptitude failed (100)
oj@oj-desktop:~/Downloads$

```

---

### Post by guppydas on 2010-10-20
I get the same error. 

> xserver-xorg                    install
tasksel: aptitude failed (100)

---

### Post by AceRoom on 2011-01-30
Got the same error. Found a solution at the following site for this error.
[http://linuxandfriends.com/2009/12/09/how-to-install-lamp-server-in-ubuntu-linux/](http://linuxandfriends.com/2009/12/09/how-to-install-lamp-server-in-ubuntu-linux/)


```
sudo apt-get update
sudo tasksel
```

Working for me :)

---

### Post by earlf on 2011-03-30
I followed the above advice and ```
sudo apt-get update
``` then ```
sudo tasksel
```tasksel started up and I was able to select the lamp option, but hitting return showed the install process bar and then quit.

Strangely I recieved the same ```
tasksel: aptitude failed (100)

```I also tried the similar update of packages from[ this thread.]("http://ubuntuforums.org/showthread.php?t=600429")

What fixed it for me was trying ```
sudo tasksel lamp-server
```Most probably tried this method, so don't worry about originality. I posted this info here to help anyone else running into similar issues. 

I'm not sure what causes this though. Could it be that tasksel's package information for the LAMP option is out of date?

---

### Post by shvahabi on 2011-06-03
Hi,
I encountered this error message when trying to install lamp-server using
```
sudo tasksel install lamp-server
```
Then I just used the following:
```
sudo apt-get update
```
and repeat:
```
sudo tasksel install lamp-server
```
thanks for your help buddies!

---

### Post by Nilesh_85 on 2011-07-03
Hi 
I have just read the forum and its really usefull 
100% working 

thanks a lot

---

### Post by Libety on 2011-11-22
I'm still running into the same problem,

I have tried different ways, including all mentioned above...

---

### Post by fritzah on 2012-10-10
Old thread but make sure you can resolve names. I was missing a nameserver in my resolv.conf.

---


---
title: "Cannot remove package kdm"
date: 2011-04-04
forum: General Help
---

### Post by user1397 on 2011-04-04
So I had installed some kde app a while ago which I didn't want anymore so I uninstalled it and noticed that I didn't need the million kde dependencies that program had required.  So I uninstalled all those, and everything went fine except for kdm which gives me the following error:

```
$ sudo apt-get purge kdm
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kdm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 129607 files and directories currently installed.)
Removing kdm ...
Purging configuration files for kdm ...
rm: cannot remove `/etc/init/kdm.conf': No such file or directory
dpkg: error processing kdm (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 kdm
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I was able to autoremove it, just not purge it (removing the config files left over).

Any ideas?

---

### Post by TeoBigusGeekus on 2011-04-04
Well, if it's problem is that it can't find the /etc/init/kdm.conf file, create an empty one yourself
```
sudo cat /etc/init/kdm.conf
```
and try again.

---

### Post by tredegar on 2011-04-04
> sudo cat /etc/init/kdm.conf
A typo, I think you mean **sudo [COLOR="Red"]touch[/COLOR] /etc/init/kdm.conf**
Best wishes.

---

### Post by TeoBigusGeekus on 2011-04-04
> **tredegar said:**
> A typo, I think you mean **sudo [COLOR="Red"]touch[/COLOR] /etc/init/kdm.conf**
Best wishes.

No, it will work with cat as well.
If sudo wasn't involved, you could even do
```
>/etc/init/kdm.conf
```

---

### Post by user1397 on 2011-04-04
I'm still getting the exact same error even after creating the empty file...hmm

I notice that when I run apt-get purge it does remove the newly created empty file /etc/init/kdm.conf that i made, but it still says the file cannot be found...

---

### Post by TeoBigusGeekus on 2011-04-04
Are you sure the file was created?

---

### Post by gmargo on 2011-04-04
Here's a hack to get around that error:  

Edit the file **/var/lib/dpkg/info/kdm.postrm**.

Scroll down to about line 38 and comment out this section:
```

if [ "$1" = "purge" ] ; then
        rm /etc/init/kdm.conf || exit $?
fi

```Then try the purge again.

---

### Post by user1397 on 2011-04-04
> **TeoBigusGeekus said:**
> Are you sure the file was created?Yea I double checked to see if the file was created, it was, but to no avail.

> **gmargo said:**
> Here's a hack to get around that error:  

Edit the file **/var/lib/dpkg/info/kdm.postrm**.

Scroll down to about line 38 and comment out this section:
```

if [ "$1" = "purge" ] ; then
        rm /etc/init/kdm.conf || exit $?
fi

```Then try the purge again.This worked perfectly, thank you.

---


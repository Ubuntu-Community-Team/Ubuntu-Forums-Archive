---
title: "Can't do these commands."
date: 2012-07-11
forum: General Help
---

### Post by Napoleon Hill on 2012-07-11
So I managed to get the touchpad working properly by following instructions in the ASUS subforum here.

But now I've run in to a general problem. I can't use these commands.

gzip -d asus-wmi-dkms_0.2_all.deb.gz sudo apt-get install dkms sudo dpkg -i asus-wmi-dkms_0.2_all.debhttp://ubuntuforums.org/showpost.php?p=12057336&postcount=49

I attached what I got. What am I doing wrong?

---

### Post by codemaniac on 2012-07-11
Are you sure the file asus-wmi-dkms_0.2_all.deb.gz exists in the directory from where you are running the gunzip command .

please check .

```
ls -l asus-wmi-dkms_0.2_all.deb.gz
```

---

### Post by Napoleon Hill on 2012-07-11
> **codemaniac said:**
> Are you sure the file asus-wmi-dkms_0.2_all.deb.gz exists in the directory from where you are running the gunzip command .

please check .

```
ls -l asus-wmi-dkms_0.2_all.deb.gz
```

It says the file or catalog doesn't exist.

---

### Post by codemaniac on 2012-07-11
> **Napoleon Hill said:**
> It says the file or catalog doesn't exist.

Hi ,

You need to switch to the directory where the file is residing and then fire up gunzip command to uncompress it .

If you are not sure where you have placed the zipped file , please do an search like below .

```
find $HOME -name "asus-wmi-dkms_0.2_all.deb.gz" -print 
```

---


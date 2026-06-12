---
title: "Synaptic and Terminal Errors When Trying To Install"
date: 2009-07-03
forum: General Help
---

### Post by BlazeFire247 on 2009-07-03
Hi there! I keep getting an error when opening Synaptic Package Manager. It says:

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Then, when I try to do sudo apt-get adobe-flashplugin or sudo aptitude adobe-flashplugin, it gives me

> E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it. 

Help would be nice, thanks!

---

### Post by synapsys on 2009-07-03
```
sudo apt-get remove adobe-flashplugin
sudo apt-get purge adobe-flashplugin
sudo apt-get install adobe-flashplugin
```

---

### Post by BlazeFire247 on 2009-07-03
I tried that and:

```
niteangel@ubuntu:~$ sudo apt-get remove adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
niteangel@ubuntu:~$ sudo apt-get purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
niteangel@ubuntu:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
niteangel@ubuntu:~$ 

```

---

### Post by kerry_s on 2009-07-03
```
sudo apt-get remove --purge adobe-flashplugin
```

---

### Post by synapsys on 2009-07-03
> HAH! Fixed it!

I had a look at the errors, namely this line:
 ```

     postinst called with argument `abort-upgrade' 
```This looked intriguing to me. So I ran the command     ```

~$ locate adobe-flashplugin | grep postinst 
/var/lib/dpkg/info/adobe-flashplugin.postinst
~$ 
```Just for the heck of it, I removed that file (backed it up in my home directory.) After I did that, I was able to use apt normally again, and flash was auto-magically reinstalled when I tested apt by installing abiword.[http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/](http://www.linuxquestions.org/questions/debian-26/sid-adobe-flasplugin-is-reinstall-required-but-apt-cant-find-archive-for-it-727572/)

Google is your friend

[http://www.google.com/search?q=The+package+adobe-flashplugin+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a]("http://www.google.com/search?q=The+package+adobe-flashplugin+needs+to+be+reinstalled%2C+but+I+can%27t+find+an+archive+for+it.&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

---

### Post by BlazeFire247 on 2009-07-03
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```It kept saying that after I entered the commands then tried to install Opera to test it.

EDIT: Tried it again, still same error: E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by synapsys on 2009-07-04
> **BlazeFire247 said:**
> ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

That means you have a package manager open. Close Synaptic.

Did you delete the file it told you to?

---

### Post by BlazeFire247 on 2009-07-04
Yes. Synaptic still shows the error message, too.

---

### Post by BlazeFire247 on 2009-07-04
Ok, now it shows
```
niteangel@ubuntu:~$  locate adobe-flashplugin | grep postinst 
/var/lib/dpkg/info/adobe-flashplugin.postinst
niteangel@ubuntu:~$ /var/lib/dpkg/info/adobe-flashplugin.postinst
postinst called with unknown argument `'

```

---

### Post by Soul-Sing on 2009-07-04
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```
```
sudo apt-get update
```
```
sudo apt-get remove -y --purge flashplugin-nonfree
```
or:

```
sudo apt-get remove -y --purge adobe-flashplugin.postinst
```

---

### Post by BlazeFire247 on 2009-07-06
Those worked, but the last two didn't. It just says that the package needs to be reinstalled. Oh, and sorry for the late reply.

---

### Post by Soul-Sing on 2009-07-06
BlazeFire247 is it OK now?

---

### Post by BlazeFire247 on 2009-07-08
Not really... I try to install different kinds of things and it still gives me the error message. Thanks for all your help, I appreciate it!

---

### Post by BlazeFire247 on 2009-07-15
Hey, just wanted you all to know that it's fixed now. Thanks for all your help, guys!!

---


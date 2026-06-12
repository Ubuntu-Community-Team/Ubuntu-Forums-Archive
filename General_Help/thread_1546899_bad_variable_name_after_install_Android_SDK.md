---
title: "bad variable name after install Android SDK"
date: 2010-08-06
forum: General Help
---

### Post by gishak on 2010-08-06
Hi everyone, I have Ubuntu 10, and after I installed Android SDK some applications doesn't work anymore (Picasa, Teamviewer), I have reviewed the problems related to android environment variables, but the case is that I can run android in the command tool and it works, I have changed the bashrc files setting the path to:
export PATH=$PATH:/etc/android/android-sdk-linux_86/tools
in the file:
/etc/bash.bashrc

If I run picasa or teamviewer from command tool the displayed error is:
[B]
gishac@ubuntu:~$ cd /opt/google/picasa/3.0/bin
gishac@ubuntu:/opt/google/picasa/3.0/bin$ picasa
[COLOR=Red]export: 351: /etc/android/android-sdk-linux_86/:/etc/android/android-sdk-linux_86/tools: bad variable name
export: 351: /etc/android/android-sdk-linux_86/:/etc/android/android-sdk-linux_86/tools: bad variable name
export: 351: /etc/android/android-sdk-linux_86/:/etc/android/android-sdk-linux_86/tools: bad variable name[/COLOR]
[/B]
Any idea how to fix this?

---

### Post by gishak on 2010-08-07
Any help???

---

### Post by arm-c on 2010-08-20
I had a problem caused by the Android SDK.

Suddenly, for no reason, from a terminal I could run no commands.  After looking around, I noticed the following in my ~/.bashrc file.

```
export PATH=$(PATH:/home/arick/Data/android-sdk-linux_86/tools)
```

I suspect that the format of that export PATH statement had something to do with it, so I modified the line to the following:

```
export PATH=/home/arick/Data/android-sdk-linux_86/tools:"${PATH}"
```

I now have my path environment back.... not sure if that will help the above...

---


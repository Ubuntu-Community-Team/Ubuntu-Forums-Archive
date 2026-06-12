---
title: "teminal , unable to locate package."
date: 2011-03-12
forum: General Help
---

### Post by purezwater on 2011-03-12
Unable to locate package pam-face-authentication

Guys , i want to install the ubuntu face recognize software ,but i get file unable to locate,why ? is my computer problem or what ? i follow the instrument in following link :popcorn::popcorn::confused::confused:.[http://pam-face-authentication.org/downloads.php](http://pam-face-authentication.org/downloads.php)

---

### Post by cap10Ibraim on 2011-03-12
what was the command that caused this error ?

---

### Post by bapoumba on 2011-03-12
Please check the repo has been added:
```
ls -l /etc/apt/sources.list.d/

```
Then update
```
sudo apt-get update
```
and install your package.

---

### Post by purezwater on 2011-03-14
sir....this is what i get ...

```
user@ubuntu:~$ ls -l /etc/apt/sources.list.d/
total 32
-rw-r--r-- 1 root root 148 2011-03-13 01:59 antonio_chiurazzi-ppa-maverick.list
-rw-r--r-- 1 root root 148 2011-03-13 01:59 antonio_chiurazzi-ppa-maverick.list.save
-rw-r--r-- 1 root root 176 2011-03-13 01:59 google-chrome.list
-rw-r--r-- 1 root root 176 2011-03-13 01:59 google-chrome.list.save
-rw-r--r-- 1 root root 144 2011-03-13 01:59 jd-team-jdownloader-maverick.list
-rw-r--r-- 1 root root 144 2011-03-13 01:59 jd-team-jdownloader-maverick.list.save
-rw-r--r-- 1 root root 132 2011-03-13 01:59 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 132 2011-03-13 01:59 tualatrix-ppa-maverick.list.save
user@ubuntu:~$ sudo apt-get update
[sudo] password for user: 
E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
user@ubuntu:~$ 

```

---

### Post by doas777 on 2011-03-14
you have a problem in your [FONT=monospace]tualatrix ppa .list file. what does it contain?
[/FONT]```
cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

---

### Post by purezwater on 2011-03-14
```
user@ubuntu:~$ cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main #Ubuntu Tweak Stable Source
.net/tualatrix/ppa/ubuntu maverick main
user@ubuntu:~$ 

```

what to do ...TT....:confused::confused:
i cant install that and i get this all code .when i type in ```
sudo add-apt-repository ppa:antonio.chiurazzi
sudo apt-get update
sudo apt-get install pam-face-authentication
```

and i get this while install...

```
user@ubuntu:~$ sudo add-apt-repository ppa:antonio.chiurazzi
[sudo] password for user: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 230CDF8AFAB2832CFEF2AD4D8E24BF68FCE0C058
gpg: requesting key FCE0C058 from hkp server keyserver.ubuntu.com
gpg: key FCE0C058: "Launchpad PPA for steveacab" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
user@ubuntu:~$ sudo apt-get update
E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
user@ubuntu:~$ sudo apt-get install pam-face-authentication
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package pam-face-authentication
user@ubuntu:~$ 


```

---

### Post by doas777 on 2011-03-14
try adding this to the beginning of line two:
```
deb-src http://ppa.launchpad
```
just before the ".net/..."
looks like the first part got cut off somehow

---

### Post by purezwater on 2011-03-14
You means like that ?


sudo add-apt-repository ppa:antonio.chiurazzi
[COLOR="Red"]deb-src [http://ppa.launchpad](http://ppa.launchpad)[/COLOR]
sudo apt-get update
sudo apt-get install pam-face-authentication
deb-src: command not found


i got this ....:sad::sad:

---

### Post by purezwater on 2011-03-14
sir ...or you give me a full code?..cause i am still a newbie in ubuntu ...thx for you kindly help ..

---

### Post by doas777 on 2011-03-14
> **purezwater said:**
> You means like that ?


sudo add-apt-repository ppa:antonio.chiurazzi
[COLOR=Red]deb-src [http://ppa.launchpad](http://ppa.launchpad)[/COLOR]
sudo apt-get update
sudo apt-get install pam-face-authentication
deb-src: command not found


i got this ....:sad::sad:

ok, the blow by blow:
```

gksu gedit /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```
this will open up a text editor showing the file.
on line two where it starts with ".net/tualatrix/ppa/ubuntu maverick main"
paste in the token I posted. your second line should now look like:
```
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main


```notice how the url is whole now? 

save the file, and run 
```
sudo apt-get update
```then try your install again

---

### Post by purezwater on 2011-03-14
i change to this ..```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu maverick main #Ubuntu Tweak Stable Source
deb-src http://ppa.launchpad
.net/tualatrix/ppa/ubuntu maverick main
```

and i get this.
```

user@ubuntu:~$ sudo apt-get update
[sudo] password for user: 
E: Malformed line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list (dist)
E: The list of sources could not be read.

```

---

### Post by doas777 on 2011-03-14
get rid of the line break. there shoudl be only two lines in the file, not 3.
"http://ppa.launchpad.net/tualatrix/ppa/ubuntu"
is one url.

---

### Post by purezwater on 2011-03-14
sir ..i am so stupid ...can you just show me the code and let me copy and paste in the PAD and save...please sir .:confused:

---

### Post by purezwater on 2011-03-14
problem solve !!!...thx :popcorn::popcorn::popcorn:

---


---
title: "Synaptic shows errors"
date: 2011-04-11
forum: General Help
---

### Post by telovin on 2011-04-11
Hi,
My synaptic package manager was showing errors when tried to upgrade or remove packages from it.I was trying to remove linux images from it. So it showed th error.
Not all packages were removed successfully or something like that. 
Now I was trying to reinstall grub customizer and it showed the following error
"E: Type 'ielrichter2007/grub-customizer/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

When click on close to the error window, The whole synaptic closes. No idea what to do.A few hours ago, I had unchecked some packages from software sources. But when I tried to re add it I am unable to.
I am using natty narwhal.
Not only with grub customizer, I was trying to remove firefox, still I got errors. Guess my synaptic is not working properly.

---

### Post by plucky on 2011-04-11
> "E: Type 'ielrichter2007/grub-customizer/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

The error is pointing to the **.list** file in **/etc/apt/sources.list.d/ directory**.

Open a terminal and ```
cat /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
``` will show you what the problem is.

Either correct it or delete the file then run ```
sudo apt-get update
``` and post the output.

Good Luck

---

### Post by telovin on 2011-04-16
Plucky but I am using natty, so is it ok to get maverick.list?
I typed the command , got the following result.

```
vinu@vinu-desktop:~$ cat /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
deb http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu maverick main # disabled on upgrade to maverick
ielrichter2007/grub-customizer/ubuntu maverick main
```

My update manager says

```
Could not initialize package information.

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ielrichter2007/grub-customizer/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list'
```

I had disabled all maverick updates since I am using natty. Now when I open software centre to enable it, My software centre wont open. When clicks on software centre, NOTHING HAPPENS.

I dont know how to enable it again. Still I typed sudo apt-get update and it gave the following result.

[COLOR="Blue"]E: Type 'ielrichter2007/grub-customizer/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
E: The list of sources could not be read.[/COLOR]

---

### Post by Yellow Pasque on 2011-04-16
```
sudo rm /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
sudo apt-add-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
```

---

### Post by telovin on 2011-04-16
Hi got the following results


```
vinu@vinu-desktop:~$ sudo rm /etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list
rm: cannot remove `/etc/apt/sources.list.d/danielrichter2007-grub-customizer-maverick.list': No such file or directory
vinu@vinu-desktop:~$ sudo apt-add-repository ppa:danielrichter2007/grub-customizer
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 59DAD276B942642B1BBD0EACA8AA1FAA3F055C03
gpg: requesting key 3F055C03 from hkp server keyserver.ubuntu.com
gpg: key 3F055C03: "Launchpad PPA for Daniel Richter" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
vinu@vinu-desktop:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ maverick/main Translation-en_IN
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_IN
Get:4 http://ppa.launchpad.net maverick Release [9,784B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
Get:5 http://ppa.launchpad.net maverick Release [9,775B]
Get:6 http://ppa.launchpad.net maverick/main Sources [584B]
Get:7 http://ppa.launchpad.net maverick/main i386 Packages [794B]
Get:8 http://ppa.launchpad.net maverick/main Sources [18.2kB]
Get:9 http://ppa.launchpad.net maverick/main i386 Packages [15.4kB]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN
Get:10 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_IN   
Get:11 http://dl.google.com stable Release [1,347B]                            
Get:12 http://dl.google.com stable Release [1,347B]                            
Get:13 http://dl.google.com stable/main i386 Packages [1,096B]                 
Get:14 http://dl.google.com stable/main i386 Packages [737B]                   
Fetched 60.0kB in 8s (7,395B/s)                                                
Reading package lists... Done
```

I don't see grub customizer under system tools now also.

---

### Post by Yellow Pasque on 2011-04-16
> Plucky but I am using natty, 
All your sources are maverick..

---

### Post by telovin on 2011-04-16
Hi Temujin,
So does it cause a clash? Do I have to wait till the official release of natty? or is it ok to continue with maverick sources?

---

### Post by oldos2er on 2011-04-16
> **telovin said:**
> So does it cause a clash? 

Very much so.

---

### Post by telovin on 2011-04-16
Hi oldos2er,
I am able to install grub customizer and resolved the problem. Now I tried removing firefox from synaptic, it got removed without any errors. Guess Now synaptic is ok. And for the crashes I guess I have to wait till the official release date of natty :)

---


---
title: "info util"
date: 2009-08-13
forum: General Help
---

### Post by acutshall1 on 2009-08-13
Is there a software util that runs on new ubuntu that will tell me info about my software versions. Such info such as ubuntu version 32 or 64 bit; flash version etc. i.e i go to adobe to update flash and i do not know which version to download becuase I do not what version I am running.
thx

---

### Post by credobyte on 2009-08-13
Use -v argument in command line :)

```
dainis@ubuntu:~$ firefox -v
Mozilla Firefox 3.0.13, Copyright (c) 1998 - 2009 mozilla.org
dainis@ubuntu:~$ konversation -v
Qt: 3.3.8b
KDE: 3.5.10
Konversation: 1.1 (Debian 1.1-1ubuntu2)
dainis@ubuntu:~$ skype -v
Skype 2.0.0.72
Copyright (c) 2004-2007, Skype Limited
```

---

### Post by acutshall1 on 2009-08-13
> **credobyte said:**
> Use -v argument in command line :)

```
dainis@ubuntu:~$ firefox -v
Mozilla Firefox 3.0.13, Copyright (c) 1998 - 2009 mozilla.org
dainis@ubuntu:~$ konversation -v
Qt: 3.3.8b
KDE: 3.5.10
Konversation: 1.1 (Debian 1.1-1ubuntu2)
dainis@ubuntu:~$ skype -v
Skype 2.0.0.72
Copyright (c) 2004-2007, Skype Limited
```


thx!!!!!

---

### Post by acutshall1 on 2009-08-13
> **credobyte said:**
> Use -v argument in command line :)

```
dainis@ubuntu:~$ firefox -v
Mozilla Firefox 3.0.13, Copyright (c) 1998 - 2009 mozilla.org
dainis@ubuntu:~$ konversation -v
Qt: 3.3.8b
KDE: 3.5.10
Konversation: 1.1 (Debian 1.1-1ubuntu2)
dainis@ubuntu:~$ skype -v
Skype 2.0.0.72
Copyright (c) 2004-2007, Skype Limited
```


spoke too soon it tells me command not found

---

### Post by credobyte on 2009-08-13
> **acutshall1 said:**
> spoke too soon it tells me command not found
 
Which one ? -v argument will always be accepted, except, for some applications it's being used for something else, not printing it's version ( tough, it'll never show "command not found" ).

---

### Post by acutshall1 on 2009-08-14
> **credobyte said:**
> Which one ? -v argument will always be accepted, except, for some applications it's being used for something else, not printing it's version ( tough, it'll never show "command not found" ).


maybe I am doing something wrong


acutshall@mediabox1:~$ boxee _v
bash: boxee: command not found
acutshall@mediabox1:~$ boxee-v
bash: boxee-v: command not found
acutshall@mediabox1:~$ boxee -v
bash: boxee: command not found
acutshall@mediabox1:~$ adobe -V
bash: adobe: command not found
acutshall@mediabox1:~$ adobeflash -v
bash: adobeflash: command not found
acutshall@mediabox1:~$

---

### Post by Volt9000 on 2009-08-14
The commands you are typing are invalid.
What program are you trying to determine the version of?

---

### Post by soapBAR2 on 2009-08-14
> **acutshall1 said:**
> Is there a software util that runs on new ubuntu that will tell me info about my software versions. Such info such as ubuntu version 32 or 64 bit; flash version etc. i.e i go to adobe to update flash and i do not know which version to download becuase I do not what version I am running.
thx

```
uname -a
```

will tell you information about your computer. Here's mine:

> Linux Desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 01:19:55 UTC 2009 x86_64 GNU/Linux

which is
<Kernel name> <Computer Name> <Kernel release> <Kernel version>  <Operating system> 

Although if you just want flash, use the repository. Enable "restricted" repositories from synaptic/aptitude, and then install flashplugin-installer either by searching in synaptic/aptitude, or by exiting synaptic/aptitude and executing

```
sudo apt-get install flashplugin-installer
```

---

### Post by acutshall1 on 2009-08-15
> **Volt9000 said:**
> The commands you are typing are invalid.
What program are you trying to determine the version of?


I was trying to get the utility or general command for viewing installed versions of app/drivers on my computer, so  I can determine if the web offers a newer version than what I have installed.


i.e

in windows you can view what driver you are running by properties of that device or in mac more info about an app

---

### Post by acutshall1 on 2009-08-15
> **credobyte said:**
> Which one ? -v argument will always be accepted, except, for some applications it's being used for something else, not printing it's version ( tough, it'll never show "command not found" ).

I was just testing out your command on various apps to see if I could get it to work. i.e boxee

---

### Post by credobyte on 2009-08-15
> **acutshall1 said:**
> I was just testing out your command on various apps to see if I could get it to work. i.e boxee

Not all applications can be launched from terminal, which means .. you can't get their version that easy.

Try:
```
sudo aptitude show flashplugin-nonfree
```You should see the description, version, libraries, etc. ;)

---


---
title: "add-apt-repository doesn't work?"
date: 2012-09-03
forum: General Help
---

### Post by Zukaro on 2012-09-03
The command "sudo add-apt-repository ppa:" doesn't work, when I try it it says "add-apt-repository: command not found".  How do I add ppa's?  I'm using Ubuntu Server 12.04.1 (so I need to do it through the terminal).

---

### Post by oldos2er on 2012-09-03
It's ```
apt-add-repository ...
```

---

### Post by Zukaro on 2012-09-03
> **oldos2er said:**
> It's ```
apt-add-repository ...
```

When I try it that way it says: "apt-add-repository: command not found"

---

### Post by oldos2er on 2012-09-03
Which version of Ubuntu are you using?

---

### Post by deadflowr on 2012-09-03
What's the repository?

```
sudo add-apt-repository name of repo
```

the repo will probably be ppa:name_of_repo/ppa, or something similar.

---

### Post by Zukaro on 2012-09-03
I'm using Ubuntu Server 12.04.1
The repository is "ppa:ubuntu-audio-dev/ppa"

---

### Post by oldos2er on 2012-09-03
I don't think the server version installs python-software-properties (the package that contains the apt-add-repository command) by default, but you should be able to install it. Or you could manually edit your sources.list file.

---

### Post by Zukaro on 2012-09-03
How would I be able to install it?  Trying to install "repository" just tells me it can't find it and doesn't say any packages it's in.

---

### Post by oldos2er on 2012-09-03
```
sudo apt-get update && sudo apt-get install python-software-properties
```

---

### Post by Zukaro on 2012-09-03
> **oldos2er said:**
> ```
sudo apt-get update && sudo apt-get install python-software-properties
```


Thanks; it's working now.

---

### Post by oldos2er on 2012-09-03
Welcome.

---

### Post by bmwman on 2013-01-03
I am having the same issue on Ubuntu 12.10 Minimal. I did install ```
sudo apt-get update && sudo apt-get install python-software-properties
``` Even rebooted couple times after the install. When I try to add a repository: ```
sudo apt-add-repository pap:team-xbmc/unstable 
``` it still gives me "command not found error". Any other ideas? Thanks.

---

### Post by ibjsb4 on 2013-01-03
> **bmwman said:**
> ```
sudo apt-add-repository pap:team-xbmc/unstable 
``` it still gives me "command not found error". Any other ideas? Thanks.

try

```
sudo apt-add-repository [COLOR=Red]ppa[/COLOR]:team-xbmc/unstable
```

---

### Post by bmwman on 2013-01-03
Sorry for the typo, i did type it right in terminal. Even if I run "sudo apt-add-repository" by itself, I get the "command not found".

---

### Post by ibjsb4 on 2013-01-03
> **bmwman said:**
> Sorry for the typo, i did type it right in terminal. Even if I run "sudo apt-add-repository" by itself, I get the "command not found".

I too am working off a 12o4 minimal install.  In my case python-software-properties was already installed.  I always install synaptic-package-manager at the start of a fresh build and suspect this is why I already had it.  Are you running a GUI?

---

### Post by bmwman on 2013-01-03
No GUI, only command line. I want to use the machine for XBMC and installed only Minimal plus SSH server. I thought the apt-add-repository is part of the python-software-properties package and should work. Not sure if something else is needed...

---

### Post by ibjsb4 on 2013-01-03
Ok, just tried installing xbmc/unstable on a vanilla copy of 12o4 minimal (vBox) and got the command not found.

Installed python-software-properties and it worked.

Maybe try reinstalling python-software-properties.

---

### Post by bmwman on 2013-01-03
No dice. I wonder if this is a bug with 12.10 64bit. I just did a format/clean install, installed only core and SSH server. Then installed python-software-properties and still "command not found" when trying to add the repo. I guess I can try 12.04 instead and see what happens

---

### Post by ibjsb4 on 2013-01-03
I just tried it again on vanilla 12o4 server edition to see if there was a difference.  And again it worked.  I am running 32 bit.

---

### Post by ibjsb4 on 2013-01-03
software-properties-common ??

[https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/1086800](https://bugs.launchpad.net/ubuntu/+source/command-not-found/+bug/1086800)

---

### Post by bmwman on 2013-01-03
I just installed 12.04 64bit minimal and it works fine after installing the python-software-properties. I'll stick with that for now, thanks :)

---

### Post by ibjsb4 on 2013-01-03
Better an LTS, welcome  :)

---

### Post by Asitaka on 2013-01-26
This is not solved for me on a 12.04 LTS 64 bit server. Both software-properties-common and python-software-properties are installed but add-apt is not working.

---

### Post by elgordodude on 2013-01-26
For future reference it's better to start a new thread than try to resurrect one that's weeks old and marked solved. 

Anyway one inelegant but sure to work solution not mentioned is to use a cli text editor like vim nano or emacs```
sudo vim /etc/apt/sources.list
``` then scroll to the bottom and add the following 

## new repository comment
deb [http://mynewrepository.org](http://mynewrepository.org)

note that these editors all obey their own quirky little rules, they're not like gedit. If you're not familiar with them you'll want a tutorial site nearby for reference.

---


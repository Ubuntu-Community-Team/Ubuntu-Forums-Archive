---
title: "Sources.list Error"
date: 2011-05-06
forum: General Help
---

### Post by Cagatay on 2011-05-06
Hi All Again me =) , first of all i want to congratulate for your job =) and Sorry my bad english =)

i want to backtrack app into my ubuntu but whatever i tryed couldn't it.

first use gnome-terminal command after that i am using sudo 

echo &#8220;deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsaucen microverse macroverse restricted universe multiverse&#8221; > /etc/apt/sources.list

but my ubuntu says that " bash: /etc/apt/sources.list: Access denied ".

please help me. Thank you...

---

### Post by Grenage on 2011-05-06
You'd need sudo rights, so prefix your command with *sudo*.

Can you not add the source through Update Manager?  It will cut down on the chances of bad data being entered.

P.S: It's probably also worth mentioning that a single '>' will *overwrite* a file with the input contents, whereas a '>>' will *append*.

---

### Post by dino99 on 2011-05-06
the command line is:

sudo gedit /etc/apt/sources.list

and its a working one for natty (adapt if you dont want natty, just copy/paste the lines below)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe

---

### Post by ajgreeny on 2011-05-06
> **dino99 said:**
> the command line is:

sudo gedit /etc/apt/sources.list

and its a working one for natty (adapt if you dont want natty, just copy/paste the lines below)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe
To be strictly correct the command is ```
**gksudo** gedit /etc/apt/sources.list
```You should never use sudo with a GUI application, though it does not normally cause the problems it can with other apps, when used for gedit.

See **Root-sudo** link in my signature for all the details about this.

---


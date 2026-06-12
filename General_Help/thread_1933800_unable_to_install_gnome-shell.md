---
title: "unable to install gnome-shell"
date: 2012-03-01
forum: General Help
---

### Post by khaj_vah on 2012-03-01
Hello people,

I have a problem with installing gnome-shell. After i run "sudo apt-get install gnome-shell", it says this

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libgnome-keyring0 (>= 3.2.2-2~) but 3.2.0-0ubuntu1 is to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
               Recommends: gnome-contacts but it is not going to be installed
E: Unable to correct problems, you have held broken packages."

I tried to manully update  libgnome-keyring0, but it says that i already have the latest version. 

Thanks for spending time on me :)

---

### Post by pinguinhood on 2012-03-01
Which version of Ubuntu are you using?
From what I know, in Ubuntu 11.10 if you log-off and choose gnome as session type you already have gnome-shell.

---

### Post by khaj_vah on 2012-03-01
Yes, but, first i need to install gnome-shell to be able to choose it from startup

---

### Post by pinguinhood on 2012-03-01
What happens if you try to install it from software centre?
I found someone with your problem [here]("https://answers.launchpad.net/ubuntu/+source/gnome-shell/+question/187913")
Did you try the command below?
sudo apt-get install -f
sudo apt-get update

---

### Post by chehsunliu on 2012-06-05
> **pinguinhood said:**
> What happens if you try to install it from software centre?
I found someone with your problem [here]("https://answers.launchpad.net/ubuntu/+source/gnome-shell/+question/187913")
Did you try the command below?
sudo apt-get install -f
sudo apt-get update

I got the same problem this morning after allowing "partially upgrade" from the update manager. The result is that the gnome-shell is removed... I've tried these two commands but not work. The error is
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libgcr-3-1 (>= 3.4.0) but 3.2.2-2ubuntu4 is to be installed
               Depends: gir1.2-gcr-3 but it is not installable
               Recommends: gnome-contacts but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Need help:(

---

### Post by chehsunliu on 2012-06-05
```

sudo apt-get update
sudo apt-get install python-software-properties
sudo apt-add-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell

```

This commands work for me!!

---

### Post by wilee-nilee on 2012-06-05
Never do a partial upgrade.

---

### Post by deadflowr on 2012-06-05
> **wilee-nilee said:**
> Never do a partial upgrade.

Exactly. Here's a good read on why:

[http://ubuntuforums.org/showthread.php?t=1859240&highlight=offer+partial+upgrade]("http://ubuntuforums.org/showthread.php?t=1859240&highlight=offer+partial+upgrade")

as for installing gnome-shell I always run

```
sudo apt-get install gnome-tweak-tool
```

Which installs the advanced settings program for gnome along with the gnome desktops. I've run this on every pc I've loaded with Ubuntu since gnome3 was added(ocelot), and it never fails to install gnome-shell.

---


---
title: "Need help with add-apt-repository"
date: 2010-07-12
forum: General Help
---

### Post by jChrisRoss on 2010-07-12
I'm creating an install script for some friend who are switching to Ubuntu. Anyway, is there a way to send STDOUT from add-apt-repository to /dev/null or any other way to quiet the output like apt-get -qq. I've tried add-apt-repository {some repo} 1> /dev/null

The problem
```

kjell@kjell-laptop:~/Documents$ sudo add-apt-repository ppa:globalmenu-team/ppa
gpg: requesting key DA6DEEAA from hkp server keyserver.ubuntu.com
gpg: key DA6DEEAA: "Launchpad PPA for Globalmenu Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```What I've done so far
```

#!/bin/sh

username=`whoami`
startdir=`pwd`

# InterfaceTab
echo -n "Install InterfaceTab [y/n]: "
read interfacetab

case "${interfacetab}" in
    "y")
        echo "Installing InterfaceTab"
        echo
        wget -q http://launchpad.net/interfacetab/trunk/inital/+download/InterfaceTab.py
        sudo mv InterfaceTab.py /usr/local/bin/
        sudo chmod 755 /usr/local/bin/InterfaceTab.py
    ;;
    "n")
    ;;
esac

# Transmission
echo "Updating Transmission"
sudo add-apt-repository ppa:transmissionbt/beta
sudo apt-get -qq update
sudo apt-get -qq upgrade transmission
mkdir -p /home/${username}/.config/transmission/
wget -q http://db.tt/opPX1F
mv transmission-settings.json /home/${username}/.config/transmission/settings.json
chmod 600 /home/${username}/.config/transmission/settings.json
mkdir -p /home/${username}/Torrents/Complete/
mkdir -p /home/${username}/Torrents/Working/
echo

# gnome-globalmenu
echo -n "Install gnome-globalmenu [y/n]: "
read globalmenu

case "${globalmenu}" in
    "y")
        sudo add-apt-repository ppa:globalmenu-team/ppa
        sudo apt-get -qq update
        sudo apt-get -qq install gnome-globalmenu
    ;;
    "n")
    ;;
esac
echo

echo "Upgrading Kernel"
sudo apt-get -qq update
newkernel=`sudo apt-cache search ^linux-image-2.6.*-generic$ | sort -r | head -n 1 | cut -d" " -f1`
sudo apt-get -qq install ${newkernel}

```

---

### Post by sisco311 on 2010-07-13
It's because it prints that message to stderr. So you have to redirect stderr to /dev/null too:
```
command &> /dev/null
```

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)


You may also want to print a short message if the command is successful and/or exit if it fails:
```
command &> /dev/null && echo OKAY || exit 1
```
```
command &> /dev/null || exit 1
```

---

### Post by jChrisRoss on 2010-07-13
Thanks. :)

---


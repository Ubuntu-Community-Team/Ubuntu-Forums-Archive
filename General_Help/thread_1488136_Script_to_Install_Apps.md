---
title: "Script to Install Apps"
date: 2010-05-19
forum: General Help
---

### Post by Jason Cook on 2010-05-19
I have created a Bash script to install Ubuntu application that I commonly use. I did this since I need to install on multiple computer and using this script will make this easier for me. This script will need to be run as root. After creating the script it must be made executable by running
```
chmod +x /path/to/file
```

```

#!/bin/bash
echo "This script was created by Jason Cook"

echo "Adding to Repositories"
echo "Adding Chromium PPA"
add-apt-repository ppa:chromium-daily/beta

echo "Adding Dropbox to Repository"
echo "#Dropbox" > /etc/apt/sources.list.d/Dropbox
echo "deb http://linux.dropbox.com/ubuntu lucid main" > /etc/apt/sources.list

echo "Adding Midori PPA"
add-apt-repository ppa:midori/ppa

echo "Adding Webkit PPA"
add-apt-repository ppa:webkit-team/ppa

echo "Adding Wicd to Repository"
echo "Wicd" > /etc/apt/sources.list
echo "deb http://apt.wicd.net karmic extras" > /etc/apt/sources.list.d/Wicd

echo "Adding Wine PPA"
add-apt-repository ppa:ubuntu-wine/ppa

echo "Adding Minitube PPA"
add-apt-repository ppa:neversfelde/ppa

echo "Adding Ailurus PPA"
sudo add-apt-repository ppa:ailurus

echo "Adding Ubuntu Tweak PPA"
add-apt-repository ppa:tualatrix/ppa

echo "Adding Blueman PPA"
add-apt-repository ppa:blueman/ppa

echo "Adding Tracker PPA"
add-apt-repository ppa:tracker-team/tracker

echo "Adding Empathy PPA"
add-apt-repository ppa:telepathy/ppa

echo "Adding Transmission PPA"
add-apt-repository ppa:transmissionbt/ppa

echo "Adding Ged Deb to Repository"
echo "#Get Deb" > /etc/apt/sources.list
echo "deb http://archive.getdeb.net/ubuntu lucid-getdeb apps" > /etc/apt/sources.list.d/GetDeb

echo "Adding Gloobus Preview PPA"
add-apt-repository ppa:gloobus-dev/gloobus-preview

echo "Adding Nautilus Elementary PPA"
add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa

echo "Adding PDF Mod to Repository"
echo "deb http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu karmic main" > /etc/apt/sources.list.d/PDFMod
echo "deb-src http://ppa.launchpad.net/pdfmod-team/ppa/ubuntu karmic main" >> /etc/apt/sources.list.d/PDFMod

echo "Adding Openshot PPA"
add-apt-repository ppa:openshot.developers/ppa

echo "Adding Keys"
echo "Adding Dropbox Key"
apt-key adv --keyserver pgp.mit.edu --recv-keys 5044912E

echo "Adding Get Deb Key"
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | apt-key add -

echo "Adding PDF Mod Key"
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1024R/A8DF5CE3

echo "Updating Packages"
aptitude update

echo "Upgrading Packages"
aptitude safe-upgrade

echo "Installing Team Viewer"
cd /tmp/
wget http://www.teamviewer.com/download/teamviewer_linux_x64.deb
dpkg -i teamviewer_linux_x64.deb

echo "Installing Apps"
aptitude install edubuntu-desktop chromium-browser nautilus-dropbox midori webkit wicd wine minitube ailurus ubuntu-tweak hardinfo  blueman blueman-icon-humanity  blueman-mono-icons simple-ccsm tracker samba bum gparted gufw curlftpfs empathy transmission vlc gloobus-preview parcellite nautilus stardict pdfmod openshot

exit 0

```

---

### Post by K.Mandla on 2010-05-20
Moved to General Help.

---

### Post by Jason Cook on 2010-05-20
> **K.Mandla said:**
> Moved to General Help.
Why was this moved to General Help. I, and the mod that approved this, thought that this should be in "Tutorials & Tips" as it is a tutorial. Can you please tell my why this was done so I can post it on the proper forum next time.

---

### Post by jsstn on 2010-05-20
am i very confused or shouldn't you be using >> instead of > to write to /etc/apt/sources.list?
it seems to me that in the end, you will have a sources.list only containing the last echo you sent it as > rewrites the file it is directed to while >> appends.

---

### Post by 3rdalbum on 2010-05-20
Don't write directly to sources.list - create a new file in /etc/apt/sources.list.d/ because it's much neater, and much less error-prone to remove just one item.

---

### Post by Jason Cook on 2010-05-20
> **3rdalbum said:**
> Don't write directly to sources.list - create a new file in /etc/apt/sources.list.d/ because it's much neater, and much less error-prone to remove just one item.
I didn't know that could be done. Thanks!

> **jsstn said:**
> am i very confused or shouldn't you be using >> instead of > to write to /etc/apt/sources.list?
it seems to me that in the end, you will have a sources.list only containing the last echo you sent it as > rewrites the file it is directed to while >> appends.
You are right. I knew that but when righting this it just sliped past me.

I have updated the script with those changes.

---


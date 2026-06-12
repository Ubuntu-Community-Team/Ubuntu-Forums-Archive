---
title: "How to uninstall Eternal Lands"
date: 2011-03-13
forum: General Help
---

### Post by TBruff15 on 2011-03-13
I ran a script to install eternal lands. So How do I uninstall it. Here is the script


#! /usr/bin/env bash

# Instructions to use:
# Download to, for example, your desktop then right click and select "Properties".
# From the "Permissions" tab, set the execute flag then click "Close".
# When that is done, double click the icon and click "Run in Terminal"

# Author Paul Broadhead [email]pjbroad@twinmoons.org.uk[/email]
#
# This program (script) is released as Public Domain software.  
# You are free to use it as you wish.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

vers="$(lsb_release -sc)"
repoline="deb [http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu) ${vers} main"

# show some information and give the chance to quit
if [ "$1" != "skip" ]
then
  cat << EOT
To install the EL packages you need root/admin privileges.

1. The following extra line will be added to your package sources list
  "${repoline}"
  
2. The key "Launchpad PPA for Paul Broadhead" will be added to your trusted
software providers list.

3. The eternallands and eternallands-data packages will be installed.  The sound
and music packages may also be installed depending on your system settings.

If you prefer, you can add add the sources and key manually using the
information provided at <https://launchpad.net/~pjbroad/+archive/ppa>.

Once installed, you will have an "Eternal Lands" icon in the
"Applications->Games" menu.  This program/icon can be deleted from 
your desktop.

EOT
  read -p "Press the return/enter key to continue" dummy
  echo ""
fi

# restart as the root user if required
if [ "$(id -u)" != "0" ]
then
  sudo $0 skip
  exit
fi

# get and install the PPA key
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com d0c20459417c1d349e2ab7d053babe78df90c47a

# write the sources line if not already there, update if added now 
pks=/etc/apt/sources.list
if [ "$(grep "^${repoline}$" $pks)" == "" ]
then
  echo -e "\n#Eternal Lands package repository\n${repoline}" >> $pks
  apt-get update
fi

# install the client package (and hence the data and other dependencies)
apt-get install eternallands

echo ""
read -p "Install complete, you can close this terminal" dummy

Please help me with this. Thank you for your time

---

### Post by tredegar on 2011-03-14
**sudo apt-get purge eternallands** should do it.

---

### Post by TBruff15 on 2011-03-20
thanks

---

### Post by W4TCHDOG on 2011-08-08
Thanks Tredegar i too was having trouble uninstalling Eternal Lands

---


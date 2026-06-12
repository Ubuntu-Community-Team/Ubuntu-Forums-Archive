---
title: "Problem with system update"
date: 2009-09-21
forum: General Help
---

### Post by mouratos1a on 2009-09-21
when attempting update i receive this:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: Failed to fetch [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/binary/Packages)  Unable to fetch file, server said 'Failed to open file.  '

W: Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '

W: Some index files failed to download, they have been ignored, or old ones used instead.



My sources.list is:

# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
#gnome-globalmenu
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
#opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
#skype
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free
#firefox
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main
#gnome-do
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main
#compiz-fusion
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
#google
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
#medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# MySQL Workbench
deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/
# Depot PlayOnLinux
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) jaunty main
# Ubuntu tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
##Themes du ZgegBlog: Project Bisigi
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe

deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) jaunty main



What should i do?
Thank you all ...

P.S.: this is my first thread please forgive any errors
Mouratos1a

---

### Post by beastrace91 on 2009-09-21
Did these repositories you added ever update with out throwing these error messages? The first error (GPG error) means you do not have the GPG key for those repositories. It will complain about this but it will not prevent updating from these repos (it will ask you to confirm before installing files form them but that is all) 

The second error is an issue on the hosts part, perhaps they are having connection issues.

At any rate neither of the two posted errors should prevent the rest of the system from updating, so no worries there ;)

~Jeff

---


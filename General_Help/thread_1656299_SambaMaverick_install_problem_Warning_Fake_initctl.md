---
title: "Samba/Maverick install problem: Warning: Fake initctl called, doing nothing."
date: 2010-12-30
forum: General Help
---

### Post by OS Stuntman on 2010-12-30
Hello,

         I have Maverick running on a Dell Latitude D610 (I'm using it as a desktop PC); I'm trying to install Samba so I can network with a newer Notebook (Windows 7/Ubuntu Maverick or Debain). 

I've tried a few HOWTOs but I end up with the same error message when I get to this point in any of the howtos:

>sudo restart smbd
>
>Warning: Fake initctl called, doing nothing.

Again, I've tried four different howtos on this and none of them ended with an installed Samba, would someone tell me what's going on.

---

### Post by t4thfavor on 2010-12-30
Is the PC visible under Network from other PC's on the lan?

Try:
```
 sudo service smbd restart 
```

Also try ps -ef|grep smbd to see if it's still running.

Did you edit the config file, maybe post it up so that I can compare it to an existing, and working smbd install I have.

Just some thoughts.

---

### Post by OS Stuntman on 2011-01-05
Excuse the late reply....

I installed Samba on my newer notebook and it installed correctly; two processes are launched at the end of the install (sudo apt-get install samba)

Here's what happens on the Dell notebook: 

```
 sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl libqca2 libqt4-opengl libxine1-x ttf-dejavu-extra
  libkjsembed4 oxygen-icon-theme libqt4-sql-mysql libqt4-dbus libxcb-xv0
  libkdecore5 docbook-xsl shared-desktop-ontologies amarok-common mysql-common
  libkatepartinterfaces4 libdvbpsi6 libsolid4 virtuoso-minimal libnepomuk4
  libx264-98 libsoprano4 libpolkit-qt-1-0 libqtscript4-core libvlc5 libkdnssd4
  libkparts4 libqapt1 kdelibs5-data kdoctools libvirtodbc0 libdbusmenu-qt2 hal
  libqtcore4 libupnp3 libxcb-shape0 libkrossui4 libqtscript4-gui
  docbook-xsl-doc-html libqt4-sql-sqlite libqtscript4-uitools libthreadweaver4
  libhal-storage1 libkmediaplayer4 libknewstuff2-4 libqt4-sql libkfile4
  libknewstuff3-4 libqapt-runtime libqt4-svg libkpty4 libindicate-qt0
  libstreamanalyzer0 libphonon4 libqt4-xml libknotifyconfig4 libkntlm4
  libqtscript4-sql libqt4-network ttf-dejavu libmysqlclient16 kdelibs-bin
  libqtgui4 libktexteditor4 libqtscript4-xml libattica0 libkio5 libkjsapi4
  libstreams0 vlc-data libtag-extras1 hal-info liblastfm0
  virtuoso-opensource-6.1-common libqt4-script libssh-4 libvlccore4
  soprano-daemon libvcdinfo0 amarok-utils kdebase-runtime-data libebml2
  libreadline5 libiodbc2 libkhtml5 libkdeui5 libkdesu5 libqtscript4-network
  kdelibs5-plugins libmatroska2 virtuoso-opensource-6.1-bin libkutils4
  libkrosscore4 libnepomukquery4a libxine1-console
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwbclient0 samba-common samba-common-bin
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools
The following NEW packages will be installed:
  libwbclient0 samba samba-common samba-common-bin
0 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/13.7MB of archives.
After this operation, 39.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package libwbclient0.
(Reading database ... 195021 files and directories currently installed.)
Unpacking libwbclient0 (from .../libwbclient0_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb) ...
Selecting previously deselected package samba-common.
Unpacking samba-common (from .../samba-common_2%3a3.5.4~dfsg-1ubuntu8.1_all.deb) ...
Selecting previously deselected package samba-common-bin.
Unpacking samba-common-bin (from .../samba-common-bin_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_2%3a3.5.4~dfsg-1ubuntu8.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for ufw ...
Setting up libwbclient0 (2:3.5.4~dfsg-1ubuntu8.1) ...
Setting up samba-common (2:3.5.4~dfsg-1ubuntu8.1) ...
Setting up samba-common-bin (2:3.5.4~dfsg-1ubuntu8.1) ...
update-alternatives: using /usr/bin/nmblookup.samba3 to provide /usr/bin/nmblookup (nmblookup) in auto mode.
update-alternatives: using /usr/bin/net.samba3 to provide /usr/bin/net (net) in auto mode.
update-alternatives: using /usr/bin/testparm.samba3 to provide /usr/bin/testparm (testparm) in auto mode.
Setting up samba (2:3.5.4~dfsg-1ubuntu8.1) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.

Warning: Fake initctl called, doing nothing.

Warning: Fake initctl called, doing nothing.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```I tried "ps -ef|grep smbd" on both machines after install Samba; it did not show smbd running on the Dell.

I have not edited the .conf file.

I also tried completely removing samba and reinstalling with Synaptic

---

### Post by t4thfavor on 2011-01-05
> **t4thfavor said:**
> Is the PC visible under Network from other PC's on the lan?

Try:
```
 sudo service smbd restart 
```

Also try ps -ef|grep smbd to see if it's still running.

Did you edit the config file, maybe post it up so that I can compare it to an existing, and working smbd install I have.

Just some thoughts.


You should probably try all of this including the part where you restart the smbd. I am not sure if you have to emable it within /etc/defaut/smbd, but you may also try there. 

You only need functioning smbd on the pc doing the sharing, and not the one doing the playing. Keep trying, I'm sure you will be successful.

also, have a look here. [http://ubuntuforums.org/archive/index.php/t-1359292.html](http://ubuntuforums.org/archive/index.php/t-1359292.html)

---


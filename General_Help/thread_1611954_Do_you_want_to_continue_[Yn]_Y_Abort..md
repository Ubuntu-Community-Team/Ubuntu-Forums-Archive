---
title: "Do you want to continue [Y/n]? Y Abort."
date: 2010-11-02
forum: General Help
---

### Post by seizart on 2010-11-02
Hi

I m trying to install some package for bigbluebutton but not working. The Y to confirm the process doesn t work:confused: 
I m complitely new with ubuntu.
****_I have already seen one post about this , but can t find my answer: _[B][U]
Please see the context below:[/U][/B]



[HTML]Suggested packages:
  asterisk-doc asterisk-dev asterisk-h323 dh-make debian-keyring g++-multilib
  g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg gettext-doc uw-mailutils
  libsox-fmt-all libstdc++6-4.4-doc vpb-utils diffutils-doc libmail-box-perl
  libmyodbc odbc-postgresql tdsodbc unixodbc-bin
The following NEW packages will be installed:
  asterisk asterisk-config asterisk-sounds-main build-essential dahdi
  dahdi-dkms dahdi-linux debhelper dkms dpkg-dev fakeroot freetds-common
  fxload g++ g++-4.4 gawk gettext html2text intltool-debian
  libalgorithm-diff-perl libalgorithm-merge-perl libc-client2007e libcorosync4
  libdpkg-perl libgmime-2.0-2a libiksemel3 libmail-sendmail-perl libopenais3
  libopenr2-3 libpq5 libpri1.4 libradiusclient-ng2 libsox-fmt-alsa
  libsox-fmt-base libsox1b libspandsp2 libsqlite0 libss7-1 libstdc++6-4.4-dev
  libsybdb5 libsys-hostname-long-perl libtonezone2.0 libunistring0 libvpb0
  mlock module-assistant odbcinst odbcinst1debian2 patch po-debconf sox
  unixodbc vpb-driver-source
0 upgraded, 53 newly installed, 0 to remove and 0 not upgraded.
Need to get 23,3MB of archives.
After this operation, 69,4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.

---

### Post by 3Miro on 2010-11-02
Have you tried System -> Admin -> Synaptic Package Manager. Does it work from there?

---

### Post by hhh on 2010-11-02
I've run into this with some installs, try hitting Enter without hitting Y.

Found this, check that you have all the prerequisites...
[http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu](http://code.google.com/p/bigbluebutton/wiki/InstallationUbuntu)

---

### Post by seizart on 2010-11-02
it worked !

Thanks

now i m trying to give access from external host

---

### Post by seizart on 2010-11-09
it was working and suddenly it stopped.

I resinstalled complitely ubuntu and tried to reinstall bbb but i got the following error:
E: bbb-client: subprocess installed post-installation script returned error exit status 1
E: bbb-config: dependency problems - leaving unconfigured
E: bigbluebutton: dependency problems - leaving unconfigured

I dont understand what i am doing wrong

---


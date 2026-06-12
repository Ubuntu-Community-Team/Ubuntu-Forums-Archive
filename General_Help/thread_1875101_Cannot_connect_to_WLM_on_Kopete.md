---
title: "Cannot connect to WLM on Kopete"
date: 2011-11-04
forum: General Help
---

### Post by FallenUnia on 2011-11-04
Hey all,

Since three days, I can not connect to my Windows Live Messenger acount on Kopete. It just shows "Connecting" and stays there, untill I double-click my account. Then it gives me a popup, saying that it can not reach the server because either my connection is down or the server is.

Now obviously, it's not my internet. And also, it's not WLM's server(s), because my brother (on Windows, however) can still log in and my friends can too.

I already tried to delete Kopete's config file in ~/.kde/share/config/kopeterc and start fresh, but it still refuses to connect.

To perhaps spot some error messages, I tried launching Kopete from the terminal, and I got this:
```

[jente@lappy ~]$ kopete(10432)/libkopete Kopete::AccountManager::registerAccount: No identity for account  "<censor>@hotmail.com" : falling back to default
```

Google does not come up with any help, so that's why I'm asking here. Please help me!

PS: reinstalling didn't help either - nor did purging it.

---

### Post by kaizo2560 on 2011-11-04
Hi got the same problem please help.

Thanks in advance

---

### Post by mweijts on 2011-11-05
I have the same problem,

when i logged in with 2 accounts ....@hotmail.com its keeps connecting.
....@msn.com  is working correct.

It looks likes a problem with the hotmail.com server, but ...@hotmail.com is working with AMSN

there are problems with the messenger server [http://windowslivehelp.com/thread.aspx?threadid=7d165548-a7a0-4616-ad24-bb2444a23db9&page=1](http://windowslivehelp.com/thread.aspx?threadid=7d165548-a7a0-4616-ad24-bb2444a23db9&page=1)

---

### Post by FallenUnia on 2011-11-05
I can log in on my Android phone and on my brother's Windows laptop using the normal Windows Live Messenger application.

I still can not login on Kopete. What's wrong?

---

### Post by FallenUnia on 2011-11-06
I have just installed Kmess (alternative IM application for KDE) and it can log in fine. I guess this is a bug so I will submit a bug report later today. I'll keep you guys posted through here.

In the meantime, does anyone have an older version of Kopete so that I can try and see if that works?

---

### Post by FallenUnia on 2011-11-07
Bug reported here:
[https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/887104](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/887104)

As you can see in the report, downgrading to Kopete from Natty didn't work either. Lets hope they can fix this bug!

**EDIT:** The bug has just been confirmed!

---

### Post by nick_nitro on 2011-11-07
> **FallenUnia said:**
> I have just installed Kmess (alternative IM application for KDE) and it can log in fine. I guess this is a bug so I will submit a bug report later today. I'll keep you guys posted through here.

In the meantime, does anyone have an older version of Kopete so that I can try and see if that works?

yes Kmess works but i can not retrieve my contacts.
It seems the have changed the contacts service URL.

---

### Post by FallenUnia on 2011-11-07
> **nick_nitro said:**
> yes Kmess works but i can not retrieve my contacts.
It seems the have changed the contacts service URL.

Exactly my problem with Kmess too! Although I do appear as online at other people and they can start a conversation...

---

### Post by nick_nitro on 2011-11-07
patch available for kmess

[http://kmess.org/board/viewtopic.php?f=4&t=20549](http://kmess.org/board/viewtopic.php?f=4&t=20549)

---

### Post by FallenUnia on 2011-11-07
Thanks, that indeed fixed Kmess! Do you happen to know if there's an up to date .deb too? 

I tried making one following this how-to: [http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html](http://www.webupd8.org/2010/01/how-to-create-deb-package-ubuntu-debian.html)

But it fails at the last step (step 7), throwing me this error:
```
&#9484;&#9472;[jente@lappy kmess-2.0.6.1][21:01:51] 
&#9492;&#9472;&#9632; dpkg-buildpackage -rfakeroot
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package kmess
dpkg-buildpackage: source version 2.0.6.1-1
dpkg-buildpackage: source changed by Jente Hidskes <jthidskes@gmail.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build kmess-2.0.6.1
 fakeroot debian/rules clean
dh clean 
   dh_testdir
   dh_auto_clean
make[1]: Map '/home/jente/packages/ubuntu/kde/kmess/kmess-2.0.6.1' wordt binnengegaan
make[1]: Map '/home/jente/packages/ubuntu/kde/kmess/kmess-2.0.6.1' wordt verlaten
   dh_clean
 dpkg-source -b kmess-2.0.6.1
dpkg-source: info: using source format `3.0 (quilt)'
dpkg-source: info: building kmess using existing ./kmess_2.0.6.1.orig.tar.bz2
dpkg-source: error: cannot represent change to kmess-2.0.6.1/build/CMakeFiles/CMakeDetermineCompilerABI_CXX.bin: binary file contents changed
dpkg-source: error: add build/CMakeFiles/CMakeDetermineCompilerABI_CXX.bin in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to kmess-2.0.6.1/build/CMakeFiles/CMakeDetermineCompilerABI_C.bin: binary file contents changed
dpkg-source: error: add build/CMakeFiles/CMakeDetermineCompilerABI_C.bin in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to kmess-2.0.6.1/build/CMakeFiles/CompilerIdC/a.out: binary file contents changed
dpkg-source: error: add build/CMakeFiles/CompilerIdC/a.out in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: cannot represent change to kmess-2.0.6.1/build/CMakeFiles/CompilerIdCXX/a.out: binary file contents changed
dpkg-source: error: add build/CMakeFiles/CompilerIdCXX/a.out in debian/source/include-binaries if you want to store the modified binary in the debian tarball
dpkg-source: error: unrepresentable changes to source
dpkg-buildpackage: error: dpkg-source -b kmess-2.0.6.1 gave error exit status 2

```Can anyone shed some light on this? Then I can make an up-to-date .deb of a working Kmess available for all of you!

**EDIT:** I did compile it from source to test if it works, it does!
**EDIT2:** Does it throw these errors because I compiled from source from this directory too?

---

### Post by nick_nitro on 2011-11-07
sorry, i'm at work now but i will look into this asap.

---

### Post by djchallis on 2011-11-07
I'm having exactly the same problem.

---

### Post by FallenUnia on 2011-11-09
Someone posted how you can make your own working Kopete on the bug report. I'll quote him here:

[quote=Jari]                              The updates can be applied also to oneiric, and an updated package can be built as follows:
 mkdir tmpmsn
cd tmpmsn/
apt-get source libmsn
sudo apt-get build-dep libmsn
wget [http://libmsn.svn.sourceforge.net/viewvc/libmsn/trunk/msn/soap.cpp?revision=121](http://libmsn.svn.sourceforge.net/viewvc/libmsn/trunk/msn/soap.cpp?revision=121)
wget [http://libmsn.svn.sourceforge.net/viewvc/libmsn/trunk/msn/soap.h?revision=121](http://libmsn.svn.sourceforge.net/viewvc/libmsn/trunk/msn/soap.h?revision=121)
mv soap.cpp\?revision\=121 libmsn-4.1/msn/soap.cpp
mv soap.h\?revision\=121 libmsn-4.1/msn/soap.h
cd libmsn-4.1/
dpkg-buildpackage
cd ..
sudo dpkg -i libmsn0.3_4.1-2ubuntu1_i386.deb
 Start kopete and it connects.
 Next upgrade will overwrite it, so one can hold the package
sudo aptitude hold libmsn0.3
 Holding can be avoided if the version number was changed in libmsn-4.1/debian/changelog (like I actually did).[/quote]

**EDIT:** So far it's not working for me...

---

### Post by nick_nitro on 2011-11-10
well i don't know about kopete but debs for kmess 64bits ubuntu and 32 bits ubuntu are here.

32 bit: [http://lekensteyn.nl/files/kmess/kmess_2.0.6.1-0ubuntu1~_i386.deb](http://lekensteyn.nl/files/kmess/kmess_2.0.6.1-0ubuntu1~_i386.deb) 
64 bit: [http://lekensteyn.nl/files/kmess/kmess_2.0.6.1-0ubuntu1~_amd64.deb](http://lekensteyn.nl/files/kmess/kmess_2.0.6.1-0ubuntu1~_amd64.deb)

i can not test the kopete deb building for the moment cause i have only archlinux on my pc.

---

### Post by cyberwizzard on 2011-11-10
> **FallenUnia said:**
> Someone posted how you can make your own working Kopete on the bug report. I'll quote him here:

**EDIT:** So far it's not working for me...

It is working for me (Ubuntu 11.10 AMD64 with Kopete) and I've uploaded the binary package to my website.

You can download the package [*here*](http://www.cyberwizzard.nl/site/downloads/view.download/1/12.html), or use the instructions above to compile it yourself, of course :)

After installation I only shut down Kopete and started it again: no need to log out or reboot.

---

### Post by FallenUnia on 2011-11-10
Thank you cyberwizzard! 

I appreciate that you packaged it and hosted the .deb for us, but sadly, this does not fix my issue. As seen in the bug report, is does solve it or many users - sadly I am not among them.

**EDIT:** Removing my user account and re-adding it, did the trick!

---

### Post by mbenedettini on 2011-11-15
i386 libmsn4.2 package can be found [here]("http://marianobe.wordpress.com/2011/11/15/unofficial-libmsn4-2-package-for-ubuntu-11-10-oneiric-ocelot/").

---

### Post by djchallis on 2011-11-30
I ran the AMD64 Kopete binary package as provided by cyberwizzard. It didn't fix it for me. In fact, Kopete now can't even load the Windows Live Messenger plugin. My WLM account doesn't appear on my accounts list, when I try to add it again it says it can't load the plugin.

---


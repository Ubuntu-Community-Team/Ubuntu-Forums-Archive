---
title: "Democracy Player on Dapper howto"
date: 2006-06-25
forum: General Help
---

### Post by macewan on 2006-06-25
*basicly you'll wget the two .debs & force install*

 [U][.deb 1]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb")
[.deb 2]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb")

[/U]**sudo dpkg –force-all -i de*.deb**
*it will show as a menu entry under the Sounds & Video menu section*

[IMG]http://www.macewan.org/images/DemocracyPlayerUbuntuDapperMenu.png[/IMG]

*it's slow to start but it works, just give it a sec. when you click*



[[IMG]http://www.macewan.org/images/DemocracyPlayerDapper.png[/IMG]]("http://www.macewan.org/images/DemocracyDapperScreenshot.png")



If you’re trying to install the Democracy Player on Ubuntu Dapper you will more than likely run into the libpango error. Version 1.12.3 of libpango is the requested requirement from Democracy Player while Dapper is supplying libpango 1.12.2-0ubuntu3. The solution, until either the Dapper devs or Democracy devs match them, is to force the package. Let’s see the error first before we force.
     macewan@cole:~/Desktop$ wget [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb")
macewan@cole:~/Desktop$ wget [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb")
macewan@cole:~/Desktop$ sudo dpkg -i de*.deb
Password:
Selecting previously deselected package democracyplayer.
(Reading database … 170250 files and directories currently installed.)
Unpacking democracyplayer (from democracyplayer_0.8.4.1-1_i386.deb) …
Selecting previously deselected package democracyplayer-data.
Unpacking democracyplayer-data (from democracyplayer-data_0.8.4.1-1_all.deb) …dpkg: dependency problems prevent configuration of democracyplayer:
 democracyplayer depends on libpango1.0-0 (>= 1.12.3); however:
  Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
dpkg: error processing democracyplayer (–install):
 dependency problems - leaving unconfigured
Setting up democracyplayer-data (0.8.4.1-1) …
Errors were encountered while processing:
 democracyplayer
     macewan@cole:~/Desktop$ sudo dpkg –force-all -i de*.deb
Selecting previously deselected package democracyplayer.
(Reading database … 170422 files and directories currently installed.)
Unpacking democracyplayer (from democracyplayer_0.8.4.1-1_i386.deb) …
Preparing to replace democracyplayer-data 0.8.4.1-1 (using democracyplayer-data_ 0.8.4.1-1_all.deb) …
Unpacking replacement democracyplayer-data …
Setting up democracyplayer-data (0.8.4.1-1) …
dpkg: democracyplayer: dependency problems, but configuring anyway as you reques t:
 democracyplayer depends on libpango1.0-0 (>= 1.12.3); however:
  Version of libpango1.0-0 on system is 1.12.2-0ubuntu3.
Setting up democracyplayer (0.8.4.1-1) …
macewan@cole:~/Desktop$
     ** alright, let’s see where we stand at the moment starting with the menu system
Applications > Sound & Video > Democracy TV
     ** looks good, let’s see if it is actually working (click Democracy TV in the menu)
     
[IMG]http://www.macewan.org/images/DemocracyPlayerDapper.png[/IMG]
     The two Dapper .debs you want are the [data package]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb") and the [player package]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb") - see the [Ubuntu download page]("http://www.getdemocracy.com/downloads/ubuntu.php") on the Democracy Player site for more information.
     [http://www.getdemocracy.com/downloads/ubuntu.php]("http://www.getdemocracy.com/downloads/ubuntu.php")

---

### Post by dipswitch on 2006-06-26
Thanks for the how-to. Works great.

---

### Post by spooler on 2006-06-30
Hi , i have some errors when i try to run DP : 

```
 giladk@xmachine:~$ democracyplayer
DTV: Starting up Democracy Player
DTV: Version:  0.8.4.1
DTV: Revision: https://svn.participatoryculture.org/svn/dtv/tags/Democracy-Player-0.8.4.1/tv - 2146
DTV: Loading preferences...
DTV: Restoring database...
DTV: Recomputing filters...
DTV: Spawning auto downloader...
DTV: Spawning idle notifier
DTV: idle notifier running
DTV: Displaying main frame...
DTV: Starting event loop thread
*** Launching Democracy Downloader Daemon ****
*** Daemon ready ***
DTV: updating the Guide
WARNING: feed update for: http://del.icio.us/rss/representordie/system:media:video too slow (0.267 secs)
INTERNAL ERROR on Browser End: JavaPluginFactory5 init - no agent?

System error?:: No such file or directory
downloader: connection closed -- quitting
Shutting down downloaders...
giladk@xmachine:~$
 
```

i have jre5 installed ...

---

### Post by cbudden on 2006-06-30
> **macewan]*basicly you'll wget the two .debs & force install*

 [U][.deb 1]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb")
[.deb 2]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb")

[/U]**sudo dpkg –force-all -i de*.deb**
*it will show as a menu entry under the Sounds & Video menu section*

[IMG]http://www.macewan.org/images/DemocracyPlayerUbuntuDapperMenu.png[/IMG]

*it's slow to start but it works, just give it a sec. when you click*



[[IMG]http://www.macewan.org/images/DemocracyPlayerDapper.png[/IMG]]("http://www.macewan.org/images/DemocracyDapperScreenshot.png")



If you’re trying to install the Democracy Player on Ubuntu Dapper you will more than likely run into the libpango error. Version 1.12.3 of libpango is the requested requirement from Democracy Player while Dapper is supplying libpango 1.12.2-0ubuntu3. The solution, until either the Dapper devs or Democracy devs match them, is to force the package. Let’s see the error first before we force.
     macewan@cole:~/Desktop$ wget [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb")
macewan@cole:~/Desktop$ wget [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb")
macewan@cole:~/Desktop$ sudo dpkg -i de*.deb
Password:
Selecting previously deselected package democracyplayer.
(Reading database … 170250 files and directories currently installed.)
Unpacking democracyplayer (from democracyplayer_0.8.4.1-1_i386.deb) …
Selecting previously deselected package democracyplayer-data.
Unpacking democracyplayer-data (from democracyplayer-data_0.8.4.1-1_all.deb) …dpkg: dependency problems prevent configuration of democracyplayer:
 democracyplayer depends on libpango1.0-0 (>= 1.12.3) said:**
> http://www.macewan.org/images/DemocracyPlayerDapper.png[/IMG]
     The two Dapper .debs you want are the [data package]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer-data_0.8.4.1-1_all.deb") and the [player package]("http://ftp.osuosl.org/pub/pculture.org/democracy/linux/ubuntu/democracyplayer_0.8.4.1-1_i386.deb") - see the [Ubuntu download page]("http://www.getdemocracy.com/downloads/ubuntu.php") on the Democracy Player site for more information.
     [http://www.getdemocracy.com/downloads/ubuntu.php]("http://www.getdemocracy.com/downloads/ubuntu.php")




Could you tell me where you got that nice wallpaper from please.

Thanks

---

### Post by cooldudejz on 2006-06-30
i am having the exact same problem as spooler. do u have seomthing special in your Sun Java 5.0 Plugin Control Center or something.

---

### Post by spockrock on 2006-06-30
works perfectly thanks.

---

### Post by H.E. Pennypacker on 2006-07-14
> **cbudden said:**
> Could you tell me where you got that nice wallpaper from please.

Thanks

[[IMG]http://img215.imageshack.us/img215/5786/intelmacred16001024notxt0hq.th.jpg[/IMG]](http://img215.imageshack.us/img215/5786/intelmacred16001024notxt0hq.jpg)

---

### Post by abbot on 2006-07-23
getting this error.

adam@ubuntu:~$ democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 80, in ?
    startapp()
  File "/usr/bin/democracyplayer", line 37, in startapp
    import singleclick
  File "/usr/lib/python2.4/site-packages/democracy/singleclick.py", line 17, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 434, in ?
    import frontend
  File "/usr/lib/python2.4/site-packages/democracy/frontend.py", line 42, in ?
    import MozillaBrowser
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

---

### Post by j-strap2 on 2006-07-23
I get the same error as abbot. I installed the packages listed here:
[https://develop.participatoryculture.org/projects/democracy/wiki/GTKX11BuildDocs](https://develop.participatoryculture.org/projects/democracy/wiki/GTKX11BuildDocs)
and still no joy.

---

### Post by SmrtJustin on 2006-07-24
> **abbot said:**
> getting this error.

adam@ubuntu:~$ democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 80, in ?
    startapp()
  File "/usr/bin/democracyplayer", line 37, in startapp
    import singleclick
  File "/usr/lib/python2.4/site-packages/democracy/singleclick.py", line 17, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 434, in ?
    import frontend
  File "/usr/lib/python2.4/site-packages/democracy/frontend.py", line 42, in ?
    import MozillaBrowser
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory

I'm getting the same exact error!

---

### Post by j-strap2 on 2006-07-24
I've got a little bit further but still get an error. It looks like democracyplayer cannot find the libgtkembedmoz.so library. If I run it like this:

```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/firefox && democracyplayer
```

I get this error instead:

```
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 80, in ?
    startapp()
  File "/usr/bin/democracyplayer", line 37, in startapp
    import singleclick
  File "/usr/lib/python2.4/site-packages/democracy/singleclick.py", line 17, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 434, in ?
    import frontend
  File "/usr/lib/python2.4/site-packages/democracy/frontend.py", line 42, in ?
    import MozillaBrowser
ImportError: /usr/lib/python2.4/site-packages/democracy/MozillaBrowser.so: undefined symbol: _Z12ToNewCStringRK9nsAString

```

---

### Post by justinflavin on 2006-07-24
i'm getting the exact same errors here , after i adjusted my LD LIBRARY PATH.
guess i'll have to give DemocracyPlayer a miss until they get the packages sorted out.

is anyone going to add it to the Ubuntu repositories, so that we can just "apt-get install" it in the future?

---

### Post by OmShiva on 2006-07-24
Thanks for the install. It installed and is working fine. The update icon shows up in the notification area however saying that I have a broken package. My concern is will synaptic remove this package when updating or intalling other packages? Is there a way to show it as not being broken?

---

### Post by PhoeZ on 2006-07-24
I'm getting the same error as others above after symlinking/fixing the path. Nice to know I'm not the only one.

Edit: It seems to work after installing mozilla, but I don't really want mozilla on my computer seeing as I already have opera and firefox.

---

### Post by s_h_a_d_o_w_s on 2006-07-24
I think i messed it up, but i rebooted as voila, it worked.

---

### Post by kbuel on 2006-07-24
> **abbot said:**
> getting this error.

adam@ubuntu:~$ democracyplayer
Traceback (most recent call last):
  File "/usr/bin/democracyplayer", line 80, in ?
    startapp()
  File "/usr/bin/democracyplayer", line 37, in startapp
    import singleclick
  File "/usr/lib/python2.4/site-packages/democracy/singleclick.py", line 17, in ?
    import app
  File "/usr/lib/python2.4/site-packages/democracy/app.py", line 434, in ?
    import frontend
  File "/usr/lib/python2.4/site-packages/democracy/frontend.py", line 42, in ?
    import MozillaBrowser
ImportError: libgtkembedmoz.so: cannot open shared object file: No such file or directory



I had this error... to fix it i installed these two packages:
mozilla-browser
mozilla-psm

Hope this helps.

---

### Post by SmrtJustin on 2006-07-25
You only need to install mozilla-browser, and that takes care of the problem! ;)  It does suck that its needed, because besides Democracy Player, I have no use for mozilla-browser, its not like I'm actually going to use it.

---

### Post by j-strap2 on 2006-07-25
Somehow my mozilla installation was broken. I had to rebuild the package database and clean out the old mozilla stuff before restoring. Working fine now, thanks.

---

### Post by easyease on 2006-08-28
I just installed it via "automatix bleeder" last night but run into a problem 
 i tried to access "french maid tv(hehe) from the channel list, when a box pops up and tells me i need to install a personel security manager- clicking on this box freezes the app for some reason (?) and christ knows what a personel security manager is, 
 i cant find the package.....
also it eats up a lot of cpu....

 other than that it  looks great. \\:D/

---

### Post by nolihc on 2006-09-09
I'am having problems with the quicktime codec, does democracy player use vlc as a player?

---

### Post by babwe on 2006-10-02
I got democracyplayer to run on Dapper 64 bit PC, by going here [http://http://www.getdemocracy.com/downloads/]("http://http://www.getdemocracy.com/downloads/")
and then I downloaded the DataPackage and the For 64-bit systems, use this player package instead.       Then I installed as per this guide [https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes]("https://develop.participatoryculture.org/projects/democracy/wiki/LinuxNotes")
and every thing wazz done as right click and select "Open with gdebi") on the deb files so they are opened with gdebi, first democracyplayer-data_0.8.4.1-1_all.deb and after that democracyplayer_0.8.4.1-1_i386.deb and everything worked:) :KS

---


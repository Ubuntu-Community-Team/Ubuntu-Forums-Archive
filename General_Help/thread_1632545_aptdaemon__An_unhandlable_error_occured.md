---
title: "aptdaemon / An unhandlable error occured"
date: 2010-11-28
forum: General Help
---

### Post by Nathre on 2010-11-28
aptdaemon

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Detail

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 938, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the g++ package. This might mean you need to manually fix this package.


*************************************************************************
I used this line as someone asked in the forums on someone else's thread:
sudo apt-get update

After many lines I got this:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
andres@ubuntu:~$

*************************************************************************

I restarted my pc after installing Ubuntu updates while I was downloading an app. Can you guys help me?

I can not install any other software by the way...

---

### Post by sikander3786 on 2010-11-28
First of all add the missing gpg key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

Then try these,

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

---

### Post by Lure_Angler on 2010-12-22
Thank you very much.

Your code have solved my problem. 
:popcorn:


tc

---

### Post by sikander3786 on 2010-12-23
You are Welcome :-)

Please mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

### Post by intominto on 2011-02-19
> **sikander3786 said:**
> First of all add the missing gpg key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```Then try these,

```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
```
  
hello i tried to install p2p program for watching live football games and so on and i had to install there , GTK-soap cast and i downloaded it like gtk-sopcast_0.2.8-1_i386.deb and open it from UBUNTU software center but same error repeated all the time:( and I tried the command way like you told above, but it doesn't work yet:( 

could you please help me ? I have screenshot here attached within!
Or is that I have to add new source for it instead of installing from ubuntu software center, if you know can you provide me the source for repository like 'deb http:// blaa. blaa. ' :(

[IMG]file:///home/kaliama/Desktop/Screenshot.png[/IMG][ATTACH]183916[/ATTACH]

---

### Post by sikander3786 on 2011-02-20
> **intominto said:**
> hello i tried to install p2p program for watching live football games and so on and i had to install there , GTK-soap cast and i downloaded it like gtk-sopcast_0.2.8-1_i386.deb and open it from UBUNTU software center but same error repeated all the time:( and I tried the command way like you told above, but it doesn't work yet:( 

could you please help me ? I have screenshot here attached within!
Or is that I have to add new source for it instead of installing from ubuntu software center, if you know can you provide me the source for repository like 'deb http:// blaa. blaa. ' :(

[IMG]file:///home/kaliama/Desktop/Screenshot.png[/IMG][ATTACH]183916[/ATTACH]
Welcome to the forums :-)

I haven't used sopcast myself. However I found this for you. Add the sources and install gtk-sopcast from the repositories.

[http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/](http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/)

Let us know how that goes ;-)

---

### Post by intominto on 2011-02-20
> **sikander3786 said:**
> Welcome to the forums :-)

I haven't used sopcast myself. However I found this for you. Add the sources and install gtk-sopcast from the repositories.

[http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/](http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/)

Let us know how that goes ;-)

:( doesn't work yet :(

---

### Post by intominto on 2011-02-20
> **sikander3786 said:**
> Welcome to the forums :-)

I haven't used sopcast myself. However I found this for you. Add the sources and install gtk-sopcast from the repositories.

[http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/](http://www.kabatology.com/05/15/how-to-install-sopcast-player-in-ubuntu-10-04/)

Let us know how that goes ;-)

:( doesn't work yet :( and well I have ubuntu 10.10 Marverik !

---

### Post by winspear on 2011-06-08
I tried the same in natty narhwal 64-bit OS and nothing happens. It fails with the following error. 

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/plymouth/libplymouth2_0.8.2-2ubuntu23_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.8.13.2ubuntu3_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc62_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns69_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg62_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.3.dfsg-1ubuntu2.1_amd64.deb  Size mismatch
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt-common_0.7.100.3ubuntu6.1_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Any help will be appreciated. 
Thanks
W

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **intominto said:**
> :( doesn't work yet :(

Don't use that method to install a PPA..  It better this way:

[http://cinderbox.net/2011/04/13/install-sopcast-player-in-ubuntu-11-04-natty-narwhal-ppa/](http://cinderbox.net/2011/04/13/install-sopcast-player-in-ubuntu-11-04-natty-narwhal-ppa/)

---

### Post by bapoumba on 2011-06-08
@winspear: from what I have read around, this is due to either slow internet connection or proxy problems. Would this apply to your case?

Please try:
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by fallforthesky on 2011-07-19
> **linuxinstalledfromhdd said:**
> Don't use that method to install a PPA..  It better this way:

[http://cinderbox.net/2011/04/13/install-sopcast-player-in-ubuntu-11-04-natty-narwhal-ppa/](http://cinderbox.net/2011/04/13/install-sopcast-player-in-ubuntu-11-04-natty-narwhal-ppa/)

i keep getting this when i try installing anything 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download:(
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by User2011 on 2011-09-23
Hey there! I am searching through posts to try to find anything that can help me with my problem. I'd wonder if you could help me? 

[FONT=Arial Narrow][SIZE=2]every software that I try to download on the **Ubuntu Software  Center** is consequently being interrupted by a pop up error window that  says:

***An unhandlable error occured -*** [I]There seems to be a   programming error in aptdaemon, the software that allows you to   install/remove software and to perform other package management related   tasks

[B]Details:
[FONT=Courier New]
[/FONT][/B][/I][FONT=Courier New]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.



[FONT=Arial Narrow]Can you please help me? Thankyou.[/FONT][/FONT][/SIZE][/FONT]

---

### Post by robothouse01 on 2011-09-30
> **User2011 said:**
> Hey there! I am searching through posts to try to find anything that can help me with my problem. I'd wonder if you could help me? 

[FONT=Arial Narrow][SIZE=2]every software that I try to download on the **Ubuntu Software  Center** is consequently being interrupted by a pop up error window that  says:

***An unhandlable error occured -*** [I]There seems to be a   programming error in aptdaemon, the software that allows you to   install/remove software and to perform other package management related   tasks

[B]Details:
[FONT=Courier New]
[/FONT][/B][/I][FONT=Courier New]Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the  ttf-mscorefonts-installer package. This might mean you need to manually  fix this package.



[FONT=Arial Narrow]Can you please help me? Thankyou.[/FONT][/FONT][/SIZE][/FONT]

Hi Ubuntu forums :D

I have the same problem and I get the exact same error except for the last line!! 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
[B]SystemError: E:I wasn't able to locate file for the _libcommons-logging-java_ package. This might mean you need to manually fix this package.

[/B]So what do we do?? If I need to manually fix the java package, how would I go about doing that?

---

### Post by benjaminblaqk on 2011-10-08
> **sikander3786 said:**
> First of all add the missing gpg key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```Then try these,

```
sudo apt-get update && sudo apt-get upgrade
``````
sudo apt-get install -f
``````
sudo dpkg --configure -a
```


I've tried these in terminal, but at the end, a license agreement appears with the <ok> listed down towards the bottom. I'm sure i'm suppose to agree to something, I just can't figure out how.

---

### Post by jayanthsagar on 2013-01-29
press F12...it will prompt u to agree...press ok to continue.

---

### Post by overdrank on 2013-01-29
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


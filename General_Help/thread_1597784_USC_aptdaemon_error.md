---
title: "USC aptdaemon error"
date: 2010-10-15
forum: General Help
---

### Post by migs73 on 2010-10-15
Hi All

I downloaded a driver for my Brother scanner (brscan) and tried to install it, USC said already installed, so I (stupidly) clicked reinstall.
Seemed to go ok but scanner not working still. Then realise I should have had brscan3 driver. Opened USC and clicked uninstall for the brscan. Now I get the following errors;
```
Removing brscan ...

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory

rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory

dpkg: error processing brscan (--remove):

 subprocess installed post-removal script returned error exit status 1

Errors were encountered while processing:

 brscan
```

Now no matter **what** I try to install I get this message;
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Details;

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the brscan package. This might mean you need to manually fix this package.
```

Tried Synaptic to unisntall brscan and get the following error;
E: brscan: subprocess installed post-removal script returned error exit status 1

Details

```
(Reading database ... 143691 files and directories currently installed.)
Removing brscan ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHLFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHMFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/BHminiFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/YL4FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZL2FB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLe': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ZLeFB': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

Don't know if the brscan package is problem or apt.

Please help!!

---

### Post by migs73 on 2010-10-16
Tried this code (don't know if it was a good idea or not);

```
sudo apt-get --purge remove brscan
```

and got the same results as for synaptic above.

---

### Post by migs73 on 2010-10-16
Better being lucky then good!!!

Realised after a good look at what the terminal spat out that all the things it was missing were in one folder. Luckily I dual boot with Lucid where I already had Brscan3 set up. Browsed in there for the same folder, and copied it to where apt was looking to delete (usr/local/Brother/sane) and pasted it. Started back into synaptic and marked Brscan for removal again. Hit the apply button and hoped it wouldn't notice the folder contents were for Brscan3.
It didn't. Brscan removed.
 
Installed Brscan3 and all okay!!
Well I say all okay, now I just have to get simple scan to acknowledge my scanner!! But that is a different story.

Look at this, a whole thread all to myself!!

:P

---

### Post by jandriel on 2010-10-16
> **migs73 said:**
> Look at this, a whole thread all to myself!!

And it's entertaining, too!

---

### Post by mendoh on 2010-10-17
Hi everybody!

I was wondering if anyone could help with the following error I am getting from aptdaemon:

[B]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the mysqmail package. This might mean you need to manually fix this package.[/B]

I am currently _unable to install any new software_ because of the above error and it all came up when I tried to install (without success) mysqlmail on my Ubuntu.

Thanks a lot in advance

Mendoh

---

### Post by migs73 on 2010-10-17
> **mendoh said:**
> Hi everybody!

I was wondering if anyone could help with the following error I am getting from aptdaemon:

[B]Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the mysqmail package. This might mean you need to manually fix this package.[/B]

I am currently _unable to install any new software_ because of the above error and it all came up when I tried to install (without success) mysqlmail on my Ubuntu.

Thanks a lot in advance

Mendoh

Try ```
sudo apt-get install mysqmail
```
and post the results (it will fail) back here.

---

### Post by hijataka on 2010-10-18
Hi, I got the same problem also with a brother-driver.
Here's the errormsg when I try to install anything:

```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the dcp1000lpr package. This might mean you need to manually fix this package.

```

And the result when I use you command

```
sudo apt-get install mysqmail
```

looks like this:

```
matt@ubuntu:~$ sudo apt-get install dcp1000lpr
[sudo] password for matt: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
dcp1000lpr ist schon die neueste Version.
Die folgenden Pakete werden ENTFERNT:
  dcp1000lpr
0 aktualisiert, 0 neu installiert, 1 zu entfernen und 0 nicht aktualisiert.
1 nicht vollständig installiert oder entfernt.
Nach dieser Operation werden 0B Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren [J/n]? j
(Lese Datenbank ... 147746 Dateien und Verzeichnisse sind derzeit installiert.)
Entferne dcp1000lpr ...
start: Unknown job: lpd
dpkg: Fehler beim Bearbeiten von dcp1000lpr (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 dcp1000lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's partly german i hope you can figure it out...
Thx in advance!

---

### Post by migs73 on 2010-10-18
```
Package dcp1000lpr is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  brother-lpr-drivers-laser1

E: Package 'dcp1000lpr' has no installation candidate

```

That is the result I get when trying to install that package.
Try to remove it and install it again.

---

### Post by hijataka on 2010-10-18
Well that's what doesn't work - removing the package...
And I cannot install any other packages cause synaptic always shows the error msg concerning the brother dcp1000 package...

---

### Post by migs73 on 2010-10-18
I was hoping that by installing it on my machine I could tell you where the file should be and you could just create one for it to delete as I did. 

Unfortunately I am not able to do so. Try some of the other ways to remove the package (synaptic, USC) and look for any files it says it can't find in the details drop down. 
Create files at those locations and then try again.

There must be a bug in APT, for it to 'lose' files like this. 
I also don't understand why it hogs the whole of the install process and effectively stops you installing anything else.
Maybe somebody else will have a better solution than my (admittedly poor) effort.

---

### Post by hijataka on 2010-10-18
Yesss, I got it! Thanks....

I used
```
sudo gedit /var/lib/dpkg/status
```
and deleted the section about dcp1000lpr!

Then
```
sudo apt-get update
sudo apt-get upgrade
```

and voila....

---

### Post by migs73 on 2010-10-18
Good find, I'll need to remember that.
Still don't know if it is just a general screw-up or a bug in APT (dpkg).

---

### Post by migs73 on 2010-10-18
> **hijataka said:**
> 

and voila....

English, German and now French!!

Now a bit o'Scots. We're a' Jock Tamson's bairns!

(Translates as we are all equal, pretty much the scots for Ubuntu!!)

:P

---

### Post by hijataka on 2010-10-19
Actually I'm dutch! And I write in english, german and french - Weird........
;)

---

### Post by hijataka on 2010-10-19
JAJA I know - dutch is basically just a mixture of those languages....................

---

### Post by Paulgirardin on 2010-10-26
I had the same problem with a package called Icogen.

The fix worked.

thanks

---

### Post by sotospt52 on 2010-11-06
It worked and with me i had the bandwithd with broken pakages and remove it like this way thnx

---

### Post by giuseppegiache on 2011-01-22
solved thanks a lot
 I created what is called the terminal or a folder in etc / dtc
 then I deleted the config files and I re-created
best regards

---


---
title: "serious problem with last openoffice.org update"
date: 2010-02-25
forum: General Help
---

### Post by euux on 2010-02-25
hi, 
2 days ago the update manager presented me with an update to several  openoffice.org components - as usual i've allowed the installation BUT i got an error during the installation process:
```
E: /var/cache/apt/archives/openoffice.org-core_1%3a3.1.1-5ubuntu1.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.1/program/libcuili.so')
```

The instalation terminal was showing me this:
```
Setting up ure (1.5.1+OOo3.1.1-5ubuntu1.1) ... 
dpkg: dependency problems prevent configuration of openoffice.org-emailmerge: openoffice.org-emailmerge depends on python-uno; however: Package python-uno is not configured yet. 
dpkg: error processing openoffice.org-emailmerge (--configure): dependency problems - leaving unconfigured Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
openoffice.org 
openoffice.org-impress 
openoffice.org-officebean 
openoffice.org-base 
openoffice.org-math 
openoffice.org-draw 
openoffice.org-calc 
openoffice.org-filter-binfilter 
openoffice.org-report-builder-bin 
openoffice.org-base-core 
openoffice.org-writer 
python-uno 
openoffice.org-emailmerge
```
It ended recommending me to check the Broken filter in Synaptic. I've tried to reinstall and later tried a removal followed by install (:/)

Now, i have no openoffice. Synaptic is proposing an update to openoffice.org-core that whenever i try to follow ends with the same error.

Has anyone got this problem? What do you suggest?

I've found another thread about this same update (but not this problem) with update package manager screen shots.
[http://ubuntuforums.org/showthread.php?t=1414631](http://ubuntuforums.org/showthread.php?t=1414631)

---

### Post by amsterdamharu on 2010-02-25
> openoffice.org-emailmerge depends on python-uno; however: Package python-uno is not configured yet. 

Is python-uno installed? Maybe try to re-install that package in synaptic package manager (under system -> administration) and then try re-install openoffice then update manager.

---

### Post by euux on 2010-02-25
hi amsterdamharu, thanks, 

i've uninstalled everything openoffice and python-uno. When marking python-uno Synaptic requests that openoffice.org-core and -common be also marked for installation. Upon applying i get the same error; the details of the  installation are somewhat different:
```
Selecting previously deselected package openoffice.org-common.
(Reading database ... 251789 files and directories currently installed.)
Unpacking openoffice.org-common (from .../openoffice.org-common_1%3a3.1.1-5ubuntu1.1_all.deb) ...
Unpacking openoffice.org-core (from .../openoffice.org-core_1%3a3.1.1-5ubuntu1.1_i386.deb) ...
lzma: Decoder error 
dpkg-deb: subprocess <decompress> returned error exit status 1 
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a3.1.1-5ubuntu1.1_i386.deb (--unpack): 
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/basis3.1/program/libcuili.so') 
No apport report written because the error message indicates a dpkg I/O error 
Selecting previously deselected package python-uno. 
Unpacking python-uno (from .../python-uno_1%3a3.1.1-5ubuntu1.1_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 

Unknown media type in type 'all/allfiles' 

Unknown media type in type 'uri/mms' 

Unknown media type in type 'uri/mmst' 

Unknown media type in type 'uri/mmsu' 

Unknown media type in type 'uri/pnm' 

Unknown media type in type 'uri/rtspt' 

Unknown media type in type 'uri/rtspu' 

Unknown media type in type 'fonts/package' 

Unknown media type in type 'interface/x-winamp-skin' 
Processing triggers for desktop-file-utils ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/openoffice.org-core_1%3a3.1.1-5ubuntu1.1_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1) 
A package failed to install. Trying to recover: 
Setting up openoffice.org-common (1:3.1.1-5ubuntu1.1) ... 

dpkg: dependency problems prevent configuration of python-uno: python-uno depends on openoffice.org-core (= 1:3.1.1-5ubuntu1.1); however: 
 Package openoffice.org-core is not installed. 
dpkg: error processing python-uno (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: python-uno
```
To me it looks that python-uno depends on openoffice.org-core and the reverse !.. :confused:
This time I note also and error with lzma, (exceedingly) soon on the installation detail.

---

### Post by amsterdamharu on 2010-02-25
There seems to be a problem with one of the deb files, maybe it was half downloaded and then apt crashed or something. Since the file is in cache maybe apt thinks it's ready for use.

You might try to remove it and then install:

```
sudo su
rm /var/cache/apt/archives/openoffice.org-core*
apt-get update
apt-get install python-uno
```

Since python-uno depends on openoffice.org-core it will be installed as well.

---

### Post by euux on 2010-02-25
well, now, after reading your kind reply,  i'm quite proud of myself.
I've uninstalled everything openoffice. Found some caches with locate (after updatedb) and tried:
```
sudo rm -f /var/cache/apt/archives/openoffice*.deb
```
reinstalled lzma and lib_lzma_something (just for insurance)
and voilá, looks OK.

Thank you vary much for the attention spared. Cheers!

---

### Post by unelsson on 2010-02-27
I have this problem because I accidentally switched off the power during openoffice update. None of the tips mentioned here or else seem to help. 

This is what terminal says after "sudo apt-get python-uno" and pretty much the same result with "sudo apt-get -f install"
```
Seuraavat paketit asennettiin automaattisesti, eivätkä ne ole enää vaadittuja:
  openoffice.org-filter-mobiledev openoffice.org-filter-binfilter openoffice.org-report-builder-bin openoffice.org-officebean
Poista ne komennolla "apt-get autoremove".
Nämä paketit päivitetään:
  python-uno
1 päivitetty, 0 uutta asennusta, 0 poistettavaa ja 1 päivittämätöntä.
2 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 0t/96,7kt.
Toiminnon jälkeen käytetään 0 t lisää levytilaa.
(Luetaan tietokantaa... 270969 tiedostoa ja hakemistoa tällä hetkellä asennettuna.)
Valmistellaan paketin python-uno 1:3.1.1-5ubuntu1 vaihtamista (käyttäen pakettia .../python-uno_1%3a3.1.1-5ubuntu1.1_i386.deb)...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1644, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: varoitus: vanha pre-removal-komentosarja palautti virheen! Annetaan exit status arvolla 1 ja poistutaan
dpkg - koitetaan uuden paketin komentosarjaa...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1644, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: virhe käsiteltäessä /var/cache/apt/archives/python-uno_1%3a3.1.1-5ubuntu1.1_i386.deb (--unpack):
 aliprosessi uusi pre-removal-komentosarja palautti virhetilakoodin 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1478, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 279, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: virhe jälkipuhdistuksessa:
  aliprosessi installed post-installation script palautti virhetilakoodin 1
Käsittelyssä tapahtui liian monta virhettä:
 /var/cache/apt/archives/python-uno_1%3a3.1.1-5ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by amsterdamharu on 2010-02-27
Not sure what version of python is installed, you can check in synaptic package manager under system -> administrative task (I think). 
[http://packages.ubuntu.com/karmic/python](http://packages.ubuntu.com/karmic/python)
[http://packages.ubuntu.com/karmic-updates/python](http://packages.ubuntu.com/karmic-updates/python)

Your version might be too new/old, don't know if re install will help after removing 3rd party repositorys (I think it's somewhere under administrative task called software sources and in the menu of synaptic package manager called software sources). Un check 3rd party and try to re-install python, install openoffice, activate the 3r party, refresh and update (other software might be needing the newer python).

You can right click the python package and choose properties to see what version it is and where it came from. Do not uninstall it as many other packages might depend on it and you end up uninstalling half your system.

---

### Post by unelsson on 2010-02-27
The error persists without 3rd party repositories, I don't normally use them anyway. I also tried with all of the Ubuntu Karmic repositories, but error still the same.

---

### Post by Hagar Delest on 2010-02-27
Try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by euux on 2010-03-05
hi, between amsterdamharu and the solution that worked for me there is a difference and most notably in both suggestions python-uno deb file would not be removed.
amsterdamharu:
```
sudo rm /var/cache/apt/archives/openoffice.org-core*
```
euux:
```
sudo rm -f /var/cache/apt/archives/openoffice*.deb
```
In your place, I'd do a 
```
find /var/cache/apt/archives/ -type f -iname "*python-uno*.deb"
```
If it returns something, do:
```
sudo find /var/cache/apt/archives/ -type f -iname "*python-uno*,deb" -exec rm {} \;
```
Then try to reinstall openoffice.org

---

### Post by Zeitlos on 2010-03-06
Hi @ all

First of all I'm a total noob trying to get along with ubuntu... using it for a couple of weeks now.. 

I've also got the problem trying to update the following package: 

 "uno-libs3"  
My bugreport says: E: /var/cache/apt/archives/uno-libs3_1.5.1+OOo3.1.1-5ubuntu1.1_i386.deb: Unterprozess dpkg-deb --control gab den Fehlerwert 2 zurück
   that's in english: "subprocess-dpkg-deb --control returned error/bugvalue 2

I tried everything you guys said in this thread, but nothing worked. 

I really do need open office and appreciate your help.

Edit:
If there is any other windows office clone I'd really like to test it. Have to work on different papers for university and that's why I need open office or something similar.

---

### Post by euux on 2010-03-09
hi, you say you've tried everything in this thread.. 
..hmmm, literally, or did you adapt for your case? Like deleting, from the /var/cache/apt/archives/ folder, the file with file name with uno-libs3 and ending with .deb? Something like:```
sudo rm -f /var/cache/apt/archives/*uno-libs3*.deb
```
After this, you'll have to (re)install openoffice.org.
hope this helps... you know I'm this thread's original ignorant, right? :-\"

---


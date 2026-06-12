---
title: "Software Center package catalog &quot;needs repaired&quot;?!?!"
date: 2012-09-27
forum: General Help
---

### Post by Eirreann on 2012-09-27
Okay, so I was trying to install some games from the 5th Humble Bundle on a relatively new install of Ubuntu 12.04.  Anyway, I downloaded and uninstalled the game LIMBO from the Humble Bundle website (in the form of a .deb file) but then I found out that I'm supposed to "activate" it, to show that I own the game, by opening it from a link titled "Download for Ubuntu".  I did this, too, and it began to install LIMBO for a second time.  Then a pop-up appeared, saying "Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now?"  I clicked "repair", and moments later, another pop-up appears, saying "An Unhandleable Error has occured; There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks." The details of this error are:
```
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 226, in _process_transaction
    self._apply_changes(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/pkcompat.py", line 2860, in _apply_changes
    install_range)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 987, in _apply_changes
    self._cache.commit(fetch_progress, inst_progress)
  File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 481, in commit
    res = self.install_archives(pm, install_progress)
  File "/usr/lib/python2.7/dist-packages/apt/deprecation.py", line 98, in deprecated_function
    return func(*args, **kwds)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 443, in install_archives
    install_progress.start_update()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/progress.py", line 390, in start_update
    lock.status_lock.release()
  File "/usr/lib/python2.7/dist-packages/aptdaemon/lock.py", line 83, in release
    os.close(self.fd)
OSError: [Errno 9] Bad file descriptor
```
When I click okay, the "Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now?" pops up again, but this time, the next pop-up to appear says "Package Operation Failed; The installation or removal of a software package failed." With the details of this error being:
```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 180486 files and directories currently installed.)
Unpacking limbo-bin:i386 (from .../limbo-bin_1.3-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/limbo-bin_1.3-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/opt/limbo/lib/wine/mmdevldr.vxd.so', which is also in package ia32-limbo 1.3-1
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/limbo-bin_1.3-0ubuntu1_i386.deb
Error in function: 
dpkg: dependency problems prevent configuration of limbo:
 limbo depends on limbo-bin (= 1.3-0ubuntu1); however:
  Package limbo-bin is not installed.
dpkg: error processing limbo (--configure):
 dependency problems - leaving unconfigured
```
Then the "Items cannot be installed or removed until the package catalog is repaired.  Do you want to repair it now?" error pops up again, and the process repeats, over and over again!  HELP!!!

---

### Post by Eirreann on 2012-09-27
EDIT:  Just noticed there's a red icon in the upper right corner (next to the mail icon) which says "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong.  The error message was 'Error: BrockenCount > 0'.  This usually means that your installed packages have unmet dependencies."  Under it there is an option to go to the Update Manager.  Well, when I go to the update manager and try to install these six new updates, I get an error saying "Task cannot be monitored or controlled

The connection to the daemon was lost. Most likely the background daemon crashed."
The details say ```
It seems that the daemon died. 
```
I get another error message saying "The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f"
With the details saying ```
The following packages have unmet dependencies:

limbo: Depends: limbo-bin (= 1.3-0ubuntu1) but it is a virtual package
```
I tried using the "apt-get" command, and the "apt-get install -f" command, but they didn't seem to help anything!  (or even make sense [to me, anyway]).  PLEASE HELP SOMEONE!

---

### Post by jerrrys on 2012-09-27
In terminal:

sudo apt-get clean

sudo apt-get update

See if you get lucky :)

---

### Post by cortman on 2012-09-27
OR, run

```
sudo rm /var/cache/apt/archives/*
```

Then

```
sudo apt-get install -f
```

---

### Post by Eirreann on 2012-09-27
> **jerrrys said:**
> In terminal:

sudo apt-get clean

sudo apt-get update

See if you get lucky :)

I tried it, and absolutely nothing happened...

---

### Post by Eirreann on 2012-09-27
> **cortman said:**
> OR, run

```
sudo rm /var/cache/apt/archives/*
```

Then

```
sudo apt-get install -f
```

I tried this too, and this is what happened after it finished whatever it was doing with the % (downloading?):
```
Unpacking limbo-bin:i386 (from .../limbo-bin_1.3-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/limbo-bin_1.3-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/opt/limbo/lib/wine/mmdevldr.vxd.so', which is also in package ia32-limbo 1.3-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/limbo-bin_1.3-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And I'm still getting the package catalog needs repaired error...

---

### Post by jerrrys on 2012-09-27
Im thinking remove (purge) Limbo, but not sure how these paid games work.  Any thoughts on that Captain Jack (aka cortman) .. :)

---

### Post by Eirreann on 2012-09-27
> **jerrrys said:**
> Im thinking remove (purge) Limbo, but not sure how these paid games work.  Any thoughts on that Captain Jack (aka cortman) .. :)

I did try removing it, but apparently I can't install or uninstall anything because of those issues previously mentioned...

---

### Post by HiImTye on 2012-09-27
the issue you are having is that you have a version of a dependency installed that is greater than the version the package you are trying to install depends on, and the package you are trying to install depends on a *specific* version of that package (=), rather than a version that is *greater than or equal to* a version of that package (>=). the issue is with the package itself, unfortunately. your best bet is to find the version of the package that it requires and installing that.

> trying to overwrite '/opt/limbo/lib/wine/mmdevldr.vxd.so', which is also in package **ia32-limbo 1.3-1**> limbo: Depends: limbo-bin (**[COLOR=DarkRed]=[/COLOR] 1.3-0ubuntu1**) but it is a virtual package


---

### Post by cortman on 2012-09-27
Maybe your best bet would be to go to packages.ubuntu.com/precise and download ia32-libs-multiarch (that package seems to include older versions) and install it with dpkg.
Just an idea.

---

### Post by Eirreann on 2012-09-27
> **cortman said:**
> Maybe your best bet would be to go to packages.ubuntu.com/precise and download ia32-libs-multiarch (that package seems to include older versions) and install it with dpkg.
Just an idea.

Okay, I'll give that a go...but how exactly do I do that?  Install something with dpkg??

---

### Post by cortman on 2012-09-27
> **Eirreann said:**
> Okay, I'll give that a go...but how exactly do I do that?  Install something with dpkg??

Download the .deb file and navigate in the terminal to its directory. Run

```
sudo dpkg -i file_name
```

to install.

---

### Post by Eirreann on 2012-09-28
> **cortman said:**
> Download the .deb file and navigate in the terminal to its directory. Run

```
sudo dpkg -i file_name
```

to install.
I think you overestimate my skills with Linux just a bit, haha!  I'm a serious noob here!
So how do I navigate to it's directory using the terminal?

---

### Post by Eirreann on 2012-09-28
Okay, I can't find the  ia32-libs-multiarch package on that page that you linked, and I still don't know how to install it using dpkg!  Please help!!!

---

### Post by Eirreann on 2012-09-28
After finding no solution, I just re-installed Ubuntu... now everything is fine and LIMBO works great!

---


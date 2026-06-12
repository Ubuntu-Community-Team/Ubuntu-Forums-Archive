---
title: "Packages locked. APT Install always gives error."
date: 2009-11-07
forum: General Help
---

### Post by arielon on 2009-11-07
*So this one was posted [here]("http://ubuntuforums.org/showthread.php?p=8268532#post8268532"), starting to try to follow their recommendation to erase the locks, but I thought I reposted in a new thread as there it says [solved] and it isn't for me... Thanks...*

Ok, supers, here's my little one, to see if u can lend me a hand...):P

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.12.4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)
```currently doing the .private thing... (dunno if is right) with fakeroot.private ([find -name fakeroot.private], as i don't know where to look).

Thanks!

Edit1: Nothing found with ```
sudo find / -name fakeroot.private
```Edit2: The output following what says [here]("http://linux.derkeiler.com/Mailing-Lists/Debian/2006-06/msg01254.html") is the same as the one above.
Edit3: Solution found.

[This post]("http://ubuntuforums.org/showpost.php?p=7234436&postcount=6") put me in the right track.

<code>
Open terminal and:
[COLOR=DarkGreen]cd /var/lib/dpkg/info[/COLOR]

I then issue:
[COLOR=DarkGreen]rm packagename.post*[/COLOR]
where packagename is the package I'm having issues with (in my case the scripts were empty which caused the errors).

Then I used this:
[COLOR=DarkGreen]apt-get --purge remove packagename[/COLOR]
where packagename is the package name I'm having issues with.</code>


Did that for 
```
 bcmwl-kernel-source
 fakeroot

```but in my case, i had to remove all the files (not only the *.post). Moved them to a backup folder (just in case) and got:

```

dpkg: warning: files list file for package `bcmwl-kernel-source' missing, assuming package has no files currently installed.
(Reading database ... 139454 files and directories currently installed.)                                                    
Removing bcmwl-kernel-source ... 
```Great! After they were removed, I could reinstall fakeroot (bcmwl was not needed, using closed source drivers).

Installed sudoku (apt-get install sudoku) and voila! No problems.:p

(same for fakeroot)

---

### Post by fancypiper on 2009-11-07
In an x-terminal, type this command:

sudo rm /var/lib/dpkg/lock

---

### Post by arielon on 2009-11-07
> **fancypiper said:**
> In an x-terminal, type this command:

sudo rm /var/lib/dpkg/lock


Yeah, saw that, but wanted to do this as the last resource... Thank you.

---

### Post by IAmAnirban on 2009-12-11
> **arielon said:**
> *So this one was posted [here]("http://ubuntuforums.org/showthread.php?p=8268532#post8268532"), starting to try to follow their recommendation to erase the locks, but I thought I reposted in a new thread as there it says [solved] and it isn't for me... Thanks...*

Ok, supers, here's my little one, to see if u can lend me a hand...):P

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.12.4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)
```currently doing the .private thing... (dunno if is right) with fakeroot.private ([find -name fakeroot.private], as i don't know where to look).

Thanks!

Edit1: Nothing found with ```
sudo find / -name fakeroot.private
```Edit2: The output following what says [here]("http://linux.derkeiler.com/Mailing-Lists/Debian/2006-06/msg01254.html") is the same as the one above.
Edit3: Solution found.

[This post]("http://ubuntuforums.org/showpost.php?p=7234436&postcount=6") put me in the right track.

<code>
Open terminal and:
[COLOR=DarkGreen]cd /var/lib/dpkg/info[/COLOR]

I then issue:
[COLOR=DarkGreen]rm packagename.post*[/COLOR]
where packagename is the package I'm having issues with (in my case the scripts were empty which caused the errors).

Then I used this:
[COLOR=DarkGreen]apt-get --purge remove packagename[/COLOR]
where packagename is the package name I'm having issues with.</code>


Did that for 
```
 bcmwl-kernel-source
 fakeroot

```but in my case, i had to remove all the files (not only the *.post). Moved them to a backup folder (just in case) and got:

```

dpkg: warning: files list file for package `bcmwl-kernel-source' missing, assuming package has no files currently installed.
(Reading database ... 139454 files and directories currently installed.)                                                    
Removing bcmwl-kernel-source ... 
```Great! After they were removed, I could reinstall fakeroot (bcmwl was not needed, using closed source drivers).

Installed sudoku (apt-get install sudoku) and voila! No problems.:p

(same for fakeroot)
:D  Thanks a lot !!!!! Same problem same solution !!! My problem was with the wireless driver. Thanks once again to all you guys

---


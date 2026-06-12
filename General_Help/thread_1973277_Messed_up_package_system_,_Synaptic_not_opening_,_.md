---
title: "Messed up package system , Synaptic not opening , cannot remove any packages"
date: 2012-05-04
forum: General Help
---

### Post by alamban on 2012-05-04
t seems I have messed up all of the package installation system in ubuntu. This was the error it appeared on my system first. I was unable to open synaptic then-->[INDENT]   ```
E: Encountered a section with no Package: header
  E: Problem with MergeList /var/lib/dpkg/status    E: The package lists or status file could not be parsed or opened.
``` [/INDENT]Then as answered in the forum  [[http://www.linuxquestions.org/questions/debian-26/apt-dpkg-errors-var-lib-dpkg-status-155478/]](http://www.linuxquestions.org/questions/debian-26/apt-dpkg-errors-var-lib-dpkg-status-155478/])[1]   I executed the following commands..[INDENT]   ```
mv /var/lib/dpkg/status __/var/lib/dpkg/status_bak
cp /var/backups/dpkg.status..gz __/var/lib/dpkg/
gunzip -d /var/lib/dpkg/dpkg.status..gz
mv /var/lib/dpkg/dpkg.status. __/var/lib/dpkg/status
apt-get update
``` [/INDENT]After this the first error messege stopped even though synaptic was  not opening.But now I m not able to uninstall any packages even if they  are installed..
  For eg: when i try to uninstall vlc ,it shows[INDENT]   ```
ajith@ajith-pc:~$ sudo apt-get remove vlc Reading package lists...   Done Building dependency tree        Reading state information... Done   Package vlc is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
``` [/INDENT]Can anyone please help?

---

### Post by 2ta8gdfte on 2012-05-04
Run a sudo apt-get update in the terminal and post all the readout. Your link is also dead.

---

### Post by PhantomTurtle on 2012-05-04
> **2ta8gdfte said:**
> Run a sudo apt-get update in the terminal and post all the readout. Your link is also dead.

Link isn't dead, he just typed it in wrong. Remove the "]" at the end.

amamban, have you tried this: [http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/]("http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/"). The comments says it worked.

EDIT: also it says it's for 11.04, but it will other versions as well.

---

### Post by alamban on 2012-05-05
> **2ta8gdfte said:**
> Run a sudo apt-get update in the terminal and post all the readout. Your link is also dead.

It is updating cache properly.
No errors.

---

### Post by alamban on 2012-05-05
> **PhantomTurtle said:**
> Link isn't dead, he just typed it in wrong. Remove the "]" at the end.

amamban, have you tried this: [http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/). The comments says it worked.

EDIT: also it says it's for 11.04, but it will other versions as well.


it is to fix MergeList /var/lib/apt/lists.That is not the problem with me.Nevetheless,I had tried it.It was of no use.The problem persisted.

---


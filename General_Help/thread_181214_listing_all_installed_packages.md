---
title: "listing all installed packages"
date: 2006-05-23
forum: General Help
---

### Post by grajea01 on 2006-05-23
Good evening.. I have two questions concerning package handling, hopefully one or both will be answered in here..

First of all, I'd like to put a cron job where all (correctly) installed packages will be listed into a file. Something like dpkg --list-installed >/.packagelist.txt
(of course the --list-installed option I just made up).

Is there an easy way ? I tried parsing the /var/lib/dpkg/status file, without any success.


Second question.. Let's say I have package ubuntu-bin-1.0.0.deb which is broken. At some apt-get upgrade it tried to install it. I dpkg -P the package because of that. How can I make sure it won't reappear at the next apt-get dist-upgrade or apt-get dselect-upgrade since I know the package to be borked , without having to put it in hold status with dselect ?

I actually have this problem with artwiz-cursor, btw. It used to reappear whenever an apt-get dist-upgrade is scheduled.

Hoping to get an answer.

Jeff

---

### Post by kaydub on 2006-05-23
I can help with the first part.  

"dpkg -l > filename"

The dash ell just tells it to list.  You can add pattern matching after the -l to get specific packages.

Will list all of the "properly" installed applications

Note that you can proceed that with COLUMNS=xxx to get a wider format output into your file (where xxx is some number like 120).  This file can then be processed by a spreadsheet type application, which is very handy for referencing your installed packages.

Hope this helps...

BTW, if it was a snake it would have bit ya...

---

### Post by meng on 2006-05-23
Something like:
dpkg --list > output.txt
--
edit: beaten to the punch

---

### Post by grajea01 on 2006-05-23
damned.. and I missed that one ??? It's straight out of the man pages :(

Sorry for being a dunce, _that_ one I should have thought about. Now let's hope someone will be able to help me out with the second question..


Thanks meng, kaydub

-- Jeff

---

### Post by ifokkema on 2006-05-24
[QUOTE=grajea01]Second question.. Let's say I have package ubuntu-bin-1.0.0.deb which is broken. At some apt-get upgrade it tried to install it. I dpkg -P the package because of that. How can I make sure it won't reappear at the next apt-get dist-upgrade or apt-get dselect-upgrade since I know the package to be borked , without having to put it in hold status with dselect ?

I actually have this problem with artwiz-cursor, btw. It used to reappear whenever an apt-get dist-upgrade is scheduled.[/QUOTE]

Hi,

If I understand correctly, you want to lock a version.
I've got Breezy myself, but this is how I do it:
'Applications' -> 'Add aplication'.
<Type in your password>
Select 'File' -> 'Advanced'.
Select your package in the top right-hand viewing pane.
Select in the menu: 'Package' -> 'Lock version'.

The option 'Package' -> 'Force version' might be of interest to you, too.

Hope this helps!

Ivo

---


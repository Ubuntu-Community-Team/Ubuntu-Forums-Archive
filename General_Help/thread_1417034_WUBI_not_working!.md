---
title: "WUBI not working!"
date: 2010-02-26
forum: General Help
---

### Post by MrDanielson on 2010-02-26
Hey guys (and girls)!
WUBI isn't working at me - I really don't know what can be wrong - it has worked before, but after i removed ubuntu and I now want it again, WUBI just isnt working. I get this error message:

[IMG]http://localhostr.com/files/408a0c/wubi.png[/IMG]

Which does mean on english:
There is no disc in the disc-drive. Insert a disc in \Device\Harddisk1\DR1.

I really don't understand what's wrong, and to close that window i need to go into the task manager and close pyrun.exe.
I have my Ubuntu 9.10 with WUBI on a CD disc, so it can't be that?

Uhm, I hope someone can help me - I would really appreciate it :)

Oh, by the way, my OS is : Windows Vista 64-bit.

Thanks :D

---

### Post by MrDanielson on 2010-02-27
Bump

---

### Post by jmszr on 2010-02-27
MrDanielson,

If you install Wubi from here: [http://wubi-installer.org/](http://wubi-installer.org/) there is no need to use a CD.

This doesn't answer why it is not working the way you are trying, but it does install Wubi for you. You do, of course, need to defrag a couple of times before you install Wubi.

Here is some more information: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) and: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) 

 It's been a while since I used Wubi, but these instructions seem to be correct- #'s 3 & 4 here inparticularly (for installing from CD): [http://seogadget.co.uk/the-ubuntu-installation-guide/](http://seogadget.co.uk/the-ubuntu-installation-guide/). (Of course if your CD is not being recognized,they don't really matter.)
 
Edit: More information

---

### Post by oldfred on 2010-02-27
After you install it you will want to run this fix.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by MrDanielson on 2010-02-28
Hmm, I tried all you guys wrote but didn't work. Oh well at least it started the installation this time but crashes after some time and says:
[IMG]http://localhostr.com/files/3dceca/ubuntu.jpg[/IMG]

I dont know if i should upload the file?

---

### Post by lisati on 2010-02-28
Edit: accidental double post.

---

### Post by lisati on 2010-02-28
> **MrDanielson said:**
> Hey guys (and girls)!
WUBI isn't working at me - I really don't know what can be wrong - it has worked before, but after i removed ubuntu and I now want it again, WUBI just isnt working. I get this error message:

[IMG]http://localhostr.com/files/408a0c/wubi.png[/IMG]

Which does mean on english:
There is no disc in the disc-drive. Insert a disc in \Device\Harddisk1\DR1.

I really don't understand what's wrong, and to close that window i need to go into the task manager and close pyrun.exe.
I have my Ubuntu 9.10 with WUBI on a CD disc, so it can't be that?

Uhm, I hope someone can help me - I would really appreciate it :)

Oh, by the way, my OS is : Windows Vista 64-bit.

Thanks :D
The error could be related to this: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by MrDanielson on 2010-02-28
> **lisati said:**
> The error could be related to this: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)
Thanks, but it didn't help :|

---

### Post by MrDanielson on 2010-03-01
bump 8)

---

### Post by bribok on 2010-03-02
> **MrDanielson said:**
> Hmm, I tried all you guys wrote but didn't work. Oh well at least it started the installation this time but crashes after some time and says:
[IMG]http://localhostr.com/files/3dceca/ubuntu.jpg[/IMG]

I dont know if i should upload the file?

The same error message appeared to me and i solved it cleaning up the registry and everything with CCleaner and running Wubi as the Administrator.
Hope it work for you too!

---

### Post by Gstrazds on 2010-05-04
> **bribok said:**
> The same error message appeared to me and i solved it cleaning up the registry and everything with CCleaner and running Wubi as the Administrator.
Hope it work for you too!

I also am having this identical problem...

I already have a very clean registry and am logged in as administrator.

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-04 15:05 DEBUG  TaskList: # Cancelling tasklist
05-04 15:05 DEBUG  TaskList: # Finished tasklist
05-04 15:05 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-04 15:05 INFO   root: Received settings

I could upload the whole file..
Plan B would to make an ISO which is downloading now..

thanks

---

### Post by Gstrazds on 2010-05-04
Hi there .. Got it to work after clicking run as administrator ? third time..

and now I have a first grub screen; not bootable - my failed upgrade 10.4 Ubuntu and sda1 where I then boot into the sda1 winloader where I can boot vista or Ubuntu - booting Ubuntu gets me another grub session which lets me boot into WUBI 

which does not have my proprietary Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter driver which was in my 9.4 ubuntu install.

So did everything get over written on the Linux partition?

and beyond the above I appear to have several additional problems..

two grub sessions and a win loader session? which I guess require new threads

thanks



> **Gstrazds said:**
> I also am having this identical problem...

I already have a very clean registry and am logged in as administrator.

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-04 15:05 DEBUG  TaskList: # Cancelling tasklist
05-04 15:05 DEBUG  TaskList: # Finished tasklist
05-04 15:05 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
05-04 15:05 INFO   root: Received settings

I could upload the whole file..
Plan B would to make an ISO which is downloading now..

thanks

---


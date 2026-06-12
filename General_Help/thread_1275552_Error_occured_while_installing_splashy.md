---
title: "Error occured while installing splashy"
date: 2009-09-25
forum: General Help
---

### Post by praveesh on 2009-09-25
I uninstalled usplash and tried to install splashy , but couldn't because an error occured. The output of terminal is shown below . Please help.
(Reading database ... 125590 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-3ubuntu1_i386.deb) ...
dpkg: error processing splashy_0.3.13-3ubuntu1_i386.deb (--install):
 trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base
Processing triggers for man-db ...
Errors were encountered while processing:
 splashy_0.3.13-3ubuntu1_i386.deb

---

### Post by praveesh on 2009-09-26
This is not a solved problem. I don't know how to change . If a moderator can do, please do.

---

### Post by pastalavista on 2009-09-26
How did you install splashy? It is in the repositories. You can find it with Synaptic Package Manager or I would use the terminal ```
sudo apt-get install splashy
```. Sometimes when you download deb packages fron other sources, they won't be compatible with your kernel, xorg, gnome etc. That's why it's best to use the repos whenever possible.

---

### Post by wojox on 2009-09-26
You're trying to download these from APTonCD?

---

### Post by praveesh on 2009-09-26
I  downloaded it from the official Ubuntu repository with the help of [http://packages.Ubuntu.com](http://packages.Ubuntu.com). Then I made a repository cd with it using  aptoncd . Then used synaptic to install from that cd . I have downloaded all the required dependancies and included that in the cd . When that failed, I tried to install it using gdebi . The output from that is shown in 1st post (it's different from that in the screenshot). .

---

### Post by praveesh on 2009-09-26
I downloaded an early version from the website of splashy . That also showed the same error.

---


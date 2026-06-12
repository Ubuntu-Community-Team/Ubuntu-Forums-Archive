---
title: "update and program manager chrashed - can't report"
date: 2010-10-05
forum: General Help
---

### Post by superangel on 2010-10-05
I am new to Linux, but a very happy M$ XP convert. Now running Ubuntu 10.04
Recently tried to view a video from my phonecard and was asked to download/update new apps. Now both update and program manager crashes with the following message:
  
[INDENT]Could not initialise the package information 
[/INDENT][INDENT]  An unresolvable problem occurred while initialising the package information. 
 
Please report this bug for the 'update-manager' package and try to include the following error message: 
 'E:Malformed 3rd word in the Status line, E:Error occurred while processing libgnome2-common (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'
[/INDENT] 
I then ran gksudo -d and got this:
          
    
          per@per-desktop:~$ gksudo -d synaptic 
[INDENT] No ask_pass set, using default! 
xauth: /tmp/libgksu-TY6yj9/.Xauthority 
STARTUP_ID: gksudo/synaptic/2497-0-per-desktop_TIME4253875 
cmd[0]: /usr/bin/sudo 
cmd[1]: -H 
cmd[2]: -S 
cmd[3]: -p 
cmd[4]: GNOME_SUDO_PASS 
cmd[5]: -u 
cmd[6]: root 
cmd[7]: -- 
cmd[8]: synaptic 
buffer: -- 
brute force GNOME_SUDO_PASS ended... 
No password prompt found; we'll assume we don't need a password. 
Traceback (most recent call last): 
  File "/usr/sbin/update-apt-xapian-index", line 699, in <module> 
    res = updateIndex(dbpath, addons, progress) 
  File "/usr/sbin/update-apt-xapian-index", line 340, in updateIndex 
    cache = apt.Cache(memonly=True,progress=aptprogress) 
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 86, in __init__ 
    self.open(progress) 
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 123, in open 
    self._cache = apt_pkg.Cache(progress) 
SystemError: E:Malformed 3rd word in the Status line, E:Error occurred while processing libgnome2-common (UsePackage2), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.
[/INDENT]Any ideas on how to solve this problem, please?

---

### Post by superangel on 2011-10-19
My message has been ignored on this blog - but one year later - problem solved!:razz:
Many thanks to the German Ubuntu help site - particularly to DrScott and prometheus0815 - and to my German teacher Frau Stahl (in 1966!) Vielen Dank!

**Solution:** Safety first - open terminal, copy the dpkg status file as txt to Home folder:
[INDENT]~$ **cp /var/lib/dpkg/status  $HOME/dpkg_status.txt**
[/INDENT](How a non-geek would know where this file was hiding is beyond me). Now:
Open Home folder and search for  the "libgnome2-common" entry in the dpkg_status.txt file. And bingo! I found that the status line read: "Status: install ok** ijstalled**". How that ever could happen no one knows.

Back in the terminal, now use gksudo to enable root edit in the original file:
[INDENT]~$ **gksudo gedit /var/lib/dpkg/status**
[/INDENT] search again and correct the spelling in the affected status line. Save. Job done!

From October 2010 to October 2011 there were 233 updates waiting for Lucid!

---


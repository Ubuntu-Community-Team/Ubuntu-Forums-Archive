---
title: "Filesystem woes + Files marked as archive on xp??"
date: 2011-09-25
forum: General Help
---

### Post by TheUnseenRealm on 2011-09-25
After being frustrated with windows XP and its constant security problems, not being able to trust Microsoft much any more and a various other reasons like not using propitiatory software, I have decided to switch to Linux using ubuntu 9.04 (Jaunty) a few weeks ago because I needed to use it for a specific wireless device it supported to get on the Internet. I am still fairly new to linux but am learning. I got my wireless device to work just fine following the instrctions.
 
I have some problems with my usb flash drive though and some kind of filesystem or virus problem on ubuntu.
 
First thing I noticed is that the Xorg process kept going to 100% cpu usage when I was not even using the system almost as if something else was causing it to go to 100%.
 
2nd, When mounting a usb drive the filesystem was marked as read-only after mounting it, was this caused by fstab/squashfs not mounting the usb correctly resulting in errors?
 
3rd, When rebooting back to windows XP on the internal HDD I see that all of my files on the usb drive have been marked with the &quot;Archive&quot; attribute in windows XP, this even happens when I make new blank files on the flash drive, they are always marked as archive..which is odd because It does not normally do that. After trying to access the USB the frist time switching back to xp it caused a Bluescreen of death but only once. What could cause this? It seems to have started with this one USB device then it appears to have spread to other devices. I checked with another computer and anoter new flash drive it does not seem to do it. Since it was something possibly made in Linux for Linux what can I do to remedy this? I have a few ideas myself but am looking for suggestions.
 
Also I have sice upgraded to a newer version of ubuntu 10.10 (Maverick Meerkat) since i have read 9.04 has not had much security fixes released for it in quite some time. I use 10.10 now on a usb drive but there seems to be a problem with python i receive errors when trying to install any package, the ubuntu software center does not run it attempts to load but then closes, Tried the sympatic package manager and when I tried to install anything I get these error(s) from the console: This time I even tried to run UFW
here is the result

ubuntu@ubuntu:~$ sudo ufw enable
Traceback (most recent call last):
  File "/usr/sbin/ufw", line 89, in <module>
    ui = ufw.frontend.UFWFrontend(pr.dryrun)
  File "/usr/lib/python2.6/dist-packages/ufw/frontend.py", line 158, in __init__
    self.backend = UFWBackendIptables(dryrun)
  File "/usr/lib/python2.6/dist-packages/ufw/backend_iptables.py", line 45, in __init__
    ufw.backend.UFWBackend.__init__(self, "iptables", d, files)
  File "/usr/lib/python2.6/dist-packages/ufw/backend.py", line 66, in __init__
    self.iptables_version = ufw.util.get_iptables_version(self.iptables)
  File "/usr/lib/python2.6/dist-packages/ufw/util.py", line 644, in get_iptables_version
    (rc, out) = cmd([exe, '-V'])
  File "/usr/lib/python2.6/dist-packages/ufw/util.py", line 269, in cmd
    sp = subprocess.Popen(command, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
AttributeError: 'module' object has no attribute 'Popen'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 53, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 75, in <module>
    def _command_output(command, input = None, stderr = subprocess.STDOUT):
AttributeError: 'module' object has no attribute 'STDOUT'

Original exception was:
Traceback (most recent call last):
  File "/usr/sbin/ufw", line 89, in <module>
    ui = ufw.frontend.UFWFrontend(pr.dryrun)
  File "/usr/lib/python2.6/dist-packages/ufw/frontend.py", line 158, in __init__
    self.backend = UFWBackendIptables(dryrun)
  File "/usr/lib/python2.6/dist-packages/ufw/backend_iptables.py", line 45, in __init__
    ufw.backend.UFWBackend.__init__(self, "iptables", d, files)
  File "/usr/lib/python2.6/dist-packages/ufw/backend.py", line 66, in __init__
    self.iptables_version = ufw.util.get_iptables_version(self.iptables)
  File "/usr/lib/python2.6/dist-packages/ufw/util.py", line 644, in get_iptables_version
    (rc, out) = cmd([exe, '-V'])
  File "/usr/lib/python2.6/dist-packages/ufw/util.py", line 269, in cmd
    sp = subprocess.Popen(command, stdout=subprocess.PIPE, stderr=subprocess.STDOUT)
AttributeError: 'module' object has no attribute 'Popen'

---

### Post by TheUnseenRealm on 2011-09-25
[update] Someone seems to be attacking my machine while using a live version, is there any way to trace this person? It looks like it could be coming from my own ISP, unsure who it is but they logged me out of these forums. Could use some help in detecting and tracking down the user responsible for this?

Looks like they gained ROOT temporarily and had access to my system, unsure of who it is or why but any rate I could use some help tracking them down.

---


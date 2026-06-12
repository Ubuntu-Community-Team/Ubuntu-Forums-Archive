---
title: "Upgrade 5.10 to 6.06 Issue"
date: 2006-05-17
forum: General Help
---

### Post by steelspyder on 2006-05-17
I cannot upgrade from 5.10 to Dapper.  I have tried several times](*,) .  Below is the terminal output.  It states, at the end, that the dapper.tar.gz file does not exist.  Please help resolve this issue so I can upgrade.  Thank you for your time.

:~$ gksudo "update-manager -d"
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:169: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
new_dist_available: dapper
on_button_dist_upgrade_clicked
extracting '/tmp/tmpBNCjjk/dapper.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/UpdateManager/UpdateManager.py", line 704, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py", line 211, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.4/site-packages/UpdateManager/DistUpgradeFetcher.py", line 136, in extractDistUpgrader
    tar = tarfile.open(self.tmpdir+"/"+os.path.basename(self.uri),"r")
  File "/usr/lib/python2.4/tarfile.py", line 916, in open
    return func(name, "r", fileobj)
  File "/usr/lib/python2.4/tarfile.py", line 959, in gzopen
    fileobj = file(name, mode + "b")
IOError: [Errno 2] No such file or directory: '/tmp/tmpBNCjjk/dapper.tar.gz'

---

### Post by mitrellim on 2006-05-18
I fixed this issue by manually editing my sources.list file to dapper instead of breezy.

Simply go to the directory /etc/apt
Then type sudo gedit sources.list
find "replace" under one of the drop down menus
then replace all the words breezy to dapper
save and exit from the sources.list
then run your normal synaptic or updates section and you will have 6.06 

Mit Rellim

---

### Post by aysiu on 2006-05-18
This is the second time I've seen that command fail.

I'm with mitrellim on this. Go the traditional route:
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by steelspyder on 2006-05-18
Thanks mitrellim.  That worked great.  I have upgraded and I am testing the new release.  I appreciate the help.  I looked all over the net and found many other people with the same issue but, no response with a solution.

Thanks again!

---

### Post by cliveau on 2006-05-29
[QUOTE=mitrellim]I fixed this issue by manually editing my sources.list file to dapper instead of breezy.

Simply go to the directory /etc/apt
Then type sudo gedit sources.list
find "replace" under one of the drop down menus
then replace all the words breezy to dapper
save and exit from the sources.list
then run your normal synaptic or updates section and you will have 6.06 

Mit Rellim[/QUOTE]



dear mitrellim, i try your method to upgrade my ubuntu 5.10 into 6.06. 
however, it seems to me that the "6.06" is not as good as i think. can you tell me how  can i uninstall 6.06 or can i just simply use the replace command to replace dapper to breezy. 

thank you

---


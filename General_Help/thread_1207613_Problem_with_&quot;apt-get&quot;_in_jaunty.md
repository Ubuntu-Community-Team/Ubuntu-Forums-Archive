---
title: "Problem with &quot;apt-get&quot; in jaunty"
date: 2009-07-08
forum: General Help
---

### Post by flandercan on 2009-07-08
Hi, All, 

I have a clean install of jaunty fully updated, only a couple of mods needed to get three screens working. I have installed vmware-workstation 6.5 using an RPM converted to DEB using alien.

Vmware-workstation 6.5 installed without issue from the DEB files and works well. 

However .......

root@susan:~# apt-get install nmap
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.
root@susan:~#


I have tried the usual clean, purge and dpkg --configure to no avail. I found the post [http://ubuntuforums.org/showthread.php?t=425887](http://ubuntuforums.org/showthread.php?t=425887) but seems to be closed. 

Jaunty runs sweet, VmWorkstation works sweet is there any way of telling apt to ignore the vmware-server package , without actually uninstalling?

thanks 
flandercan

---

### Post by pirattrev on 2009-07-08
you can try installing only the package you want through the synaptic handler (located under System -> Administration). That way you can work around the dependency in apt-get to install the full recommended package list tagged for nmap.

if there are any issues, respond quick.

---

### Post by flandercan on 2009-07-09
Hi, 

Thanks for the reply, I may have mis-understood your reply but tried running synaptic and get the following error,

E: The package vmware-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

When I click "close" the application "synaptic" does indeed close..

Im using KDE 4 so went into "system settings" and ran "Aded and Remove Software" found nmap and clicked apply.

A message box with the following appears

"A problem that we were not expecting has occurred. Please report this bug with the error description"

Traceback (most recent call last): File "/usr/lib/python2.6/dist-packages/packagekit/daemonBackend.py", line 109, in run threading.Thread.run(self) File "/usr/lib/python2.6/threading.py", line 477, in run self.__target(*self.__args, **self.__kwargs) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1399, in doGetDepends self._check_init(progress=False) File "/usr/lib/packagekit/aptDBUSBackend.py", line 1755, in _check_init self._cache.clear() File "/usr/lib/packagekit/aptDBUSBackend.py", line 246, in clear self._depcache.Init() SystemError: E:The package vmware-server needs to be reinstalled, but I can't find an archive for it. 

Thanks 
Paul

---

### Post by flandercan on 2009-08-07
Ok, I found what I think is a solution 

dpkg --remove --force-remove-reinstreq vmware-server

Vmware still runs as it did before (Havent had to reinstall) and apt now works without error.

Time to do an update, its been a while :-)


fc

---


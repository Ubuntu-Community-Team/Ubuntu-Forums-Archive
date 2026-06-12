---
title: "Webmin not working on startup/Why doesn't Ubuntu use this by default"
date: 2006-06-23
forum: General Help
---

### Post by nameiwantistaken on 2006-06-23
I have installed webmin, but it doesn't load at startup.  I have to reinstall it every time in order to get it to work.  Does anyone know of a way to force it to start?  Also, why doesn't this come pre-installed with Ubuntu?  It seems like a much better way to administer a system than anything in the Ubuntu GUI.  Anyone have any thoughts?

---

### Post by nameiwantistaken on 2006-06-24
I saw a post saying that this had something to do with run levels or something and the guy fixed it with yast.  I can't find this in the package manager and apt-get doesn't find it.  It seems I have the same problem with Oracle.

---

### Post by lamego on 2006-06-24
Where did you get the webmin from ? I am not able to find the webmin package on the ubuntu repositories.

Webmin is a web based admin interface mostly developed for servers, Ubuntu is a desktop oriented distro, it doesn't make much sense installing it as a default. 
You should have equivalent configuration tools on desktop versions.

Still about the booting, services properly packaged for ubuntu do install a boot script as default, if you need to install some manual service you can add it to the system startup, just edit /etc/rc.local an put the startup command there.

---

### Post by nameiwantistaken on 2006-06-24
I go webmin from, well, [http://webmin]("http://www.webmin.com").  Of course it makes sense to have a single place to do administrative tasks.  Windows hasn't had control panel since Windows 95 for no reason.  Plenty of people who use a desktop want to do things like web design, setup a raid to protect their data or administer a database.  The whole point of webmin is to make things easier.  I thought that the purpose of Ubuntu was the same.

Thanks for the info.  It is a good suggestion, but I have no idea how to edit a boot script or what to put in there.  I did read about Ubuntu not starting at first because of a run level problem with Ubuntu.  Any ideas about that?

On a side note, I did try uninstalling it and reinstalling it and now my machine won't boot in regular or safe mode.  Is there an OS based on linux that has things like this built in by default?

---


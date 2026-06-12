---
title: "Update manager problems"
date: 2006-04-21
forum: General Help
---

### Post by sheephead on 2006-04-21
When i run update manager, it instantly closes

When i run 
gksudo "update-manager -d"
i get this error
  File "/usr/bin/update-manager", line 874, in ?
    updatemanager.main()
  File "/usr/bin/update-manager", line 850, in main
    self.fillstore()
  File "/usr/bin/update-manager", line 648, in fillstore
    self.initCache()
  File "/usr/bin/update-manager", line 825, in initCache
    self.cache = apt_pkg.GetCache()
SystemError: E:Type '$' is not known on line 33 in source list /etc/apt/sources.list, E:The list of sources could not be read.

Help please?

---

### Post by Ubuntuud on 2006-04-21
I think you should check the 33th line of your sources.list. Maybe another Breezy user can post his/her list. My Dapper one doesn't go futher than 20 lines...

---

### Post by sheephead on 2006-04-21
My 33rd line is

 $ dpkg -i miniracer_1.XX-X_i386.deb

---

### Post by lcg on 2006-04-21
[QUOTE=sheephead]My 33rd line is

 $ dpkg -i miniracer_1.XX-X_i386.deb[/QUOTE]
There lies your problem, your sources.list should only contain lines starting with 'deb' or 'deb-src' and comments.

HTH,
Lars

---

### Post by sheephead on 2006-04-21
Ok, so how do i delete the line please?

---

### Post by _linux_ on 2006-04-21
[QUOTE=sheephead]Ok, so how do i delete the line please?[/QUOTE] To delete the line just go to the terminal and type:

```
sudo gedit /etc/apt/sources.list
```
Then just go to the 33rd line, delete it, and save the file.

---

### Post by sheephead on 2006-04-22
Thanks, problem sloved!

---


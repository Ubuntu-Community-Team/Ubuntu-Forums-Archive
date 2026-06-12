---
title: "Trying to Install FrostWire"
date: 2006-05-22
forum: General Help
---

### Post by ReviewSpin on 2006-05-22
I have put in the code (in the ternimal) "sudo dpkg -i FrostWire-4.10.9-1.i586.deb", and it did show up in my Applications menu. Problem is, I click on it, and nothingh happens. Is there something I am missing here?

---

### Post by adamkane on 2006-05-22
Add extra repositories:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

Install J2RE:
[http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://easylinux.info/wiki/Ubuntu#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

Install Frostwire:
```

cd ~/Desktop
wget http://easynews.dl.sourceforge.net/sourceforge/frostwire/FrostWire-4.10.9-1.i586.deb
sudo dpkg -i FrostWire-4.10.9-1.i586.deb 
rm -f ~/FrostWire-4.10.9-1.i586.deb 

```

---


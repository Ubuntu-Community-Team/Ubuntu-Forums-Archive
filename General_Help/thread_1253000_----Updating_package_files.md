---
title: "----Updating package files"
date: 2009-08-29
forum: General Help
---

### Post by bzhao on 2009-08-29
how can i updating files (because some files are missing) without without executing install scripts?
Current I am using the command apt-get install --reinstall packagename. But I feel it will execute install scripts 

I know rpm can do that easily, I did chech manpage for apt-get for some time and fail to have a clear option for that.

Thanks in advance
BillZ

---

### Post by SoftwareExplorer on 2009-08-29
Not quite sure what you want. If reinstall, it will uninstall, but not remove configuration files, and then install again, running any install scripts.

---

### Post by NoaHall on 2009-08-29
sudo apt-get update
sudo apt-get upgrade
sudo dpkg-reconfigure $Package name

---

### Post by bzhao on 2009-08-29
Actually I need the equivalent of apt-get :

rpm --freshen --noscripsts xxx.i386.rpm

---

### Post by SoftwareExplorer on 2009-08-30
Well, I did some googling and I found a bug that complains that dpkg doesn't allow doing this, not sure if the bug is fixed, but that might give you an idea of what is possible. By the way, apt-get is a front end for dpkg that handles dependencies and such.

---

### Post by bzhao on 2009-09-01
After a lot time of seeing the manpage of apt-get and dpkg manpage.
I got a idea to do that.

the steps are:

apt-get install -d xxx
dpkg --unpack /var/cache/apt/archives/xxx.release.deb


Bill Z

---


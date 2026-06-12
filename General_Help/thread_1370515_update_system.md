---
title: "update system"
date: 2010-01-02
forum: General Help
---

### Post by coffeecake on 2010-01-02
i have ubuntu 7.10 installed in a vmware workstation virtual machine. My problem is that i cannot update it.

Error message that i get is

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences

How can i get around this problem

please help

---

### Post by Cheesemill on 2010-01-02
Ubuntu 7.10 has reached end of life and is now no longer supported.

The repositories have been moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by coffeecake on 2010-01-02
so how can i change the update location of ubuntu?

---

### Post by kevinatkins on 2010-01-02
Now would probably be a good time to upgrade to 8.04 which is an LTS release...

---

### Post by Cheesemill on 2010-01-02
You can edit your /etc/apt/sources.list file and change all the URLs (for example from archive.ubuntu.com to old-releases.ubuntu.com)

---


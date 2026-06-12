---
title: "Uninstall unetbootin in system tools."
date: 2011-11-07
forum: General Help
---

### Post by drofart on 2011-11-07
Hello all,
         Didn't get it, But I had installed unetbootin to make live usb & it works. Now when i want to uninstall it through software center it is showing that it is not installed but it is in my system tools. Dont know how to uninstall it completely .I had tried 'sudo apt-get remove unetbootin" without success.
Wat to do ?How to do?

Thanks

Mrinal.

---

### Post by raja.genupula on 2011-11-07
Hi man do this 

```
sudo apt-get remove --purge unetbootin
```

if you got any errors please post here.

---

### Post by gandaran on 2011-11-07
> **drofart said:**
> Hello all,
         Didn't get it, But I had installed unetbootin to make live usb & it works. Now when i want to uninstall it through software center it is showing that it is not installed but it is in my system tools. Dont know how to uninstall it completely .I had tried 'sudo apt-get remove unetbootin" without success.
Wat to do ?How to do?

Thanks

Mrinal.
how did you install it or what package was used, you can only remove applications from software center if you used it install or a .deb package install, any other type of package doesn't show up on software center.

---

### Post by drofart on 2011-11-07
> **raja.genupula said:**
> Hi man do this 

```
sudo apt-get remove --purge unetbootin
```if you got any errors please post here.
Thank you raja here is the out come.

> **gandaran said:**
> how did you install it or what package was  used, you can only remove applications from software center if you used  it install or a .deb package install, any other type of package doesn't  show up on software center.
  ya , but to my memory i did it through usc or in terminal. if their is any other way to uninstall plz let me know, so that i can try those.

Thank you for ur help,

Mrinal

---

### Post by gandaran on 2011-11-07
type in terminal and paste here the output
```
sudo updatedb
```
then
```
locate unetbootin
```
this is just to find where and what unetbootin files are installed

---

### Post by drofart on 2011-11-08
> **gandaran said:**
> type in terminal and paste here the output
```
sudo updatedb
```then
```
locate unetbootin
```this is just to find where and what unetbootin files are installed
Thank you gandaran , every thing went fine but cant uninstall . Giving the out come in attachment.
If any thing can be done!

---

### Post by hhh on 2011-11-08
Unetbootin is currently uninstalled but some configuration files were left behind the first time round. Reinstall and purge should clear those out...
```
sudo apt-get install unetbootin
```
```
sudo apt-get purge unetbootin
```
And then if you want (but double check what packages will get removed)...```
sudo apt-get --purge autoremove
```
```
sudo apt-get clean
```

Edit: apt is showing that 6 packages can be upgraded as well.
```
sudo apt-get upgrade
```

To check for missing dependencies or if the install/upgrade fails...
```
sudo apt-get -f install
```
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by drofart on 2011-11-08
> **hhh said:**
> Unetbootin is currently uninstalled but some configuration files were left behind the first time round. Reinstall and purge should clear those out...
```
sudo apt-get install unetbootin
``````
sudo apt-get purge unetbootin
```And then if you want (but double check what packages will get removed)...```
sudo apt-get --purge autoremove
``````
sudo apt-get clean
```Edit: apt is showing that 6 packages can be upgraded as well.
```
sudo apt-get upgrade
```To check for missing dependencies or if the install/upgrade fails...
```
sudo apt-get -f install
```[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
Thank you hhh, problem fixed.

This is why I love ubuntu & all u folks. :)

Mrinal

---


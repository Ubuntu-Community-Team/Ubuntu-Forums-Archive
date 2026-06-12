---
title: "error on synaptic startup"
date: 2010-02-25
forum: General Help
---

### Post by dr.sehs on 2010-02-25
hi 
the problem that I face it is when I run synaptic package manger or try to install an updates from update manger this error message appear :
[PHP]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/PHP]and it close he windows after press close button in the error windows.

please I need help to fix this problem, cause now i can't install or update anything in my pc.

thanks all.

---

### Post by philinux on 2010-02-25
Close synaptic.

Open a terminal. Apps>access>Terminal

```
sudo dpkg --configure -a
```

Run the command by pressing enter. It will ask you for your password. It will not be visible so just type it in and press enter.

It's amazing that the system tells you how to correct it eh. ;)

---

### Post by dr.sehs on 2010-02-25
that's was very simple & fast, as the the simple of pressing enter button.
its work's !
thank you very much [philinux]("http://ubuntuforums.org/member.php?u=353083") for your help.

---


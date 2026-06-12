---
title: "Permission Problems"
date: 2010-01-09
forum: General Help
---

### Post by Final Version on 2010-01-09
I just installed xampp to "/opt/lampp/" and I can't even delete, create or modify files in this directory. I am the owner of the computer, the only user. I just assumed I would have all necessary permissions to do whatever.

My question being, how do I get around this, or give myself the necessary permissions. I'd rather not be having to use a terminal command every time. Anyway, thanks.

---

### Post by stoneage on 2010-01-09
You do need permissions to alter root directories in linux, it is a security feature.

Anything you do there will require using the Terminal, but an easier solution may be to use a root file manager.

Type ```
sudo nautilus
``` in a Terminal to bring up a file manager with root permissions, but as always, be very careful what you do with it.......

---

### Post by sisco311 on 2010-01-09
[thread=223410]HOWTO: Setup easy web development environment (XAMPP)[/thread]

*XAMPP by default uses /opt/lampp/htdocs as the root web directory. The easiest way to start working on files is to link a folder in your home directory into this directory.*

```
mkdir ~/public_html
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
```

[I]Now any files and folders you place in ~/public_html will be published to your personal webserver ([http://localhost/username](http://localhost/username)).
[/I]

---

### Post by rnerwein on 2010-01-09
> **Final Version said:**
> I just installed xampp to "/opt/lampp/" and I can't even delete, create or modify files in this directory. I am the owner of the computer, the only user. I just assumed I would have all necessary permissions to do whatever.

My question being, how do I get around this, or give myself the necessary permissions. I'd rather not be having to use a terminal command every time. Anyway, thanks.

hi - i think you used windows in former time - and as the only user on the system you haven't create no own account. therefor you always run asan  administrator i think. but do yourself a favour and read just a little bit about permissions. follow this link
[http://www.dartmouth.edu/~rc/help/faq/permissions.html](http://www.dartmouth.edu/~rc/help/faq/permissions.html)
it's a short and understandable description of the acces philosophie in unix/linux
ciao:D:P

---

### Post by Final Version on 2010-01-09
Thanks, I'll try all suggestions. And yes I'm a former windows user.

---

### Post by scouser73 on 2010-01-09
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by Final Version on 2010-01-10
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.
Thanks, this worked best.

---


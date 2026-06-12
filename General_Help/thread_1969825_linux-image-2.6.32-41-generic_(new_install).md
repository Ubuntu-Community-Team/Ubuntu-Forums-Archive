---
title: "linux-image-2.6.32-41-generic (new install)"
date: 2012-04-30
forum: General Help
---

### Post by Wim Sturkenboom on 2012-04-30
What the heck is it? I get this during the 10.04 LTS update.

I usually apply all updates but '*new install*' worries me big time.

Thanks in advance for your advice.

---

### Post by Tamlynmac on 2012-04-30
> Wim Sturkenboom

It should be OK. It's a new kernel update that would be installed. I've done it and had zero problems.

I understand your hesitation, but it's not an version upgrade. If you want to make sure you don't get any new distribution notices go to:

"Menu/system/administration/software sources/updates tab/release upgrade"

From the drop down menu select "Never". Then close the window. This won't stop you from performing an new distribution upgrade, only stop the notices and prevent them from showing in your "update manager".
 
* Just a note - you will need to enter your password to open the software sources window.

Good Luck & hope this helps.

---

### Post by Dennis N on 2012-04-30
I did the same update for 10.04 and saw the same message. Seen it before too. You probably just didn't notice previously. It's not a problem - it installs a new kernel package alongside the previous ones, and does not replace the 2.6.32-40 kernel or any others you might still have installed.

---

### Post by ajgreeny on 2012-04-30
This is quite a normal message when a new kernel appears.  Note that the kernel version is part of the package name, ie, **linux-image-2.6.32-41-generic**, and the package version you have will be **2.6.32-41.88**.  If there is an update of the 2.6.32-41 kernel to **2.6.32-41.89** it will not be a new install, just an update, but when a completely new numbered kernel comes along, it is always listed as a new install.

Go with it!  Nothing is likely to be a problem, and if it is for any reason you can just choose to boot to an older kernel from grub, hence the reason for keeping an older version of the kernel on your system.

---

### Post by Wim Sturkenboom on 2012-05-01
Thanks people,

as I still did not really trust it, I made an additional backup and installed all kernel stuff (6 or 8 packages). All working.

---


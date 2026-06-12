---
title: "Password Nag"
date: 2011-08-23
forum: General Help
---

### Post by raven2099 on 2011-08-23
every-time i want to install files or explore folders a get  a Password Nag

i'm tired of constantly typing in a password is there a way so top this? in not consider it for a future update

---

### Post by magic8ball on 2011-08-23
This thread might be of interest to you...

[http://ubuntuforums.org/showthread.php?t=1788308](http://ubuntuforums.org/showthread.php?t=1788308)

---

### Post by raja.genupula on 2011-08-24
> **raven2099 said:**
> every-time i want to install files or explore folders a get  a Password Nag

i'm tired of constantly typing in a password is there a way so top this? in not consider it for a future update

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

this gonna help you . scroll the page for "edit sudoers file "

---

### Post by e79 on 2011-08-24
```
every-time i want to install files or explore folders a get  a Password Nag
```Installing software requires your password to ensure only you can do so on your machine. But for exploring folders..? What folder are you trying to open that pops-up a password dialog ?

Having password pops-up all the time means that you either are trying to  access system folders you should not tinker with (unless you know what  you are doing) or folders that are not yours.

On another hand, there is a reason why Linux is more secure than Windows and its UAC, and one of the reason is this 'password prompt' you are trying to avoid. Adding your username at the sudoer file would be the equivalent of being a local administrator on your Windows machine...which is never a good thing. Password prompts are there to protect you against many things, against yourself first (like a 'am I sure of what I'm about to do) and against autorun malwares, to name only a few things.

Taken from the link posted above:

> **Remove Password Prompt For sudo**

   [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconDialog-Warning1.png[/IMG]
   **If you disable the sudo password for  your account, you will seriously compromise the security of your  computer. Anyone sitting at your unattended, logged in account will have  complete Root access, and remote exploits become much easier for  malicious crackers.**
   [IMG]https://help.ubuntu.com/community/IconsPage?action=AttachFile&do=get&target=IconDialog-Warning1.png[/IMG]


This was my 0.02$

---


---
title: "Accessing a drive"
date: 2011-04-18
forum: General Help
---

### Post by CLNJ on 2011-04-18
So here's the problem...

I have a macbook and was running Ubuntu on it for a little while. Switched back to the mac OS however I loaded a 64 bit version onto my 32 bit laptop. Right now I'm livebooting from an Ubuntu CD trying to access the HD in order to recover a paper due for classes. Whenever I try to access the HD is says that I dont have the permission to do so. Chmod won't allow me to change the permissions b/c it is set at 700. Using chmod causes it to read
```
chmod: changing permissions of `Documents': Read-only file system
```and then it doesnt change anything. Do you all know anyway around this. I tried using sudo and logging in as root, but to be honest I'm not very familiar with sudo or very much of Linux in general. I'm still trying to learn. Thanks for any of your help.

---

### Post by mikewhatever on 2011-04-18
A read only file can not be modified or deleted, but can be copied, so what's the problem?

---

### Post by CLNJ on 2011-04-19
The problem was it wouldn't let me read the files period. the permissions were 7** but for some reason I wasn't the owner, the owner was listed as 501 (not quite sure what that means). Its fixed now, I recovered the files using sudo nautilus. Once again I'm still new to linux, and not even sure what nautilus is, but the files are safely on a flash drive.

---


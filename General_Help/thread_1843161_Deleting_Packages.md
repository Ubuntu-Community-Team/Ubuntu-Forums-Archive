---
title: "Deleting Packages"
date: 2011-09-13
forum: General Help
---

### Post by PFactorial on 2011-09-13
Hi people reading this thread,
I always download random packages that I see and try to complete a project, but I always lose interest. So I'd like a list of all the packages that I installed, not the auto updater. Can Ubuntu separate those two?
Thanks.

---

### Post by garvinrick4 on 2011-09-13
Synaptic Package Manager keeps a history I do believe look in File drop down menu. edit (not want you are looking for sorry)

If you want a history in a text editor. (will say installed)
```
gedit /var/log/apt/history.log
```##I have always used the package 'aptitude" and when installed I use it to install my packages such as sudo aptitude install (package name)
It keeps me a nice file in /var/log/aptitude of my installs. ([COLOR=Red][COLOR=Black]Tells me if they are installed or upgraded[/COLOR] [/COLOR]when using aptitude.)

Here is a link about aptitude.
[http://www.garfieldtech.com/blog/your-debian-aptitude](http://www.garfieldtech.com/blog/your-debian-aptitude)

---

### Post by PFactorial on 2011-09-13
Just to clarify, I'd like to separate the files that the updater installed and the packages that I installed from Synaptic or Ubuntu Software Center.

So how can I tell the difference between a package the updater installed and one that I installed in history.log?

---

### Post by PFactorial on 2011-09-29
anyone?

---


---
title: "Edubuntu --&gt; Ubuntu?"
date: 2006-05-25
forum: General Help
---

### Post by _linux_ on 2006-05-25
I installed Edubuntu to try it. But now I want to go to Ubuntu. How can I do that without using a CD?

---

### Post by Sef on 2006-05-25
Check out [Netboot]("https://wiki.ubuntu.com/Installation/Netboot?highlight=%28install%29%7C%28net%29") from the Ubuntu wiki.

---

### Post by matthew on 2006-05-25
Actually, if you have already installed Edubuntu it should be as simple as this:

Open a terminal (Applications->Accessories->Terminal) and type, one line at a time.
```
sudo apt-get install ubuntu-desktop
sudo apt-get uninstall edubuntu-desktop
```

---

### Post by Caligula on 2006-05-25
[QUOTE=matthew]Actually, if you have already installed Edubuntu it should be as simple as this:

Open a terminal (Applications->Accessories->Terminal) and type, one line at a time.
```
sudo apt-get install ubuntu-desktop
sudo apt-get uninstall edubuntu-desktop
```[/QUOTE]

is edubuntu-desktop not a metapackage?

---

### Post by matthew on 2006-05-25
[quote=Caligula]is edubuntu-desktop not a metapackage?[/quote]Oh, silly me. Of course it is. The problem Caligula is pointing out is that if we just remove the package "edubuntu-desktop" all that will be removed is the ***pointer*** to all the other files/programs that makes them easy to install at once...not the actual programs bundled with edubuntu. Oops.

I seem to recall that removing a metapackage using aptitude will remove all it's dependencies at the same time, but I haven't done that.

Another option is to use Synaptic and see what the dependencies are that are listed for each package and uninstall the edubuntu-desktop metapackage and all the dependencies that are in it but not in ubuntu-desktop.

I'm sure there's an easier way, I'm just working at the moment and don't have time to write more than a quick response...sorry!

---

### Post by Caligula on 2006-05-25
> I seem to recall that removing a metapackage using aptitude will remove all it's dependencies at the same time, but I haven't done that.

yes, it does, but only if you've installed it with aptitude... how is it when installed with the debian\ubuntu installer? hmmm...

It shouldn't be a problem to just find a list of dependencies, copy, write sudo apt-get remove and paste...

---

### Post by _linux_ on 2006-05-25
So I've removed the education and other edubuntu stuff and installed ubuntu-desktop. I hope it works!

---

### Post by _linux_ on 2006-05-25
It didn't work. It still shows "edubuntu" on startup. I guess I'll just have a Dapper CD ship to my house.

---

### Post by zxcv70 on 2006-05-26
And .. what's the difference between EDUBUNTU and UBUNTU???.. I've got edubuntu-desktop installed and splash screen is also Edubuntu.. but originally I've got 'normal' ubuntu? so.. what's the difference, because I haven't seen one yet?

---


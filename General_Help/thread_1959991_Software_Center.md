---
title: "Software Center"
date: 2012-04-16
forum: General Help
---

### Post by hottarod on 2012-04-16
It would help me greatly if you all would not automatically distribute non-required software.  An example of this is Samba.  I do not use Samba but it was automatically distributed in a recent update.  Once everything that was in the update queue was installed I had to go back and research what Samba even is and then with some amount of trepidation, remove Samba from my system.  I don't need anything to do with Apache client, server or MySQL(that I am aware of).  It took me a few hours to figure out how to remove all that from my system because of inter-dependencies that didn't seem to be included in the remove list. 

Another area of my system that seems to be extremely fat is the development tools section of Software Center.  There are 3 versions of GNU C compiler, 2 of C++, 2 versions of Python, Perl(I did experiment with Perl some), bunch of Java stuff, bunch of CLI 4.0 libraries(no idea what these are for).  

There are most likely other components that I don't need but it takes a lot of time and trouble to research all of this.  There may be some common libraries used for multiple things and I would have no clue which those are.  I don't want to remove something and find my system no longer functioning.

---

### Post by sudodus on 2012-04-16
It seem that you want to start with a simple system, and then add things that you select because you want it or need it.

Try the Ubuntu desktop flavour Lubuntu! It has a small foot-print, yet it is linked together to a working system. You can download the iso file and test it live, booted from a CD or USB drive before deciding to install it.

[[COLOR="red"]_https://help.ubuntu.com/community/Lubuntu/GetLubuntu_[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu")

A step further is to install the Ubuntu mini.iso and then add manually what you want. But you must know what you are doing, otherwise the system might lack some important parts.

[[COLOR="Red"]_https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall_[/COLOR]]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")

---

### Post by oldos2er on 2012-04-16
> **hottarod said:**
> It would help me greatly if you all would not automatically distribute non-required software. 

If you want the developers ("you all") to see this, this forum is not the place to post it. Try brainstorm.ubuntu.com instead.

Ubuntu is one of those distros that includes most everything except the kitchen sink out-of-the-box; maybe a different type of distro would suit your better, e.g. Arch?

---

### Post by 3Miro on 2012-04-16
There is no Samba installed on my machine and there is only one version of C++ (which I installed manually because I do a lot of development). This means that in your case, Samba and C++ were installed as a requirement or a feature of something that YOU have installed.

If you want a more fine-grained control over what you install, then use Synaptic Package Manager. It is not as simple and shiny as the Software Center, but it is not hard to use and it gives you a lot more information.

---

### Post by Cheesehead on 2012-05-06
> **hottarod said:**
> I do not use Samba but it was automatically distributed in a recent update.
...
There are most likely other components that I don't need but it takes a lot of time and trouble to research all of this.

3Miro is right - no package is magically added as part of an upgrade. You probably added something at some point that pulled in Samba too.

Researching dependencies can be trivially easy...if you use the correct tools. You didn't tell us how you were doing it. Try the 'apt-cache' command, specifically 'apt-cache depends' for dependencies and 'apt-cache rdepends' for reverse-dependencies.

---


---
title: "How to make a Linux shareware?"
date: 2012-07-29
forum: General Help
---

### Post by jiapei100 on 2012-07-29
Hi, all:

I'm just wondering how to make a Linux shareware ---- namely, application without disclosing the source code?

Under Windows, we can easily use InstallShield to pack up our applications into a single software. However, 
1) is there such a Linux alternative to Windows InstallShield?
2) If there is no such kind of things, is the only way out still to make a .deb file for installation?
3) Or, do I have to just make a .tar file?

Can anybody give me some suggestions?


Best Regards
Pei

---

### Post by hakermania on 2012-07-29
In Linux (*usually*) tarballs are used for the source code. I mean that the tar.gz files contain the source code, and, usually a 'Makefile' and a 'configure' which will build source code and install the software for you.

Deb packages have binary files inside them, not the source code. This means that a deb package just extracts itself and moves the files from inside it to the appropriate directories of the system, by following the directions of a file that is inside the deb file, as well.

There are command-line tools that you can use so as to build your application. dh-make and debuild commands will help you in the creation of the deb package.

Now, if you are planning to include your application to the Ubuntu Software Center, then it will provide the source code to the users with the command
```

apt-get source package-name

```
but, if you are not planning to do something like this, then you should upload a tarball with your source code to sites like sourceforge.

I would suggest, if you are planning to create a DEB file yourself, to learn how to make a PPA (Personal Package Archive) in launchpad and, by uploading the source to it, it will automatically build the DEB package for you, creating both the 32 and 64-bit versions of it.

If you have no experience in packaging and choose the command-line way so as to build your deb file (i am not sure if other way exists), then you will face failure several times. If you insist, though, you will succeed!

Useful links:
Launchpad -> [https://launchpad.net/](https://launchpad.net/)
Packaging Guide -> [https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)
PPA -> [https://help.launchpad.net/Packaging/PPA/](https://help.launchpad.net/Packaging/PPA/)

---

### Post by jiapei100 on 2012-07-30
Thanks hakermania.

Actually, I just want to make something like a shareware. I'm wondering how I can package all the things I need (including the dependent libraries) to a single .deb. Just like under Windows, I'm able to package all the .dll files into a single setup.exe file.
So, is this possible?

Best Regards
Pei

---

### Post by Jimmyfj on 2012-07-30
> **jiapei100 said:**
> Thanks hakermania.

Actually, I just want to make something like a shareware. I'm wondering how I can package all the things I need (including the dependent libraries) to a single .deb. Just like under Windows, I'm able to package all the .dll files into a single setup.exe file.
So, is this possible?

Best Regards
Pei

Going down this road only spells trouble for you. If you take some GPL'ed code (like dependencies) you will face a load of work undoing your efforts to close up code/hide code from the user. GPL'ed code does NOT allow you to do that, hide the source from users, or other programmers in all. That's exactly what the GPL is all about. Use some of our GPL'ed code in what can be called proprietary software, as yours, will make a tsunami of protests right behind you. **So please do not go down that road**.

---

### Post by BkkBonanza on 2012-07-30
> **Jimmyfj said:**
> Going down this road only spells trouble for you. If you take some GPL'ed code (like dependencies) you will face a load of work undoing your efforts to close up code/hide code from the user. GPL'ed code does NOT allow you to do that, hide the source from users, or other programmers in all. That's exactly what the GPL is all about. Use some of our GPL'ed code in what can be called proprietary software, as yours, will make a tsunami of protests right behind you. **So please do not go down that road**.

That's not true at all. There are many examples of closed source linux apps like Skype or Bibble Pro, or Adobe Reader for Linux. There are conditions on GPL'd code but that doesn't mean that programs using binary libraries need to be open source.

There are two main packaging systems used on Linux distros. deb files (for Debian based distros) and rpm files (for Red Hat based distros). You probably need to read up on both to build them. I think they're fairly straight forward and can be built using scripts but I'm not sure if there any slick programs that do it like InstallShield does. There isn't as much variation and customisation of install locations/options like in Windows.

---

### Post by jiapei100 on 2012-07-30
Ok, So, Jimmyfj:

If it is possible for me to just undisclose my own part of code, and leave a way for those GPL codes public?

I mean, for example, let the users to install their own packages, and possible specify those libraries/directories in a way. Then, my application is able to run upon those GPL open sources, but my part of code is undisclosed?


Thank you very much.

Pei


> **Jimmyfj said:**
> Going down this road only spells trouble for you. If you take some GPL'ed code (like dependencies) you will face a load of work undoing your efforts to close up code/hide code from the user. GPL'ed code does NOT allow you to do that, hide the source from users, or other programmers in all. That's exactly what the GPL is all about. Use some of our GPL'ed code in what can be called proprietary software, as yours, will make a tsunami of protests right behind you. **So please do not go down that road**.

---

### Post by Jimmyfj on 2012-07-30
> **BkkBonanza said:**
> That's not true at all. There are many examples of closed source linux apps like Skype or Bibble Pro, or Adobe Reader for Linux. There are conditions on GPL'd code but that doesn't mean that programs using binary libraries need to be open source.

There are two main packaging systems used on Linux distros. deb files (for Debian based distros) and rpm files (for Red Hat based distros). You probably need to read up on both to build them. I think they're fairly straight forward and can be built using scripts but I'm not sure if there any slick programs that do it like InstallShield does. There isn't as much variation and customisation of install locations/options like in Windows.

I'm really sorry if I have told something untrue, that was never my intention. But isn't your conclusion a bit hasty too? Matter of the fact is, as I see it, dependent on which GPL version you choose to use from? I believe it is. Without turning this threat into a GPL discussion.

Closed source is bad, no matter what. Again in my opinion. I mean, what do the programmer wish to hide, in an open source environment? Well - I'm off.

---

### Post by BkkBonanza on 2012-07-30
This may help,
[http://ubuntuforums.org/archive/index.php/t-1432713.html](http://ubuntuforums.org/archive/index.php/t-1432713.html)

and maybe this,
[http://www.swaroopch.com/blog/closed-for-business/](http://www.swaroopch.com/blog/closed-for-business/)

and this,
[http://stackoverflow.com/questions/1209674/shipping-closed-source-application-for-linux](http://stackoverflow.com/questions/1209674/shipping-closed-source-application-for-linux)

I'm not saying I like closed source. I don't. But if you have to do it that way for some reason then you need to be careful but you can do it.

---

### Post by Cheesehead on 2012-07-30
This question really should be addressed to [http://developer.ubuntu.com](http://developer.ubuntu.com)

---

### Post by HiImTye on 2012-07-30
there's nothing wrong with closed source, I wouldn't ask of a major game developer to open their source up because that means the likelihood of them porting to Linux is almost none. open source is great for a number of reasons but closed source is also good in some situations. I do enjoy open source software but I'm not against someone making money off of their hard work either.

---

### Post by uRock on 2012-07-30
> **BkkBonanza said:**
> That's not true at all. There are many examples of closed source linux apps like Skype or Bibble Pro, or Adobe Reader for Linux. There are conditions on GPL'd code but that doesn't mean that programs using binary libraries need to be open source.

There are two main packaging systems used on Linux distros. deb files (for Debian based distros) and rpm files (for Red Hat based distros). You probably need to read up on both to build them. I think they're fairly straight forward and can be built using scripts but I'm not sure if there any slick programs that do it like InstallShield does. There isn't as much variation and customisation of install locations/options like in Windows.
+1 I use Cisco PacketTracer on ubuntu often and thier binaries are closed source.

---


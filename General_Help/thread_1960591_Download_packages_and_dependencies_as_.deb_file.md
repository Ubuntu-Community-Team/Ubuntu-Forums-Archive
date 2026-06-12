---
title: "Download packages and dependencies as .deb file"
date: 2012-04-17
forum: General Help
---

### Post by PhantomTurtle on 2012-04-17
How can I get packages from the Ubuntu repositories, such as kubuntu-desktop(which is one of the things I want) as a .deb file. I also need dependencies, since I can't download them on to that computer(no internet). Thanks in advance for your help :)

---

### Post by Cheesemill on 2012-04-17
You can search and download individual packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

However for automatically identifying and downloading dependencies as well you are probably better off using an application such as [Keryx]("http://keryxproject.org/").

---

### Post by anejo on 2012-04-18
If you use 'gdebi' to install local deb packages that you've downloaded, it will also resolve and install any dependencies as well

---

### Post by Cheesemill on 2012-04-18
> **anejo said:**
> If you use 'gdebi' to install local deb packages that you've downloaded, it will also resolve and install any dependencies as well
But only if you have an internet connection, which the OP doesn't.

---

### Post by HiImTye on 2012-04-18
use a liveUSB and then ```
sudo apt-get -d package
```will 'download only' the packages

---

### Post by PhantomTurtle on 2012-04-18
> **Cheesemill said:**
> You can search and download individual packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

However for automatically identifying and downloading dependencies as well you are probably better off using an application such as [Keryx]("http://keryxproject.org/").

I try keryx out. Will it work on Windows because I might download at the public library when I use the computers, and those have Windows(XP I think).

> **HiImTye said:**
> use a liveUSB and then ```
sudo apt-get -d package
```will 'download only' the packages

Anything I use with Windows, due to the library situation and not being able to boot into a USB or cd.

---

### Post by Cheesemill on 2012-04-18
> **PhantomTurtle said:**
> I try keryx out. Will it work on Windows because I might download at the public library when I use the computers, and those have Windows(XP I think).
Yes, that's one of the features of Keryx.

The Windows machine needs to have Python and PyGTK to run the Keryx application. If these aren't installed you can get portable versions which will run from a USB stick [here]("http://www.portablepython.com/").

---

### Post by PhantomTurtle on 2012-04-18
> **Cheesemill said:**
> Yes, that's one of the features of Keryx.

The Windows machine needs to have Python and PyGTK to run the Keryx application. If these aren't installed you can get portable versions which will run from a USB stick [here]("http://www.portablepython.com/").

Does Portable Python Include pygtk? Additionally should I get python 3.2 or 2.7?

EDIT: Nevermind, portable python does come with pygtk and I'll try both and whichever one works is the right one I guess. Thank you for helping me out :)

---

### Post by anejo on 2012-04-19
> **Cheesemill said:**
> You can search and download individual packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

I know. I was going by this comment... and just adding another alternative...

---

### Post by PhantomTurtle on 2012-04-19
> **anejo said:**
> I know. I was going by this comment... and just adding another alternative...

packages.ubuntu.com lists the dependencies, but it doesn't give me the dependencies with the deb file. Is there a way to add the dependencies to the deb file?

---

### Post by Cheesemill on 2012-04-19
> **PhantomTurtle said:**
> packages.ubuntu.com lists the dependencies, but it doesn't give me the dependencies with the deb file. Is there a way to add the dependencies to the deb file?

No.

This is exactly why Keryx was developed.

Another app with similar goals is [apt-offline]("http://apt-offline.alioth.debian.org/").

---

### Post by PhantomTurtle on 2012-04-20
I got keryx portable and Python portable. When I tired to run it(drag and drop) I get a Syntax Error. I will attach a screenshot showing the error. Any help will be appreciated.

---

### Post by PhantomTurtle on 2012-04-22
> **PhantomTurtle said:**
> I got keryx portable and Python portable. When I tired to run it(drag and drop) I get a Syntax Error. I will attach a screenshot showing the error. Any help will be appreciated.

Or would this be a better question for a python/windows forum...

---

### Post by PhantomTurtle on 2012-04-23
bump...anybody?

---

### Post by oldos2er on 2012-04-23
Try the Keryx forums, [http://keryxproject.org/forums/](http://keryxproject.org/forums/)

---

### Post by techsupport on 2012-04-23
> **PhantomTurtle said:**
> How can I get packages from the Ubuntu repositories, such as kubuntu-desktop(which is one of the things I want) as a .deb file. I also need dependencies, since I can't download them on to that computer(no internet). Thanks in advance for your help :)

I think there is a 4 DVD set of Fedora linux that has just about everything you would ever need after you have those burned to disc. I thought (?) that Ubuntu had something like this a couple of years ago, but I could be thinking of Fedora.

---


---
title: "Linux applications"
date: 2010-01-24
forum: General Help
---

### Post by RFXCasey on 2010-01-24
How do applications work across most Linux variants? Is a program developed and then the source compiled for either Ubuntu, Puppy, Gentoo, or any other flavor? It seems very confusing when I am testing out an unfamiliar version of Linux trying to track down software I have used in other distros. Then there is the issue of which desktop manager you are using at any given time. Why do programs have to be written for either gnome or kde? Why do some work on both and will a program written for gnome run on xfce? If I want to run xfce and want a program I have used in Ubuntu do I have to find the source and compile it myself? How much of all this is dependent on desktop manager and how much is dependent on whether or not a distro is based on say Debian or something else. And to that matter. What are the common distro bases so to speak I mean I know that Ubuntu is based on Debian but can someone give some examples of flavors based on other base distros for lack of a better term?

---

### Post by blueshiftoverwatch on 2010-01-24
> **RFXCasey said:**
> How do applications work across most Linux variants? Is a program developed and then the source compiled for either Ubuntu, Puppy, Gentoo, or any other flavor?
I don't know the exact technical details. But a Linux application is a Linux application. It doesn't matter whether it's Ubuntu, RedHat, Gentoo, or Slackware. As long as it meets certain specifications it'll run. Most of the time Linux applications will even run on non-Linux OS's, like OpenSolaris and BSD.
> **RFXCasey said:**
> Then there is the issue of which desktop manager you are using at any given time. Why do programs have to be written for either gnome or kde? Why do some work on both and will a program written for gnome run on xfce?
Applications aren't written for desktop environments per-se. What happens is someone will develop an application and it might use various KDE libraries and use Qt for the GUI. Applications developed for GNOME will use GNOME libraries and GTK for the GUI.

There are effectively no issues with trying to run a KDE application on a GNOME desktop environment. The only two issues are that running both KDE and GNOME applications on the same environment will use up more system resources. Because your computer will have to load up both GNOME and KDE libraries. Also, the 'look and feel' of an application will probably not mesh with the rest of your OS because it was developed to run on a different desktop environment which uses a different GUI toolkit.

Xfce uses the GTK toolkit, same as GNOME.
> **RFXCasey said:**
> If I want to run xfce and want a program I have used in Ubuntu do I have to find the source and compile it myself? How much of all this is dependent on desktop manager and how much is dependent on whether or not a distro is based on say Debian or something else.
What you are thinking of is pre-compiled binaries. A binary is pre-compiled source code. Open source applications will release the source code and sometimes release binaries pre-compiled for various distributions. Popular ones being Ubuntu, OpenSuse, and Fedora. This is done because compiling the source code manually is often a very time consuming process that most people don't want to be bothered with. Binary packages are dependent on the package manager that a distro uses. So, an RPM package (used by Fedora and OpenSUSE) won't run on Debian type system (like Ubuntu). Although there are applications that will convert say an RPM binary to a Debian binary.
> **RFXCasey said:**
> And to that matter. What are the common distro bases so to speak I mean I know that Ubuntu is based on Debian but can someone give some examples of flavors based on other base distros for lack of a better term?
- [Unix family tree]("http://upload.wikimedia.org/wikipedia/commons/5/51/Unix_history.svg")
- [Linux family tree]("http://upload.wikimedia.org/wikipedia/commons/8/8c/Gldt.svg")

---

### Post by fjf314 on 2010-01-24
> **RFXCasey said:**
> How do applications work across most Linux variants? Is a program developed and then the source compiled for either Ubuntu, Puppy, Gentoo, or any other flavor?

I believe this is pretty accurate. That's why if you ever have to go hunting for software online because it isn't in the repositories, you will generally see it offered as a basic tarball that anyone can compile and run. However, a lot of software will commonly be pre-compiled for the major distros and their branches, thus why sites commonly offer .deb and .rpm files, too, rather than just tarballs. It's the same software as in the tarball; it's just been compiled and packaged to make it easier for anyone using those distros.

---


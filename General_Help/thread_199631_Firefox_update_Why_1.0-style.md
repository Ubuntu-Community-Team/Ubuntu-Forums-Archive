---
title: "Firefox update: Why 1.0-style?"
date: 2006-06-19
forum: General Help
---

### Post by metafile on 2006-06-19
One of the most interesting features in Firefox 1.5 is the new update system, when you download just those pieces of code which were updated (so you have to download, say, 450KB instead of 4.5MB).

Looks like this works only for w#ndows. I guess this is not Ubuntu but Firefox problem, but still. Anyone has any idea if partial download will ever work in Linux?

---

### Post by munckfish on 2006-06-19
Hi

I'm not sure but I'm guessing that the Firefox update system is sort of made redundant by the fantastic package installation and update system we have in the Apt system. 

The FF update mechanism is vital on a system like Windows where each vendor's packages are independently installed and therefore need their own independant update system, but on systems like Ubunu and most other Linux distributions packages can be distributed centrally and therefore individual update systems are not necessary.

In terms of efficient download sizes for updates, the way this is achieved in Apt is by the fact that an application's dependencies are often packaged separately so updates to a library may or may not require updates to client packages and vice versa. On Windows Firefox has to include all or most of it's library dependencies in the one installer package so its update system is the only way to modularize updates of individual components.

---

### Post by metafile on 2006-06-19
Kind of "not a bug but feature" philosophy? :) I`m not sure that Firefox for Linux uses any additional libraries, not included in it`s 8MB package.

---

### Post by munckfish on 2006-06-19
I understand where you are coming from :D. It's good to look for better ways to do things, but my gut feeling is that there's a trade off here. 

If Ubuntu were to allow Firefox to update itself at a more fine grained level than the apt system will provide then it would effectively be moved outside of apt's version control which to me sounds like merky territory as the version of Firefox which Apt is managing may not actually be the version it really is. 

I can imagine this would make it a bit of a nightmare for the Ubuntu team to support and securely and consistly publish updates for it. Whatever, a new strategy would have to be designed/adopted to deal with this change in approach. But then the question arises; if they were to allow firefox to do this why shouldn't they allow other packages to do this? 

IMO this would take away the consistency and stability we benefit from in the Ubuntu/Debian way of doing things and would mean that Ubuntu itself wouldn't be able to centrally support these packages as the responsibility for secure updates would be delegated back to the vendors.

So, if we are to retain the benefits of doing things this way, how could the download sizes for updates be reduced? The only way I can think of is to modularize packages yet further. In fact this is something that has happened with OpenOffice.org in the past: Fedora used to package all the OO localization packages in a single RPM which was huge. On slow connections it was horrible when an OO update arrived. Now they've split it into individual packages.

If you have a very immediate need to reduce the size of Firefox updates due to bandwidth challenges or access problems maybe you would consider installing your own copy of Firefox from the FF website itself. I did this in Breezy as I wanted to use v1.5 and the system version was old. What you do is uncompress it into the /opt/ directory and update the system links to use that instead. This way you could setup the file system permissions so that the user you're logged on as can apply updates to it. Just a thought.

Here's the link to instructions on doing this: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

In fact Firefox does have a bunch of external dependencies. If you run ```
apt-cache depends firefox
``` (see output below) on the command line (or dig around inside the properties page of the firefox package in Synaptic) you'll see quite a few library dependencies. Granted some of these are basic system deps such as libstdc++6 but others like libnss3 are components of Mozilla.

```
munckfish@dylan:~$ apt-cache depends firefox
firefox
  Depends: fontconfig
  Depends: psmisc
  Depends: debianutils
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgcc1
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libidl0
  Depends: libjpeg62
  Depends: libpango1.0-0
  Depends: libpng12-0
  Depends: libstdc++6
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxft2
  Depends: libxi6
  Depends: libxinerama1
  Depends: libxrandr2
  Depends: libxrender1
  Depends: libxt6
  Depends: zlib1g
  Depends: libnspr4
  Depends: libnss3
  Suggests: firefox-gnome-support
  Suggests: latex-xft-fonts
  Suggests: libthai0
  Conflicts: mozilla-firefox
  Replaces: mozilla-firefox
```

Phewee, brain dump over! ;)

---

### Post by metafile on 2006-06-19
Okay, munkfish, I wanted to get the answer, I`ve got it very reasoned, thanks (:. Looks like one of those situations when it`s easier to make one little step back than a long trip aside.

Btw: although it`s said that FF depends on libstdc++6, you have to apt-get install it yourself after Ubuntu installation.

---

### Post by munckfish on 2006-06-19
[QUOTE=metafile]Btw: although it`s said that FF depends on libstdc++6, you have to apt-get install it yourself after Ubuntu installation.[/QUOTE]

Yes, for the manual installation method documented in the wiki you do have to install a couple of deps manually as it looks like it needs libstdc++5 rather than 6.

However, for the official Ubuntu Apt managed version all mandatory dependencies will have been installed along with Firefox. (Or was this not your experience :-S ?)

---

### Post by metafile on 2006-06-19
No, I mean right after Ubuntu installation I have Firefox, but I don`t have libstdc++6 and have to install it manually if I want to compile C++ files.

---

### Post by Gustav on 2006-06-19
To compile c++ files, you need the libstdc++6-dev package. 

Are you sure that you don't confuse that package with libstdc++6?

---

### Post by metafile on 2006-06-19
Oh... Now I`m not so sure. I do remember, that I strongly needed to compile ppp and didn`t pay much attention on what exactly I`m installing ((:

Anyway, libc++ is not the only package in the list and all my grumbling was just a quibble.

---


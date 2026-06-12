---
title: "What's the difference between a regular package a &quot;...-dev&quot; one?"
date: 2011-03-15
forum: General Help
---

### Post by Rodayo on 2011-03-15
For example, if you do an apt-cache search for wireshark you get "wireshark" and "wireshark-dev". It says the latter is a set of development tools. But I don't know what that means. 

So clarification would be appreciated. Thank you

---

### Post by lithopsian on 2011-03-15
*-dev packages are typically source files such as headers that may be required for other programs to develop and build applications related to that package.  There may also be specific tools such as precompilers.  You don't usually need the dev package to install or run an application.

So wireshark is the program for sniffing networks, and wireshark-dev is a whole mass of headers and a few libraries that will help you develop apps to work with wireshark.  The naming is purely a convention.

Similarly libwireshark0 is a set of library files that would be used by wireshark, but also potentially by other apps that need the same functions.  Libraries are often followed by a number so that different versions of libraries can be installed simultaneously for backwards compatibility.  And then there can be packages like wireshark-dbg (with symbols), wireshark-data (non-code files such as databases), and wireshark-common (other files that could be used both by wireshark and other similar applications).

Very often the base package is very small, just a binary or two and some documentation, with most of the logic being in dependent library packages.  The naming conventions don't have to be followed and the actual dependencies are taken care of in the deb package.

---

### Post by DanneStrat on 2011-03-15
> **Rodayo said:**
> For example, if you do an apt-cache search for wireshark you get "wireshark" and "wireshark-dev". It says the latter is a set of development tools. But I don't know what that means. 

So clarification would be appreciated. Thank you

Yes, you're right the "dev" package contains development

tools(C header files, library files, examples etc.). They are 

intended for software developers.

Good luck.

---

### Post by corncob on 2011-03-15
> **Rodayo said:**
> For example, if you do an apt-cache search for wireshark you get "wireshark" and "wireshark-dev". It says the latter is a set of development tools. But I don't know what that means. 

So clarification would be appreciated. Thank you

I always assumed that dev was the source code in case you wanted to change something in the app and, not being into that, unchecked it in my software sources.  Somebody please correct me if I'm wrong.

---

### Post by Rodayo on 2011-03-16
> **lithopsian said:**
> *-dev packages are typically source files such as headers that may be required for other programs to develop and build applications related to that package.  There may also be specific tools such as precompilers.  You don't usually need the dev package to install or run an application.

So wireshark is the program for sniffing networks, and wireshark-dev is a whole mass of headers and a few libraries that will help you develop apps to work with wireshark.  The naming is purely a convention.

Similarly libwireshark0 is a set of library files that would be used by wireshark, but also potentially by other apps that need the same functions.  Libraries are often followed by a number so that different versions of libraries can be installed simultaneously for backwards compatibility.  And then there can be packages like wireshark-dbg (with symbols), wireshark-data (non-code files such as databases), and wireshark-common (other files that could be used both by wireshark and other similar applications).

Very often the base package is very small, just a binary or two and some documentation, with most of the logic being in dependent library packages.  The naming conventions don't have to be followed and the actual dependencies are taken care of in the deb package.

Hmm that's interesting. But I'd still like to see for myself what these source files are. Is there a way I can find out where they get installed to?

---

### Post by DanneStrat on 2011-03-17
> **Rodayo said:**
> Hmm that's interesting. But I'd still like to see for myself what these source files are. Is there a way I can find out where they get installed to?

Have a look in the hidden application directories in your

"home" folder, starting with a dot(.). You can unhide them with 

ctrl+H. For example, if you installed the "-dev" package for 

wireshark, go into the ".wireshark" folder and look for

the files in question. Also look in other places where

applications store data and shared files like:

usr/share

Good luck.

---

### Post by lithopsian on 2011-03-17
No, its much simpler than that.  You can open a deb file with your archive manager, and then open the data archive inside that.  It will show you all the files that make up the package.  Note that these are *not* actual source files for the package, but headers and similar files needed to develop other applications to work with this one.

Or you can browse at [this website]("http://packages.ubuntu.com/karmic/amd64/wireshark-dev/filelist") without downloading anything.  Interesting that the Natty version of wireshark-dev only has the python files and documentation, no headers.  Is it incomplete or did something dramatic change?

---


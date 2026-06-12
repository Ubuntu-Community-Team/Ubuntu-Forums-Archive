---
title: "Installing Software from Command line."
date: 2011-12-26
forum: General Help
---

### Post by TroN-0074 on 2011-12-26
Hi everyone, hope all of you had a good time this past weekend.
    I am writing today because I would like some advices on how to     install software from the command line. I downloaded the lates     version of rhytmbox in .tar.bz2 format.
    I have unpacked it, navigated to the folder and typed ./configure
    bunch of lines start moving on terminal, then the readme file says     to type make so when I do that I got 
    sudo make
    make: *** No targets specified and no makefile found.  Stop.
    
    if I do sudo make install
    make: *** No rule to make target `install'.  Stop.
    
    
    This appear to be typical each time I want to install something from     terminal. 
    I will appreciate all advices thank you!

---

### Post by Lars Noodén on 2011-12-26
The best way is to use the package provided by the repository.   You can get it with APT:

```

sudo apt-get update
sudo apt-get install rhythmbox

```

---

### Post by oldos2er on 2011-12-26
If ./configure isn't successful, 'make' won't work, so we would need to see the output from ./configure.

But as Lars said, simplest thing to do is to use the repositories.

---

### Post by TroN-0074 on 2011-12-26
Thank you for the reply. Ubuntu 10.04 doesn't have the repo for the latest rhythmbox so I am trying to install it from the tar file.
Here is the link to the pastebin with the details of the ./configure command outpot.
[http://pastebin.com/mMgQD1n8](http://pastebin.com/mMgQD1n8)

Thank you and I really appreciate it.

---

### Post by Lars Noodén on 2011-12-26
Here's the relevant output from ./configure:

```

configure: error: Package requirements (glib-2.0 >= 2.18.0 gio-2.0 >= 2.18.0 gio-unix-2.0 >= 2.18.0) were not met:
 
No package 'glib-2.0' found
No package 'gio-2.0' found
No package 'gio-unix-2.0' found

```

The next step is to add those packages and try running it again.  Keep going until it runs without error.

---

### Post by TroN-0074 on 2011-12-26
The weird thing is that they are there when I do a seach with the package manager they show to be installed and ready to go!

---

### Post by Lars Noodén on 2011-12-26
I'm very rusty at this kind of thing.  Perhaps the -dev variants are needed instead.

---

### Post by oldos2er on 2011-12-26
> **Lars Noodén said:**
>   Perhaps the -dev variants are needed instead.

^This^. Use Synaptic Package Manager to search for 'glib dev' for example; or you can do the same thing in the terminal with ```
apt-cache search glib dev
``` You'll need to do this for each missing dependency.

You could also run ```
sudo apt-get build-dep rhythmbox
``` to install the dependencies, but it's possible some of the 10.04 libraries may be out of date for use with a new rhythmbox.

---

### Post by snowpine on 2011-12-26
The dependencies are installed, but they are too old for the newest Rhythmbox (as the error message says). I recommend the current 11.10 release if you need the latest applications.

---

### Post by TroN-0074 on 2011-12-26
Thank you I would do a system upgrade but the new LTS version is coming up in only four months so I'll just wait to then. However I wish Ubuntu would let me use the latest apps with a two years old system version. I wanted to install E17 and the repo wont update.

---

### Post by snowpine on 2011-12-26
> **TroN-0074 said:**
> However I wish Ubuntu would let me use the latest apps with a two years old system version. I wanted to install E17 and the repo wont update.

Ubuntu is not responsible for the dependencies of Rhythmbox, E17, etc. This is determined by the Rhythmbox and E17 developers.

---

### Post by TroN-0074 on 2011-12-27
Should I give up trying to run app that are not the one in the repos then?

---

### Post by MrSpike16 on 2011-12-27
The best way to install newer versions or programs not in the repositories is to use PPAs  [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

There can be issues (bugs) with these, but are better than trying to install directly yourself. Look for PPA that is considered "stable" as apposed to "experimental" version.

Searching Google for "Rhythmbox PPA 10.04" came up with this: [http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html](http://www.webupd8.org/2010/06/install-rhythmbox-from-ubuntu-1010.html)

Not the latest but newer.  The Ubuntu Music store plug-in is broken if it matters to you, but works otherwise on my install.

---


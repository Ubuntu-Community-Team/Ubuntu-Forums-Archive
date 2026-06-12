---
title: "tcl,tk,perl-tk fail to install, but apt-get reports success"
date: 2010-02-26
forum: General Help
---

### Post by rbpember on 2010-02-26
I tried to install perl-tk today, and tried tcl and tk in the process. "apt-get install" is reporting success, but I can't find the commands. I expect them to be in /usr/bin, but they're not there. I've tried "clean" and "update" as well, and even rebooted, to no avail. Synaptic package manager gives the same results. This is happening on two different systems, one running koala and the other intrepid. Here's a snippet of what I've tried:

-------------------------------------------------------------------
%heron 35: sudo apt-get purge tk tcl perl-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tk is not installed, so not removed
Package tcl is not installed, so not removed
Package perl-tk is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
%heron 36: sudo apt-get clean
%heron 37: sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
...
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
%heron 38: sudo apt-get install tcl tk perl-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  perl-tk tcl tk
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 2547kB of archives.
After this operation, 9130kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe perl-tk 1:804.028-5 [2539kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main tcl 8.4.16-2 [4154B]                                              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main tk 8.4.16-2 [4184B]                                               
Fetched 2547kB in 6s (391kB/s)                                                                                   
Selecting previously deselected package perl-tk.
(Reading database ... 261408 files and directories currently installed.)
Unpacking perl-tk (from .../perl-tk_1%3a804.028-5_amd64.deb) ...
Selecting previously deselected package tcl.
Unpacking tcl (from .../archives/tcl_8.4.16-2_all.deb) ...
Selecting previously deselected package tk.
Unpacking tk (from .../archives/tk_8.4.16-2_all.deb) ...
Processing triggers for man-db ...
Setting up perl-tk (1:804.028-5) ...
Setting up tcl (8.4.16-2) ...
update-alternatives: using /usr/bin/tclsh-default to provide /usr/bin/tclsh (tclsh) in auto mode.

Setting up tk (8.4.16-2) ...
update-alternatives: using /usr/bin/wish-default to provide /usr/bin/wish (wish) in auto mode.

%heron 39: rehash
%heron 40: which tcl tk perl-tk
tcl: Command not found.
tk: Command not found.
perl-tk: Command not found.
%heron 41: cat /etc/issue
Ubuntu 9.10 \n \l

%heron 42: 
----------------------------------------------------------------------

I am able to install other packages, for example

-----------------------------------------------
%heron 46: sudo apt-get install abiword
Reading package lists... Done
...
Setting up abiword-plugin-mathview (2.6.8-5ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
%heron 47: rehash
%heron 48: which abiword
/usr/bin/abiword
%heron 49: 
---------------------------

What's going on?

---

### Post by mcduck on 2010-02-26
I don't think TCl or Tk are actual *programs* you could execute like. Instead you just use them in your scripts, via the *wish* command...

[http://www.faqs.org/docs/Linux-HOWTO/TclTk-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/TclTk-HOWTO.html#ss5.1")

---

### Post by rbpember on 2010-02-26
OK, thanks. 

What I'm trying to do is install TexLive using the perltk gui. I had to install perltk to get this to work. I've been going through iterations and so running the install script over and over. At some point I strangly got a message that perl-tk wasn't found. That's what started this bit of thrashing I went through. Oddly, just now I tried again and it is working. I'm now guessing it was an error on their end and a faulty error message.

Thanks again. Sometimes just another pair of eyes helps...

---

### Post by gmargo on 2010-02-26
To see the files installed by a package, use **dpkg -L packagename**.

---

### Post by rbpember on 2010-02-26
thanks

---


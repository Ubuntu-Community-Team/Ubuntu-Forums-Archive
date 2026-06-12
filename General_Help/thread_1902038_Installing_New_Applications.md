---
title: "Installing New Applications"
date: 2011-12-29
forum: General Help
---

### Post by normbenign on 2011-12-29
I've been using my Ubuntu installations as is.  Now I wish to install Wine, to run a few Windows programs.  I have downloaded  Wine and later aptitude.  Both came in files with .deb extensions, which seem to be like zip files in Windows.  I've unpacked them, but don't know where to go from there.

Each original file unpacks into three folders, but I can't find anything like install or the equivalent in any of them.

How do I install these applications?

---

### Post by hwttdz on 2011-12-29
Short answer:
at the terminal "sudo apt-get install -y wine aptitude"

Long answer:
You should probably try to avoid installing anything outside of using the software center/synaptic/apt-get until you're familiar with the system.  Ubuntu is nice in that it provides a repository of all software, so if there is something you want to install you just install it using the provided tools (which can also keep it up to date).  So no searching over the interwebs, no grabbing the wrong installer, none of those worries.  Software center should be accessible through the applications menu, synaptic is probably accessible through the applications menu, if not try "synaptic" at the command line, if you get a "command not found" message, run "sudo apt-get -y install synaptic" to install synaptic which is a graphical front end for apt-get (and very nice).  After that "synaptic" at the command line will work.  It will warn, "running without super user permissions" or something of the sort, which means you can't make any changes.  If you want to add or remove programs through synaptic, you'll need to launch as "sudo synaptic".  And finally apt-get, apt-get is one of the most basic ubuntu tools (i.e. it's installed even in the most minimal ubuntu installs).  And it can install, update and remove programs for you.  Say I wanted firefox, I'd just run "sudo apt-get install firefox" and that'd get it for me.  

I know that's a lot to digest, but summary:
1) don't download .deb files until you know how apt-get/synaptic/software center work.
2) software center should be accessible through the graphical interface (I've never used it so I can't tell you exactly how)
3) synaptic if installed might be graphically accessible, if you can't find it graphically try "synaptic" at the command line, if that says "command not found" install via "sudo apt-get -y install synaptic" then run "synaptic" to launch.
4) apt-get is installed and good to go on the command line.

---

### Post by oldos2er on 2011-12-29
Don't unpack *.deb files, just double-click them.

---

### Post by pretty_whistle on 2011-12-29
> **oldos2er said:**
> don't unpack *.deb files, just double-click them.
+1

---


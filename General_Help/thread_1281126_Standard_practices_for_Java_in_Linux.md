---
title: "Standard practices for Java in Linux"
date: 2009-10-02
forum: General Help
---

### Post by Chasville on 2009-10-02
Shortened story = finally wiped Windows and installed Ubuntu on my laptop.
One of the things I do is Java development and C programming for algorithmic research.
Since I'm rather new to the Linux world, is there a sort of standard practice for where to install java?  /var, /opt, /usr ?  I'm taking an SDK here, not just the JRE.

---

### Post by akakingess on 2009-10-02
> **Chasville said:**
> Shortened story = finally wiped Windows and installed Ubuntu on my laptop.
One of the things I do is Java development and C programming for algorithmic research.
Since I'm rather new to the Linux world, is there a sort of standard practice for where to install java?  /var, /opt, /usr ?  I'm taking an SDK here, not just the JRE.

I believe it is preferred to install into the /usr directory, but you can install pretty much anywhere and create links into whichever other directories may need to reference the app. Someone will probably know better and correct me if I am wrong, but that is my understanding.

Edit: BTW, it is customary to create the /java directory in the /usr directory first and set that as the install point (again, this is my understanding and the way I have at least gotten it to work, but I did create links (shortcuts) elsewhere.

---

### Post by falconindy on 2009-10-02
Why not just install the packages out of the repository and not worry about it? Use the following:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
```
In this case, Java is installed to: /usr/lib/jvm/java-6-sun/

---

### Post by Chasville on 2009-10-02
Well looking around elsewhere, for standard practices for Unix, it looks like it should be insalled in /opt/java and then have /usr/bin links to javac and java.

Searching Ubuntu, I saw a reference to a package manager, but I'm not finding it.  Is is under "Applications, Add/Remove..." ?  I don't see a java there.

But, I see "games' under both /var and /usr; /opt is currently empty; and I don't see where firefox, the office stuff, gimp, ,,,  are installed

---

### Post by Chasville on 2009-10-02
Ahh, /usr/lib, there I see stuff.  Hmm ....
time for bed ...
maybe some others will chime in here by the time I check back in tomorrow.

---

### Post by falconindy on 2009-10-03
> **Chasville said:**
> Searching Ubuntu, I saw a reference to a package manager, but I'm not finding it.  Is is under "Applications, Add/Remove..." ?  I don't see a java there.
If you're going to be a full time Linux user, its worthwhile getting acquainted with the terminal, particularly if you'll be programming. In time, you'll find that tasks can be completed much more quickly in text than they can via the GUI. The string that I gave you is for the terminal based package manager, aptitude. If you prefer a graphical interface, then press alt-f2 and type in 'gksu synaptic'. There is another graphical package manager, but its very primitive and not really worth using -- it's listed as 'add/remove programs' under applications.

---

### Post by Chasville on 2009-10-04
I've been "playing" on Unix systems for a few years.  So, I'm fairly comfortable with the command line.   I've done a fair amount of shell scipting in korne, awk and some perl.  But, not having been an admin, I didn't do much in the way of installations, and I've seen a lot of varying "standards" and styles, from HP-UX, through Solaris and into AIX.  Linux is another style, and is not (and probably never will be) a true Unix OS.   But, that's ok.  I've also used PC's, Apples, mainframes and Vax.

Now, for Ubuntu, I see a lot of stuff under /usr/lib.  I don't know if I like or agree with using /usr/lib like C:\Program Files in Windows.  But, it does make sense to put links in /usr/bin to point to stuff elsewhere.  It also makes sense to simply add an application's bin directory to PATH.  After all, USR = Unix System Resources, not an abbreviation for "user".

Hmm, some other research for Linux filesystem standards seems to indicate that /opt would be the correct choice, so that's what I'm going to do.

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by fluffman86 on 2009-10-04
seriously, you should just get it from the repositories.  Applications > Accessories > Terminal, then copy/paste:
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin

Or, you can use synaptic by going to System > Administration > Synaptic

Add/Remove is great for searching for programs and suites of programs, but pretty useless for command line utilities and package management.

---


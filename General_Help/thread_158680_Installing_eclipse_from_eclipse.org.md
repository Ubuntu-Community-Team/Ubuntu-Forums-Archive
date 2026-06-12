---
title: "Installing eclipse from eclipse.org"
date: 2006-04-11
forum: General Help
---

### Post by dpm on 2006-04-11
Hi all,

I've installed eclipse from the repositories and after some tweaking (mainly telling it to use sun's jre instead of java-gcj) I got it to run without it being excessively slow.

However, I've read somewhere in the forums that some people simply download the tarball of the last eclipse version from the eclipse.org site, untar it and run it without problems. Well, theoretically this should work, and in fact I've done the same with another java program (untar and run, I mean), but I'm not sure about eclipse. On the repos the eclipse package has got a lot of dependencies, and I'm wondering whether I would need them at all if I simply untared and run the eclipse.org version. 

I mean, apart from being able to run the latest eclipse binaries, there is also the fact that I'd like to get rid of the dependencies automatically installed by the eclipse from the repos, namely the mozilla browser, which it forced me to install (I've got epiphany and firefox, why would I want a 3rd browser???).

I'm gonna try to uninstall eclipse from the repos and all its dependencies now. Then I'll try to get the eclipse.org tarball running.

I simply would like someone to comment on his /her experiences on that in case he/she had already done it.

Thanks.

---

### Post by dpm on 2006-04-12
In case it helps anyone, I just wanted to say that I uninstalled eclipse and all its dependencies from my system (apart from junit and ant, although I don't think they are absollutely necessary) and then I downloaded and unpacked the latest version of eclipse from the eclipse.org website.

I simply untared the downloaded file into /opt and then added a menu entry for eclipse in the gnome apps menu.

That worked, eclipse is running (with cdt installed) and I'm now a happy man. I would only like to get it running a bit faster, but that's another story...

---

### Post by ccoppenbarger on 2006-04-17
How did you add it to the Gnome menu?
I did what you did, but I can't get it to run yet, even from the terminal.

---

### Post by ccoppenbarger on 2006-04-17
Never mind. Figured it out.

---

### Post by thudmeister on 2008-03-06
Which download did you use.  I have tried the latest and the latest stable and I keep getting errors about org.eclipse like can't create the view.

Also it will not execute the Find and Install or Manage Configuration under Help-Software Updates.

---


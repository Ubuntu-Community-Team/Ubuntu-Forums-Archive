---
title: "Unable to install new software for Eclipse"
date: 2011-02-28
forum: General Help
---

### Post by alman9898 on 2011-02-28
Hello,

I downloaded the latest version of Eclipse from the Ubuntu Software Center. However, when I try to install plugins to Eclipse, nothing appears in the update list. More specifically, each plugin is "blank" but when I click on it, a full description is given. But I cannot click "next" or "finish" to install it.

However, running Eclipse as root, the list will appear as it should, and installs plugins.

My question is, how can I install new software to Eclipse as user?

---

### Post by veggen on 2011-02-28
Hmm, my guess would be that it somehow doesn't have write privileges for whatever is the location plugins go to.
I downloaded the latest Eclipse from it's own site and just unpacked it in my home dir (where I knew I had all privileges), and it works fine.
Try finding out where it puts plugins and as which user (as you or as some "eclipse" user) and give that user write privileges for that location. You can start by giving everyone the privileges and see if it works.

---

### Post by m25p2 on 2011-03-01
Hi everyone,

I have a similiar problem: I have installed Eclipse SKD from the Software Center, but I would like to use eclipse for C.
Now I have tried to install it with the help--> install new software, but I have failed so far.

(I was following the instruction from [http://www.linuxforums.org/forum/ubuntu-linux/155207-eclipse-cdt-ubuntu-9-10-a.html](http://www.linuxforums.org/forum/ubuntu-linux/155207-eclipse-cdt-ubuntu-9-10-a.html), but I always get following error-report:
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.cvs 1.0.400.v201002111343, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  The artifact file for osgi.bundle,org.eclipse.cvs,1.0.400.v201002111343 was not found.)

Could anyone give me any advice? (Of course a step-to-step instruction would be the best :D)

Greetings, Martin

---

### Post by veggen on 2011-03-02
Try getting Eclipse from [www.eclipse.org/downloads](www.eclipse.org/downloads). You're not the first to have problems with Eclipse from the repo. There's no installation or anything to worry about. Just extract and run.

---


---
title: "Cannot install libre office or open office for weird reason?"
date: 2011-11-11
forum: General Help
---

### Post by jrc7z on 2011-11-11
Long time lurker, first time poster.  Normally you guys are my go to but I can't seem to figure this one out.  I have unresolved dependencies with libre office and open office when I try to install.  I had to do a partial upgrade because of unresolved dependencies (Actually.  What is a dependency?) and restarted.  After that, my open office suite was gone.  Libre office just plain wouldn't install and when I try to install either, i have a broken dependency that is just "openoffice.org".  Nothing more.  Nothing less.  What gives?!


Edit:  Here's a picture.
[IMG]http://i40.tinypic.com/11v0ck4.png[/IMG]

---

### Post by jrc7z on 2011-11-12
Nobody's got a clue?

---

### Post by peter d on 2011-11-12
I could be wrong but I think that you may already have OpenOffice.org installed (it's installed by default on 10.04 as is LibreOffice on 11.*) and are trying to install a later version. I don't think that's possible. You may need to uninstall the version that you already have first.

Synaptic, Software Centre and apt should all resolve dependencies for you (if they're resolvable).

A dependency is just a piece of software (usually a library) which the program you're installing needs (depends on) to be able to run.

---

### Post by jrc7z on 2011-11-12
I purged open office and libre office, so neither are on it anymore, I don't know why it's saying I can't.

Also,  I can't find synaptic?

EDIT:  If it helps, it disappeared after I did a partial upgrade.  I've tried to install through the software center and it just says that it has dependencies and tells me "openoffice.org" like the picture when I open the details section.  What to do to get it back?

---

### Post by pretty_whistle on 2011-11-12
I've got the same issue!

I have LibreOffice installed and I tried to install OOo and got that same message.

I'm stuck with it and don't know what to do now.

---

### Post by jrc7z on 2011-11-12
Not exactly the same, I don't have either.

---

### Post by pretty_whistle on 2011-11-12
I just tried using synaptic but got a similar message "package dependencies cant be resolved".

---

### Post by Chronon on 2011-11-12
Any luck if you try to install from the command line (i.e. apt-get or aptitude)?  Even if they fail, they might be more verbose about the source of the problem.

---

### Post by pretty_whistle on 2011-11-12
> **Chronon said:**
> Any luck if you try to install from the command line (i.e. apt-get or aptitude)?  Even if they fail, they might be more verbose about the source of the problem.
How do I type that in exactly?

Never mind.  I figured it out.

---

### Post by pretty_whistle on 2011-11-12
I tried apt-get.  Here's what the output said:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openoffice.org : Depends: libreoffice but it is not going to be installed
E: Broken packages


---

### Post by Chronon on 2011-11-12
What happens if you manually install libreoffice then?

```
sudo apt-get install libreoffice
```

I have Libre Office on my system.  I don't really know why you are hitting a problem.  (I'm not doubting you, I'm just looking for something that might give us a bit more descriptive of an error message.)

---

### Post by jrc7z on 2011-11-13
Libre office installed after I purged everything.  Again.  I have been trying to use nothing but the terminal in an attempt to learn more about ubuntu and resort to the software center when that fails.  I just used the purge command on both open office and libre office, was told there was nothing to purge.  So I tried to install open office, didn't work, but libre office did. So,  I have my text editor and I am happy.

---


---
title: "Eclipse will not start"
date: 2010-03-30
forum: General Help
---

### Post by spartan_87 on 2010-03-30
I am running Ubuntu 9.10 64bit on my desktop and using the latest version of eclipse classic (galileo). I don't have the version from synaptic installed. I downloaded it strait from the eclipse site and run the launcher out of the folder.

It was working fine a few weeks ago the last time I used it, until today I go to launch it and nothing happens. The eclipse splash screen doesn't even come up. 

I have also tried running it in the console and it give no output at all and just goes to a new prompt. 

So I also tried installing the eclipse version in synaptic and it does the same thing.

On my laptop, running Ubuntu 9.04 32bit, eclipse launches and runs fine.

Any ideas why its not launching on my desktop?

---

### Post by GregBrannon on 2010-03-30
Since Eclipse is a 100% Java application, I'm wondering if your Java install has gone bad somehow.  Do you have any other indications that there is a problem with Java?  Or check your Java installation for updates and/or just reinstall it.

---

### Post by spartan_87 on 2010-03-30
Ok I got it fixed. 

Since my eclipse was working on my Ubuntu 9.04 laptop, I compared all the java packages installed on there to my desktop. Turns out for some reason I didn't have the default-jre package installed. So I installed it and that did the trick.

Kind of weird that eclipse worked on my desktop awhile ago though. I guess that package got uninstalled some how.

All is good now! Thanks for the reply GregBrannon.

---


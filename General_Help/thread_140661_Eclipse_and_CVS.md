---
title: "Eclipse and CVS"
date: 2006-03-06
forum: General Help
---

### Post by tharsan on 2006-03-06
Hello,

I'm pretty close to switching to Ubuntu as my dedicated desktop OS (I'm already running Ubuntu server on my server at home) but there's a really annoying problem I can't solve with Eclipse:
I can't seem to checkout projects from CVS using Eclipse.  In the New Project wizard, I can't browse modules in a repository, and if I do enter a module name, nothing happens when I press Next.

Has anybody experienced this problem?
Creating Java projects appears to work correctly.

Thanks
- Tharsan

---

### Post by aayush on 2006-04-10
Yes, I have the same problem. whenever i try to expand HEAD in the repository location, it shows a popup alert saying "Internal Error". I type the name of the project i wanna check out and it shows the same popup error message. eclipse CVS is sadly the only reason i am still running windows.](*,)

can anybody help us out here?

---

### Post by aayush on 2006-04-11
i've found my problem and the solution. i hadn't fully installed sun java and was still running on the (correct me if i am wrong) crappy gij! mozilla-firefox and eclipse itself were running on the sun java jre1.5.0_06, but the system default java was still gij. i just replaced that by the sun version and it works!

a good way to see if this is your problem is to type 'java -version' on your command line.
if this is your problem, just look up 'replacing gij' in this forum and see what you need to do.

---

### Post by DC@DR on 2006-06-22
I still have the same problem with Eclipse and CVS (even with SVN-subclipse plugin also), and when I type java -version, it gives me jsdk1.5.0...I still can use kdesvn and cvs client to connect to server, but then Eclipse spawns errors when I tryto connect to any repositories (CVS and SVN) ...It's kinda weird, any help will be appreciated :-)

---


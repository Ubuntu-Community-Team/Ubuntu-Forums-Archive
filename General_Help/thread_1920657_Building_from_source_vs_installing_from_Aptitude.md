---
title: "Building from source vs installing from Aptitude"
date: 2012-02-05
forum: General Help
---

### Post by roebuck86 on 2012-02-05
Hello. 

I will shortly be setting up my own Ubuntu server for hosting a few websites. In the past, I have always installed the software through apt-get / aptitude rather than building them from source. Recently I have become increasing aware that the software avalible through apt-get can be quite outdated. Therefore, I have learnt that some applications have their own PPA to get the latest versions. Which is excellent. Yet, software such as Nginx has to be built from source in order to customise the modules. So, I can grab the latest version and install it from source, so far so good. My main concern arrives x number of months down the line, when a bug / security fix is released. I'm fairly sure if this was installed via the PPA / apt-get then I would receive security patches as part of the updates. Yet if ive built the software from source, where do I go from here? How would I get those security fixes? Would I have to rebuild from source? 

I'm in a similar situation  with PostgreSQL. Do I go for the latest release (which I most likely don't need the latest greatest features, although it's nice) or build from source?


What are the pros and cons of both approaches?

---

### Post by raja.genupula on 2012-02-05
If you're installing any application through apt-get/aptitude means first thing is that packages PPA should be in the list . so if it is available  in the list means Ubuntu and that package maintainer will take responsibility on that package support .

If you get installation of that package from source means then its maintainer will take the responsibility of that package regarding any type of fixes and support .

This is what i know under my knowledge.

Hope that helps you a bit.

---

### Post by mcduck on 2012-02-05
IF you install something manually from source code, then it's up to you to follow when there are new versions of the applciation available and to download and compile it again.

I'd definitely recommend looking for a PPA (or some other) repository for applications when eve rpossible instead of compiling things from source.

...and if you in the end need to compile stuff yourself, you might want to use checkinstall to convert the compiled code to a .deb package installable through package management. As the software still isn't coming from any of your online sources you won't get updates for it, but at least this way it'll be much easier to keep track of your installed apps and to remove them when you don't need them any more or wish to compile a new version...

(to use checkinstall all you need to do is insall the checkinstall package, and then when compiling the application instead of running "sudo make install" you run "sudo checkinstall". The packages created this way will not contain all the standard information about dependencies etc, so you shouldn't usually distribute them to other people but they will work on your own system as you'll already have all the dependencies installed anyway)

---


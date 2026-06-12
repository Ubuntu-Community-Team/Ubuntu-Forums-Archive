---
title: "if software works on one linux, can it work on all linux?"
date: 2010-08-21
forum: General Help
---

### Post by fuzzylogic25 on 2010-08-21
i have noticed when i come across some downloads (such as one of the popular browsers) when it has option to install for linux it specifically says UBUNTU and not linux. also i know that ubuntu has its own repository of software. debian too also has one with apperently over 25,000 apps. the question i want to know is, can these apps, whether located on debian, slackware, ubuntu etc repositories or even an app found specifically on the net for ubuntu, can these apps work on any other linux?

why are there apps with installations for different linux types? i ask this because i started of a windows user, for just over 10 years and finally now i realise i need an operating system like linux. however i dont plan to stick with ubuntu,i think i need more flexibility so ubuntu is a starting point for me. i use about 20 or so apps in windows for specific purposes (compression tool for example) and i am now trying to find the best equivalent or better applications for ubuntu of these apps. this is taking me time as i have to trial out different software (eg for windows messenger replacement, check each app available to ubuntu and see what they all offer, chose the best one out of all of them, or a bunch of popular ones). i know down the track i will prob want to change to an operating system like debian or slackware. so i want to be able to at least have the apps i find from using ubuntu useable on the other linux distros.

so to summarize my questions are:
1. can you use any ubuntu related software on any linux distro? ie are linux applications portable to all other linux distros
2. if not, why?
3. can there be some MINOR changes made in order to make it work? ie maybe some libraries required to run the app.
4. do you need to have an ubuntu o.s. to access the ubuntu software repository? is this the same for software repository in slackware, debian etc?

---

### Post by HoKaze on 2010-08-21
Strictly speaking, if you have all the needed libraries (and the correct versions) installed then yes, most linux programs will work across multiple distros. It doesn't quite work that way in practice as most of the time the software is packaged so that it can easily be installed via package manager, repository, etc. Different distros have different repos, different packages and different package managers. As such, you can't use a .deb package intended for Ubuntu users on say, Fedora.
Long story short is that most of the major distros tend to have pretty big repositories (although not as big as debian or ubuntu) and chances are that most programs will either be in their official repositories, additional repos, 3rd party repos or perhaps simply as a package. If worst really comes to worst you can always open up a .deb (which is essentially an archive) and try to install manually, you can search the software's website to look for a binary and install that manually or you can compile the source code.

That's probably not the best way of explaining it, but meh...basically I'd say that if your preferred software tends to be popular, more distros will have it in their repos and that generally speaking, if you want the widest range of software that's easily installable, go for a popular, "major" distro.

---

### Post by fuzzylogic25 on 2010-08-21
thanks for ur reply. one of the major reasons for me moving to linux is for reliability and stability. i want to have an operating system that will stay up for a very long period (several months) without crashing. i run alot of software so there is alot of multitasking involved.

however one of my long term goals is to also learn alot about unix too as this will help me with alot of jobs that i will be applying for. so i hear that an o.s. like arch or slackware is the best for this area.

---


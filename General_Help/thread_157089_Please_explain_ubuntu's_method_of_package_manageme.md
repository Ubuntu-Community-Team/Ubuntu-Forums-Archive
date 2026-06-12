---
title: "Please explain ubuntu's method of package management"
date: 2006-04-08
forum: General Help
---

### Post by ganja_guru on 2006-04-08
Hi everyone..I've been a linux user for a long time and have used RH,Suse,Mepis,Yoper,Slack, and finally settled with Arch linux. I've installed kubuntu for my brother cause he's new to linux and needs something a little user friendly. Since arch's package managaement is pretty simple(they don't split -dev packages), I'm a little confused how ubuntu works..This is what I did..

1). Installed kubuntu
2). Installed Automatix and installed all the other stuff I needed(this would have added other repos to apt sources)

I'm trying to build a KDE package which requires libjpeg and qt headers(these are the errors configure throws up)..These were the packages I tried to install thru adept

(sorry I dont remember them correctly..I'm on my arch box)

libjpeg was already installed
libjpeg*-dev
libqt3-mt(or something similar)
libqt3-dev...(or libqt3-headers?)

anyway Adept did not throw up any errors, so I commited changes and was suprised to see that Adept started removing things like 'kubuntu-desktop' 'akode' 'k3b' and everything else KDE related..(about 100 packages in all)

This isn't really a big deal cause I just have to do apt-get install kubuntu-desktop to get things back again...but why did this happen..I've seen it happen many times before (I've used ubuntu myself a while back), where simply wanting to install some package needs a HUGE number of packages to be removed, rendering the system useless.

This isn't a rant, just searching for an explanation so I don't mess things up again thanks to ignorance..Please help..thanks.

---

### Post by aysiu on 2006-04-08
Based on my limited knowledge, these are two things I've seen:

1. Adept never warns you if packages will be removed. apt-get will. Synaptic will. Adept won't.

2. Typically when that sort of situation happens, it has to do with conflicting repository sources. I don't know what kind of sources.list Automatix puts in, but you may want to change it up for your own.

---

### Post by Velvet Elvis on 2006-04-08
Since ubuntu is just debian on steroids, all the debian tools still work.  Aptitude is probobly the most powerful package browser available.

---

### Post by feathers on 2006-04-08
Well, the problem might have been libqt3-mt. As far as I know it has been replaced by another package. If you install it, it conflicts with all packages that depend on the other package. Because you want this particular package, everything else is removed. 
Actually this is pretty useful, because you can't get into an impossible situation. But, as others said before, adept never warns you and I have seen at least 10 posts with people desperate because they have removed half their system without knowing it.

---

### Post by ganja_guru on 2006-04-09
I've switched to kynaptic now..much cleaner interface..and at least it tells you when its uninstalling something.

---

### Post by CamD on 2006-04-17
I'm currently in a state of not being able to use Adept at all (installing/updating/removing anything). 

I just finished reinstalling Kubuntu because of this problem. Now, a day later, I already can't install anything through Adept, again.

Feathers, you say libqt3-mt could be the problem. I have it installed. Do you know what the other package is?

I'll probably just try an alternative, soon, but I'm still curious.

EDIT: ah, should have known better. I just tried out 'apt-get check'. I traced it down to a package I had downloaded at one point--a dapper version of gcc4.0-base (4.0.2) as a dependency for a dependency (I don't know why I didn't just use adept back then...or more recently). Should teach me not to google for dependencies.

I went just now and downloaded the 4.0.1 version for breezy and downgraded. All is good now :)

---


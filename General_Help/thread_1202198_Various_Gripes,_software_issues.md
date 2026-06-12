---
title: "Various Gripes, software issues"
date: 2009-07-02
forum: General Help
---

### Post by SirCyber on 2009-07-02
Ok, I'm a longtime computer nerd, have used Ubuntu before, used LinuxXP, and now using Ubuntu 9.04. I have worked with Microsoft crap since windows 3.51. I have dabbled in programming, I ran my own computer repair shop *I love windows for the revenue it brought me!*, I build computers and test software. Just a few Credos... now the issues.
 First issue!!! I am having a problem getting my yahoo messenger to work,and cannot find any issues relating to this in the forums. ok... the issue started within Pidgin... Yahoo messenger would not connect. simple issue, I figured, wth, I really want to use my webcam anyways, I'll download yahoo messenger itself. got it downloaded, great. still DOES NOT CONNECT. figured, ok, must have installed improperly. so ya-dee-da, decide to install Kopete. Yahoo still does NOT connect! in both Pidgin AND Kopete, my AIM works just fine, not a single hitch! 
Issue #2... tried installing Ventrillo. Tried installing the vent version for linux *it's a server version at that!* it will not finalize the installation process... now when I try to modify it or anything it tells me bluntly *not verbatum* that it has done all that it's going to do. which is nothing. I cannot find Ventrillo anywhere, I do not know how to go and try to delete it so I can try again, I have delete the program a few times in order to reinstall a different version, and it tells me that I need to repair, modify, or delete. delete option does not get rid of it! HELP!
Lastly, wtf is up with Java, seriously! correct me if I'm wrong, but isn't it open source? why won't it work with linux! I cannot go to some websites I normally frequent, I cannot do courseware I need to do due to Java not working as it should. That last part is critical, I NEED it to work! I am in a time sensitive class, and when not in the classroom I have plenty of time to use my personal computer to do the work. however, I am forced to use public computers and deal with half hour increments of internet use and fighting off the other people who want to watch movies while I need to do my work! any advice at ALL would be most helpful.
****EDIT****
I would also like to be directed to where I can find the most helpful pages for why I cannot get the cube desktop in Compiz to work. I have installed the CompizConfig Settings Manager, have installed Emerald Theme Manager, and Simple CompizConfig Settings Manager, have gotten my Appearance settings set to Custom, selected the cube from the compizcomfig settings manager, have installed all the right stuff, just something is not set correctly. I've gotten to the point where I want to take screenshots of everything and hopefully someone will know whats wrong with my system... I'm running a Toshiba Satellite A350 with an AMD Turion X2 Ultra, ATI Radeon 3870, 4GB RAM, and an upgraded WD Blue 7200rpm 320GB HDD. Thanks for the help.

---

### Post by ronaldprettyman on 2009-07-02
> **SirCyber said:**
> 
 First issue!!! I am having a problem getting my yahoo messenger to work,and cannot find any issues relating to this in the forums. ok... the issue started within Pidgin... Yahoo messenger would not connect. simple issue, I figured, wth, I really want to use my webcam anyways, I'll download yahoo messenger itself. got it downloaded, great. still DOES NOT CONNECT. figured, ok, must have installed improperly. so ya-dee-da, decide to install Kopete. Yahoo still does NOT connect! in both Pidgin AND Kopete, my AIM works just fine, not a single hitch! 
This is a Yahoo!! problem contact them I think their just trying to recoup revenue or something, but its been a systematic shutdown of accounts. My cousin had pidgin die first then about a week later yahoo on pidgon stoped for me as well. The web version works though, but I think they made some changes to their protocol and I'm personally trying to organize a boycott of yahoo messenger yahoo sucks anyway and for them to let this happy is crap. I'm sticking with aim and the facebook plugin.

> **SirCyber said:**
> 
Issue #2... tried installing Ventrillo. Don't know what to tell you on that one


> **SirCyber said:**
> 
Lastly, wtf is up with Java, seriously! correct me if I'm wrong, but isn't it open source? why won't it work with linux! I cannot go to some websites I normally frequent, I cannot do courseware I need to do due to Java not working as it should. That last part is critical, I NEED it to work! I am in a time sensitive class, and when not in the classroom I have plenty of time to use my personal computer to do the work. however, I am forced to use public computers and deal with half hour increments of internet use and fighting off the other people who want to watch movies while I need to do my work! any advice at ALL would be most helpful.

Download the offical version of java, search for java sun in synaptic and install the sun version of java instead of the gnu version.

---

### Post by SirCyber on 2009-07-02
Thanks for the speedy response. In reference to Java, that was the first place I looked to for java stuff. have downloaded it. second, so there is nothing I can really do about yahoo? seriously? that's my main messenger, I will have to find something to do about this. Third, no advice on vent? anyone else? and lastly... my appearances settings, any help will be most appreciated there. thanks again so far!

---

### Post by ronaldprettyman on 2009-07-02
> **SirCyber said:**
> Thanks for the speedy response. In reference to Java, that was the first place I looked to for java stuff. have downloaded it. second, so there is nothing I can really do about yahoo? seriously? that's my main messenger, I will have to find something to do about this. Third, no advice on vent? anyone else? and lastly... my appearances settings, any help will be most appreciated there. thanks again so far!

Their should be a warning label on ubuntu, its really ugly go to gnome-look.org before you have an stroke. I think the biggest hurtle for ubuntu. Is the brown, its gotta go. Fedora looks awesome, though it blows on the desktop in comparison, the default appearence is so much better.
But yeah

**gnome-look.org** great site for spicing up, sorting by download and rating is a huge plus on this site to weed though the shear volume and it has decent howto with all the varies themes. You can also install **gnome-art** through synaptic which is much nicer.

I've read some people say that upgrading pidgen though source. It still doesn't work 100% in the end.

I recommend the web version at messenger.yahoo.com (might not be spelled right) my cousin can't give it up either and said that has been working for him while he's in transition to aim.

Personally aim has always worked great for me and I started facing out yahoo awhile ago, their product just isn't up to snuff imo.

The best appearence imo option is Dark Nimbus from openSolaris, you can find a deb for ubuntu if you search for "Dark Nimbus" in google.


On the compiz thing, your have to ask somone else. The whole thing is worthless after a week. Do it once or twice and you end up turning it off cause it slows down your system and has conflict with other packages. Its nice but gets old quick. Make sure your opengl is working, google earth is the easiest way to test. Wait even easier
open a terminal and type
```
glxgears
glxinfo
```
if the gears don't come up, your drivers aren't working, post the results for glxinfo. Though this might be an nvidia specific thing if you get a command not found error and not a glx error.

---

### Post by trojanfoe on 2009-07-02
WRT Java, if you install sun-java6-jdk you get the official version and it will be upgraded automatically.  This version is better than both gij and openjdk IMHO.

---

### Post by Barquero on 2009-07-02
Yahoo changed the login method!

[http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)

---


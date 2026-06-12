---
title: "Am I Hoary???"
date: 2005-02-21
forum: General Help
---

### Post by LongTooth on 2005-02-21
Searching the forums, I used directions to upgrade to Hoary. Those being to change the repositories from'Warty' to 'Hoary'. From there I updated and upgraded. All went well with only one problem. I don't have Java working. 

I've got two question for the forum. 

#1. How do I get Java working again?
#2. How do I know I'm running Hoary? I really don't see any difference from Warty. So an I using Hoary or not?

I did this once before and some one suggested I should have dist-upgrade instead of just update&&upgrade. Bad advice. That really borked my system. So I didn't take that step. But back to my two questions. Advice anyone? Thanks.

---

### Post by poofyhairguy on 2005-02-21
[QUOTE=LongTooth]
I did this once before and some one suggested I should have dist-upgrade instead of just update&&upgrade. Bad advice. That really borked my system.[/QUOTE]

Thats how you get Hoary. Dist-Upgrade is only way. If it borked your system, that is because Hoary was REALLY buggy that day (it happens on somedays, not as much lately).

---

### Post by LongTooth on 2005-02-21
I've got Warty on two machines. I did the repository and 'apt-update/upgrade' change on both. My test box is the one that I'll do the 'dist-upgrade' to and keep my fingers crossed. Don't mind messing up my system on that PC. That's why its a test box! My main box - I'll leave as is for the time being. But it still has the repositories as Hoary. Any problems with that or should I change them back to Warty? 

What should I do about get my Java working on my main box. I miss it. How do I find it and get it linked to my browser? No problem like that with the test box because it has a plain basic install. No flash, java or any tweaking of any kind. Thanks.

---

### Post by brainstuff on 2005-02-21
Just the runtime? Here be a good guide, arrrrrrr.

[http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

 :-)

---

### Post by LongTooth on 2005-02-21
Since I installed Java Runtime on the initial Warty install I am inclined to think I would just have to redirect the Java I already have to my browser. How do I go about that? Or should I follow the step in the Guide? Would having two Java installs gum up the works?

---

### Post by kassetra on 2005-02-21
[QUOTE=LongTooth]Since I installed Java Runtime on the initial Warty install I am inclined to think I would just have to redirect the Java I already have to my browser. How do I go about that? Or should I follow the step in the Guide? Would having two Java installs gum up the works?[/QUOTE]

Well, so I'm assuming you installed it once already through apt, correct?

Here's what I did:
I first installed java through synaptic (apt), and then when it didn't work, I removed it and did what this wiki says to do:[JavaPackage1.5]("http://www.ubuntulinux.org/wiki/JavaPackageBuild15001")

(p.s. having two java installs would just make your life more work)

---

### Post by LongTooth on 2005-02-22
No I didn't install Java via apt-get. Didn't know it could be done that way. I used the method discribed in the Guide. Downloaded from the Sun site. Anyway, I do already have Java installed. Did it when I first installed Warty. So how do I get my already installed Java to work with my browser. Remember, I lost my Java after doing a apt-get update && upgrade after changing my Warty repositories to Hoary.

---

### Post by kassetra on 2005-02-22
[QUOTE=LongTooth]No I didn't install Java via apt-get. Didn't know it could be done that way. I used the method discribed in the Guide. Downloaded from the Sun site. Anyway, I do already have Java installed. Did it when I first installed Warty. So how do I get my already installed Java to work with my browser. Remember, I lost my Java after doing a apt-get update && upgrade after changing my Warty repositories to Hoary.[/QUOTE]

Can you make these links?
 ```
sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
```

---


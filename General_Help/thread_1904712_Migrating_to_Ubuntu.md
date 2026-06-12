---
title: "Migrating to Ubuntu"
date: 2012-01-05
forum: General Help
---

### Post by GERGE on 2012-01-05
I used to hate Ubuntu, it was restricting, always dictating how my system should be (at least I saw it like that), and fixed releases, what a chore.

But I guess I am getting older now. Work takes almost all my time, reading new legistrations, new cases, writing essay, readin and commenting essays... I noticed that I don't have time to tinker with my system. Recently I was even becaming afraid that my system would break with tha new update. My system was great, I had lovingly created up from the command line and used it for years; but as I said, priorities change.

Before I forget to tell you, I was using Arch Linux. And it was really great, but just not for me anylonger. Sad me =(

So, I am migrating to Ubuntu. Installed it; and contrary to all my expectations, even liked Unity. But as I said, I don't want to spend much time searching manuals, reading forums and all. So my questions: 

[LIST][*]Do you have problems with distro updates?
[*]I am a long time user of 7digital, any way to connect my account to Ubuntu One?
[*]Where can I put my startup scripts? I've never used Debian (I have used Arch exclusively for almost a decade with some Suse here ant there), so a small manual aimed to experienced Linux user should be great for these kind of questions I have. 
[*]How does Ubuntu handle power management?
[*]How does this PPA thing work?[/LIST]

---

### Post by Mark Phelps on 2012-01-05
These "laundry list" posts (list of unrelated issues) generally do not work well.

If you have specific issues you want addressed, it really works better if you confine each thread to one issue.

thanks

---

### Post by 2F4U on 2012-01-05
> Where can I put my startup scripts? I've never used Debian (I have used  Arch exclusively for almost a decade with some Suse here ant there), so a  small manual aimed to experienced Linux user should be great for these  kind of questions I have.

The startup scripts you get by default are placed in /etc/xdg/autostart, but I guess if you open the Startup Applications menu (upper right corner) and add something it will be placed in your home folder.

> How does Ubuntu handle power management?

You get the Gnome power management app. What can I say, it works for me. Suspend/hibernate depends on your hardware, but I guess you know that.

> How does this PPA thing work?

In general, it works good. However, I try to keep the ppa's I am using at a minimum. I just have a ppa for Mozilla to get newer versions and on the laptop one additional, which provides advanced power management settings. The problem is that ppa's are a potential security risk since you almost never know the people behind them.

---


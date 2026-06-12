---
title: "Shockingly disappointed..."
date: 2006-02-22
forum: General Help
---

### Post by KubuntuKilledMe on 2006-02-22
I've just had my Kubuntu install messed up so badly I'm not even sure i'll bother to fix it or reinstall it.

I am here not so much to ask for technical assistance as to express my literal _shock_ and disbelief at how can such a thing happen in a modern operating system. I'll try to be quick.

A month ago i finally took the plunge and switched from XP to Kubuntu. I had messed with Linux a lot but never as my full time desktop. My Kubuntu install is 5.10 with some added software from the repositories and then upgraded to KDE 3.5 as i read on kubuntu.org. It was great, i was very happy with my switch, for both practical and ideological reasons. I had a hard time getting my ATI 9600 to work with the ATI proprietary drivers on 3D accel. and dual head at the same time, but i eventually got it working.

I had, however, noticed the desktop was not getting updated to reflect the files changes in ~/Desktop. It would show files that had been deleted, and not show new files. A quick googling aimed me at the "fam" package which was supposedly required to fix my problem. I startup Adept, enter my password, type "fam" in the search box and it shows. I right click the fam package and select install. Click commit. And that was the end of my kubuntu instalation. Adept switched to the text dpkg output view. Suddenly its scrolling. Every line starts with "Removing". I'm a bit surprised as i see it removing almost 400 packages, many of them related to KDE, like Amarok which was _running_ at the time. After removing what i estimate to be around 200 packages, Adept crashed, maybe because it removed itself.

The system boots to a nearly empty KDE with lots of error messages and almost no interface. The few KDE programs that run are presenting "First run" Wizards, after i spent a month setting everything up as i like.

I am now posting from my XP install which i had tought i would use for playing Battlefield 2 only. I am shocked, i cant even find another word. 

I know its open source, and i didn't pay for it. I know all of that. I know the person responsible for the bug or feature that i found is probably not even reading this. But i had to register in these forums and post this to express my sadness.

If anyone is interested in this, i'll try your suggestions on the dead kubuntu install until i clear the partition. And if not, its ok. I can barelly force myself to boot into it right now.

---

### Post by az on 2006-02-22
[QUOTE=KubuntuKilledMe]I've just had my Kubuntu install messed up so badly I'm not even sure i'll bother to fix it or reinstall it.

I am here not so much to ask for technical assistance as to express my literal _shock_ and disbelief at how can such a thing happen in a modern operating system. I'll try to be quick.

A month ago i finally took the plunge and switched from XP to Kubuntu. I had messed with Linux a lot but never as my full time desktop. My Kubuntu install is 5.10 with some added software from the repositories and then upgraded to KDE 3.5 as i read on kubuntu.org. It was great, i was very happy with my switch, for both practical and ideological reasons. I had a hard time getting my ATI 9600 to work with the ATI proprietary drivers on 3D accel. and dual head at the same time, but i eventually got it working.

I had, however, noticed the desktop was not getting updated to reflect the files changes in ~/Desktop. It would show files that had been deleted, and not show new files. A quick googling aimed me at the "fam" package which was supposedly required to fix my problem. I startup Adept, enter my password, type "fam" in the search box and it shows. I right click the fam package and select install. Click commit. And that was the end of my kubuntu instalation. Adept switched to the text dpkg output view. Suddenly its scrolling. Every line starts with "Removing". I'm a bit surprised as i see it removing almost 400 packages, many of them related to KDE, like Amarok which was _running_ at the time. After removing what i estimate to be around 200 packages, Adept crashed, maybe because it removed itself.

The system boots to a nearly empty KDE with lots of error messages and almost no interface. The few KDE programs that run are presenting "First run" Wizards, after i spent a month setting everything up as i like.

I am now posting from my XP install which i had tought i would use for playing Battlefield 2 only. I am shocked, i cant even find another word. 

I know its open source, and i didn't pay for it. I know all of that. I know the person responsible for the bug or feature that i found is probably not even reading this. But i had to register in these forums and post this to express my sadness.

If anyone is interested in this, i'll try your suggestions on the dead kubuntu install until i clear the partition. And if not, its ok. I can barelly force myself to boot into it right now.[/QUOTE]

Breezy is stable.  It does not ship with kde 3.5

---

### Post by KubuntuKilledMe on 2006-02-22
It does not ship with KDE 3.5 but i upgraded as instructed here:

[http://kubuntu.org/announcements/kde-351.php](http://kubuntu.org/announcements/kde-351.php)

Anyway, I am not complaining of unstable KDE.

---

### Post by Robgould on 2006-02-22
I tried kubuntu and ubuntu both.  I know that a bucnch of people will come tell me that they are exactly the same other than gnome or kde, but I will say this anyway.  Ubuntu, for me, worked great.  Kubuntu was trouble from the begining.  So it was back to Ubuntu for me.  That is my 2 cents.

---

### Post by KubuntuKilledMe on 2006-02-22
Can anyone explain what happened? It feels like a dependency issue, but why would it want to remove everything? Does the fam package have a dependency like "must be only package in system"? How can i make sure it won't happen again?

---

### Post by GeneralZod on 2006-02-22
If you're interested in the technical reason why this happened, read on!

"gamin" is the successor to the now-deprecated "fam", and is installed by default.  The two cannot co-exist.  Many packages depend on gamin as it provides what can be an essential service.  Attempting to install fam will uninstall gamin *and all packages that depend on it*, which is how you got where you are today :)

You can probably repair it reasonably easily by uninstalling fam and then re-installing gamin.  You can ensure it never happens again by steering *well* clear of fam :)

The initial bug you spotted sounds like a variant of my pet bug that I reported almost a year ago; you can add your voice and votes [here](https://bugs.kde.org/show_bug.cgi?id=106394), if you want.  I'll probably contact David Faure directly at some point to see if it can be verified by someone high up and fixed upstream because I'm sick of manually patching this every time a KDE security exploit manually comes along.

---

### Post by KubuntuKilledMe on 2006-02-22
Thank you GeneralZod. I had to understand what happened before i could try again. 

I tried to uninstall fam, but it is not installed. As i said, adept crashed before it ended, maybe dpgk removes before it adds? So it would be installed after successfully removing all the others... And i didnt get that far.

Alsok, first run of apt-get (now on the command line, no more Adept) says it was interrupted and wanted me to run "dpkg -configure -a" (or similar, i cant remember exactly). I ran it expecting it to remove the rest of the packages and install fam (system was already hosed, might as well be in a consistent state). It didnt finish removing, it was executed instantly and i was back to the shell. Now it doesnt complain of "interrupted" anymore. 

I'll try to install gamin now.

---

### Post by GeneralZod on 2006-02-22
[QUOTE=KubuntuKilledMe]

I'll try to install gamin now.[/QUOTE]

Forgot to add - you'll want to re-install "kubuntu-desktop", also.

---

### Post by AdrianVeidt on 2006-02-22
Be sure to look at the bar at the bottom of the Adept window before you commit any changes. It passes along information about what's going to happen. It would have said something like "400 packages to be removed, 1 to be installed".

---

### Post by KubuntuKilledMe on 2006-02-22
apt-get says gamin is already installed, so it wont install it + dependencies. Meanwhile you added the kubuntu-desktop package suggestion and i'll try it.

"Be sure to look at the bar at the bottom of the Adept window before you commit any changes. It passes along information about what's going to happen. It would have said something like "400 packages to be removed, 1 to be installed"."

Once i read a joke comparing operating systems, on how much rope they gave you. UNIX joke was "here's enough rope to hang yourself, your users, and a lot more just in case".

I'm pretty sure Adept announced its intentions on the status bar before i hit commit. Reading "man apt-get" educated me on the "no-remove" option. In my opinion, Adept would benefit from having an interface checkbox widget saying "Don't remove installed packages" which would alert me on clicking commit.

Then i could uncheck that checkbox if i knew what i was doing, or if i wanted to find out real fast. If my coding wasnt so rusty i'd propose the patch myself.

---

### Post by z-vet on 2006-02-22
Hmm... fam conflicts with loads of packages. I found fam in Synaptic, tried to mark it for installation and got a huge list of packages that it will remove: everything from adept to saneconsole and secpolicy. Well, my gut feeling about Adept was right: i found this app totally confusing and unusable. Just to be sure i found fam in Adept and marked it for installation. When i click "Commit" it does not show any alert or message, it's just applying changes. Ok, it has a button to preview the changes, but newbies can be easily confused (and that's what happened here). 
KubuntuKilledMe, i think that reinstalling KDE with apt-get will solve your problem.

---

### Post by KubuntuKilledMe on 2006-02-22
I went back to it to install kubuntu-desktop. First i had no networking, couldn't even ping my router. 

sudo /etc/init.d/guarddog stop

fixed it but its strange as i had never used guarddog before. Now with networking i try to install kubuntu-desktop but it complains about lots of dependencies that "will not be installed". I install a few of them by hand, but some had more dependencies that also would not be installed and pretty soon i had dozens of dependencies to install manually. Turns out that what apt-get wanted was to remove more packages. Probably the ones it couldn't remove before adept crashed. So with one of the dependencies i installed, it removed a bunch more of packages and then kubuntu-desktop installed cleanly.

The thing is, my kde interface ("start" menu, window, list, pager, clock, systray) is reduced to 3 buttons i added manually some time ago. All the default elements are missing. Right clicking to configure it show everything ok, as the elements are selected to be presented, but they don't show up.

At this point my question is, can this install be returned to a consistent state or should i just backup /home and /etc and reinstall?

---

### Post by eMuNiX on 2006-02-22
After months of great performance from Kubuntu my gamin has suddenly decided that it will use 40%+ resources which causes my KDE to be almost unuseable.  Switching off the services instantly brings the performance back again it only affects KDE, both Gnome and Xfce work brilliantly.  The only thing that I have done to my machine in way of changes is to replace my ADSL router for a new ADSL2/2+ version nothing else has changed.  It is a PITA because for months KDE has been performing so well.

---

### Post by KubuntuKilledMe on 2006-02-22
Also, am i wrong in thinking the "fam" package should be removed from repositories? Notice there is a known bug in KDE to which a quick googling will suggest the instalation of fam. I doubt i'm the first one to fall on this trap, as the threads i found in google are abruptly finished after comments like "I wonder why fam doesnt come installed by default?" Is there any event in which the fam package can be useful in a breezy install?

---

### Post by Qwertie on 2006-02-22
That is shocking!  It sounds like Adept needs to be more reluctant about uninstalling things--you know, like showing a warning box with a list of programs to be uninstalled.  And maybe uninstalling packages Adept itself depends on might be disallowed or strongly discouraged.

---

### Post by aysiu on 2006-02-22
Has anyone filed a bug report on this "fam" thing? Why is it even a package available in the repositories if you're supposed to use "gamin" instead?

---

### Post by Jucato on 2006-02-22
Maybe it's still there for Hoary users? I mean Ubuntu is supposed to provide support for an older version upto 18 months after a newer version is released. Since Breezy was released October 2005, Hoary is supposed to be still supported until April 2006. that is, IF fam is default in Hoary, just as gamin is default in Breezy.

I strongly recommend (once you get your system up and going) to use Synaptic instead of Adept for the mean time. Take note that Adept is not a KDE project but only a Kubuntu project (KPackage is the KDE package manager). Adept is still a baby when it comes to handling this stuff, and you're not the only one to have had trouble with it removing stuff without confirmation.

---

### Post by raul on 2006-02-23
sorry to butt in, complete newbie here. gamin is also using a substantive % of my cpu. i was wondering if gamin is a kubuntu-only process though, or if it's also essential to gnome. i ask because i decided to give kdm a try (i'm an original gdm user) and hated it. i already uninstalled kubuntu-desktop, but now gamin is consuming my cpu usage on gnome. no process in gnome used that much cup before i installed kdm. i was thus wondering if there anyway to stop gamin on gnome... if so, can i still keep some kde applications? (for instance, i'd like to keep konqueror; i prefer it over nautilus).

thanks in advance

---


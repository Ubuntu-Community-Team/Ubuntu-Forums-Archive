---
title: "Adept uninstalls EVERYTHING?!"
date: 2006-02-08
forum: General Help
---

### Post by Steve Max on 2006-02-08
I've been helping my girlfriend to install Kubuntu (5.10). That's the first time she got brave enough to try Linux, and I've been trying to make that as painless as possible. Not that installing a dial-up modem could be painless, and the fact that we are 500 km apart also doesn't help, neither the fact that I've never ran a Debian-based system (she saw Kubuntu at my mother's and decided for that one), but.... Well, it was working. 

Now, she wanted to install X-Chat. We added "universe" and "multiverse" to the repositoiries on Adept, fetched updates, she selected X-Chat, clicked on install, Adept asked for the installation DVD, and... her whole system got uninstalled.

Now, she's crying over the phone, saying she won't ever again touch this thing. That she can't trust Linux, that she lost everything, "imagine if this happens again in 1 year", etc.

How the hell can a package management system uninstall your whole system per default?! I know, someone will say something about "having to select the right packages", but, why aren't the ones you already have selected? Is it "remove-by-default" or "keep-by-default"?

Seriously, how serious is a distro that doesn't even keep stuff you don't tell it to delete? How did this get pass the quality control?

Kubuntu has just made a woman with a pro-OSS mind say, in tears, that "even Windows XP is better than Linux". Thank you very much.

---

### Post by obibok on 2006-02-09
Please define "*her whole system got uninstalled*".

Package managers, such as *Adept*, are interactive applications and they never do anything without user confirmation. *Adept* has a "Preview Changes" option which will allow the system administrator to review actions and take appropriate steps. Moreover, working as *root* always requires your utmost attention to any actions you take - especially software and file management. This is actually true for any operating system.

For comparison, in Windows under the default account (which happens to be *Administrator*) you may very easily delete vital system DLL files and render your system "uninstalled". There are no "remove-by-default" or "keep-by-default" mechanisms in place here either. As a matter of fact, you could get your Windows system wiped out by simply visiting a web page with a specially formatted image.

As for *Windows XP* being better than *Linux* - "de gustibus non est disputandum" [-(

---

### Post by Steve Max on 2006-02-09
Removing kubuntu-desktop ...
Removing powermanagement-interface ...
Removing acpi-support ...
 * Disabling power management...                                                                                               [ ok ]
Removing adept ...
Removing akode ...

And all the other packages.

No confirmation. The point is, a package manager should, BY DEFAULT, keep your existing packages. That's what happens with (for instance) Slackware's pkgtool: if you choose to install a package, it installs that package. She choose to install a package, Adept would uninstall everything and keep only that package!

Looks like you have to select every single package that's in your system if you want to keep them. I have no idea on why a package management system would behave like that.

Your analogy is incorrect. Imagine, in Windows, if it removed your \winnt and \program files when you installed MS Office, unless you selected every file you already have on that list of components you want to install.

---

### Post by Jucato on 2006-02-09
A package manager does keep existing packages EXCEPT in the case that an older/installed package would conflict with something the administrator/root is trying to install. In this case it removes the older package. 

Adept doesn't prompt you for your confirmation during the installation process itself, because you're supposed to check everything before pressing the "Commit Changes". Sure, a prompt would be nice, but that's what the sudo/kdesu is for, a sort of reminder that whatever you will be doing might mess your system, so you better know what you are doing. Also, even without using the "Preview Changes" button, Adept displays at the status bar how many files will be installed, removed, or upgraded. Bottom line is, whenever you are being asked for your root password, remember that your actions will have drastic effects on your system, for better or for worse. 

My guess is that one of KDE's basic libraries, which all those other apps depended on, was to be removed. I'm not sure how that happened, I tried installing X-Chat, and it was successful. Also, did you disable/comment out the cdrom repository? If I'm not mistaken, once you've installed and enabled the other repositories, that cdrom repo is practically useless, and any update/upgrade shouldn't be asking for a cd/dvd.

I think a more proper analogy to Windows is installing a software that overwrites certain vital DLL's, affecting the system.

---

### Post by aysiu on 2006-02-09
Can you or she post the contents of the /etc/apt/sources.list file? This sounds like some kind of fishy repository conflict. When you "enabled universe and multiverse," how did you do so?

---

### Post by FlakJacket on 2006-02-09
I did this also when i was trying to install a new version of glib and it told me I had to uninstall the older version.  Uninstalled just about everything including adept and kubuntu-desktop.  Rather than bother with trying to download the packs individually on another computer I just reinstalled Kubuntu, the installation was only a couple days old.  I have definitely learned my lesson now.  I'm always going to check what exactly will go down before hitting commit, I bet she learned too.  Linux has definitely made me more aware of what I'm doing as far as tweaking, because when you can tweak more things than windows you can also get in more trouble.

Flak

---

### Post by thespinesplitter on 2006-02-09
[QUOTE=Steve Max]Removing kubuntu-desktop ...
Removing powermanagement-interface ...
Removing acpi-support ...
 * Disabling power management...                                                                                               [ ok ]
Removing adept ...
Removing akode ...

And all the other packages.

No confirmation. The point is, a package manager should, BY DEFAULT, keep your existing packages. That's what happens with (for instance) Slackware's pkgtool: if you choose to install a package, it installs that package. She choose to install a package, Adept would uninstall everything and keep only that package!

Looks like you have to select every single package that's in your system if you want to keep them. I have no idea on why a package management system would behave like that.

Your analogy is incorrect. Imagine, in Windows, if it removed your \winnt and \program files when you installed MS Office, unless you selected every file you already have on that list of components you want to install.[/QUOTE]


what  these nice folk are trying to say is that you have the completely wrong idea of what the package manager is doing, i have never seen a package manager behave the way u described, u have got urself a problem no "quality control" can fix

---

### Post by Jucato on 2006-02-09
actually, it can uninstall everything, but with warning. this happened to me when I tried to downgrade/remove a specific library, which was being used by 60+ apps, including kdm and adept itself. So what happened is not an isolated case. It's just a case of not knowing what to do.

A big difference between Windows and Linux is this: Windows presumes that users are either too dumb or uninterested to be bothered by details about the OS, at the same time, sacrificing functionality and power (almost GNOME-like, but even GNOME is waaay better). Linux, on the other hand, presumes one logical thing: you SHOULD know  what you are doing. And if you don't, either don't do it, or try to know. It's not an irrational expectation, and you don't have to be a computer engineer/scientist to know that "40 to be removed" at Adept's status bar spells trouble. Forgive me for using this worn-out cliche: "With great power comes great responsibility."

EDIT: No offense meant whatsoever. I'm just saying that be careful next time, whether in Windows or somewhere else.

---

### Post by newuser111 on 2006-02-09
next time fix your girlfriends computer by ssh or remote desktop, sounds like she didnt know what she was doing

i have never seen that problem before, but then again I dont use adept, but I do use synaptic or aptitude, the only way to uninstall that many packages was if she accidently selected an important system component (like kde libs or something) for removal and it uninstalled every depedency of that

but it does give you a list of what its going to uninstall, at least synaptic even tells you when you select something for removal, that makes it the safest to use and its the default in ubuntu (but not kubuntu, which I think it should be as well)

---

### Post by FlakJacket on 2006-02-09
[QUOTE=Fenyx]actually, it can uninstall everything, but with warning. this happened to me when I tried to downgrade/remove a specific library, which was being used by 60+ apps, including kdm and adept itself. So what happened is not an isolated case. It's just a case of not knowing what to do.

A big difference between Windows and Linux is this: Windows presumes that users are either too dumb or uninterested to be bothered by details about the OS, at the same time, sacrificing functionality and power (almost GNOME-like, but even GNOME is waaay better). Linux, on the other hand, presumes one logical thing: you SHOULD know  what you are doing. And if you don't, either don't do it, or try to know. It's not an irrational expectation, and you don't have to be a computer engineer/scientist to know that "40 to be removed" at Adept's status bar spells trouble. Forgive me for using this worn-out cliche: "With great power comes great responsibility."

EDIT: No offense meant whatsoever. I'm just saying that be careful next time, whether in Windows or somewhere else.[/QUOTE]

Exactly what I was saying \\:D/

---

### Post by Steve Max on 2006-02-10
[QUOTE=Fenyx]My guess is that one of KDE's basic libraries, which all those other apps depended on, was to be removed. I'm not sure how that happened, I tried installing X-Chat, and it was successful. Also, did you disable/comment out the cdrom repository? If I'm not mistaken, once you've installed and enabled the other repositories, that cdrom repo is practically useless, and any update/upgrade shouldn't be asking for a cd/dvd.[/quote]

No, didn't comment it out. She has slow dial-up access, and the installation doesn't install everything that's on the DVD (including some bigger packages), so it should still be useful.

Why would a kde library be removed? Are QT and GTK mutually exclusive in Ubuntu? :)

[quote=newuser111]next time fix your girlfriends computer by ssh or remote desktop, sounds like she didnt know what she was doing[/quote]

Does Ubuntu install a ssh daemon by default? (It would be weird, installing sshd and not installing gcc...). That was the first package she installed with apt. And no, she didn't know what she was doing, that was the first time she was using linux. "Newbie friendly"?

[quote=newuser111]i have never seen that problem before, but then again I dont use adept, but I do use synaptic or aptitude, the only way to uninstall that many packages was if she accidently selected an important system component (like kde libs or something) for removal and it uninstalled every depedency of that[/quote]

That's my point. Synaptic (and its KDE counterpart) are VERY mature and dependable. Why does kubuntu use something that does't even warn you that there's something wrong? All she did was select xchat for installation, nothink for removal.

[quote=thespinesplitter]what these nice folk are trying to say is that you have the completely wrong idea of what the package manager is doing, i have never seen a package manager behave the way u described, u have got urself a problem no "quality control" can fix[/quote]

Sorry, is it normal for a package manager to uninstall your whole system when you tell it to install one package? Every single manager I've ever used is abnormal? pkgtool and portage are unnaturally useable, in that you don't have to specify that you want everything else to stay there? Portage stops the installation process if there's a conflict, you choose if you want to remove the previous package and install the new one, keep the old one, or force install the new. Must this functionality be removed, as it is a slap in the face of God? :cool: 

[quote=aysiu]Can you or she post the contents of the /etc/apt/sources.list file? This sounds like some kind of fishy repository conflict. When you "enabled universe and multiverse," how did you do so?[/quote]

Sorry, apt-get got uninstalled too... Followed the first documentation I found: [https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a](https://wiki.ubuntu.com/AddingRepositoriesHowto#head-3af7264a0e97edbc5bf039e5bdb971f46c43269a)

[quote=FlakJacket]I did this also when i was trying to install a new version of glib and it told me I had to uninstall the older version. Uninstalled just about everything including adept and kubuntu-desktop.[/quote]

Sound like what's happened to her. It's possible that there's a new glib out there, and xchat does depend on it. But why uninstall everything first? Why not package-per-package? Sound too much like the RPM Hell© I've been into for some time... If you reinstall a package with the first number intact (i.e. 2.8.x to 2.10.x), the binary compatibility is kept. The other software doesn't need to be reinstalled (with rare excaptions). I should know that, as slackware packages have no dependency meta-info at all, and when we went from QT 3.3 to 3.4, no need to reinstall KDE. Even from GCC 3.3 to 3.4, binary compatibility was kept.

So no, this is NOT a good package manager behavior: this is a package manager following the meta-information on the packages blindly, and/or (probably, I don't know the .deb system) uninstalling + installing packages it should upgrade.

*** EDIT: quote --> /quote

---

### Post by Jucato on 2006-02-10
CD/DVD repositories might be months old. If she did some updating online before trying to install X-Chat through the DVD, it might have caused some conflicts between some libraries.

Qt and GTK are not mutually exclusive, but they are not best of friends either. :D
There might be some conflicting libraries. This is not exclusive to Ubuntu, but to any other distro. It's just that sometimes, a particular app has not been updated to the latest libraries, or something like that. There are many factors may cause some library to be removed.

Unfortunately, Adept is not Synaptic's KDE counterpart. Adept, AFAIK, is something being developed by Kubuntu. KPackage and Kynaptic are the KDE counterparts, with KPackage taking lead. Adept is also very young compared to any of these package managers. 

Since I have no experience handling RPM based distros, all I know is that apt-get and it's front-end counterparts informs you of what it will do BEFORE installation, and not during. It sort of tells you to review the changes before proceeding. Of course, Adept does not prompt you, but it displays the information in the status bar. All the others (dpkg, apt-get, Synaptic, KPackage) prompts you before you proceed. However, Adept does not proceed with the installation IF the installation will cause some dependencies will be broken.

An example situation where a library may be removed is when there is a newer version available.  
An example situation where dependencies might be broken: trying to install a package together an older version of a library, when the most recent version is already installed.

We really can't diagnose what the problem was with your girlfriend's system, since we don't know what happened exactly. Why not let her try out and RPM-based distro, if that's what you are more used to. Tell her not to get discouraged with this failure (heck I reinstalled Kubuntu 3 times). It happens, even in Windows.  Just learn from these experiences. Make backups of your important data. Put the /home in a separate partition so that data (and sometimes settings, too) can be recovered even after reinstalling.

Newbie(your girlfriend)-friendly is not the same as dumb(someone else)-friendly, which is what Windows expects its users to be.

---

### Post by steevc on 2006-02-10
I have had an instance where I was trying to just remove an older version of Skype so I could install a new one. During the removal I saw all my KDE files being uninstalled, which was a bit of a shock. Luckily I'm on broadband, so I was able to reinstall quite quickly, but it was not what I expected.

Could it be that the Skype uninstall tried to remove some vital file?

I don't think I have any logs now that would help in diagnosing the issue.

---

### Post by Steve Max on 2006-02-10
> **Fenyx]CD/DVD repositories might be months old. If she did some updating online before trying to install X-Chat through the DVD, it might have caused some conflicts between some libraries.[/quote]

All she installed was a couple of packages for the modem kernel driver. I don't think this could mess with any library...

[quote=Fenyx]Qt and GTK are not mutually exclusive, but they are not best of friends either. :D
There might be some conflicting libraries. This is not exclusive to Ubuntu, but to any other distro. It's just that sometimes, a particular app has not been updated to the latest libraries, or something like that. There are many factors may cause some library to be removed.[/quote]

But the main fact is that they shouldn't be :) Even if there was a new version, you don't need to uninstall the old one and everything that depends on it. If two libraries conflict, they probably provide the same functionality (like libungif and giflib), so the packages they depend can be safely reinstalled in no time.

Don't tell me that removing a library means you MUST remove all that depends on it before: I have just removed all my old xorg-6.8.x and installed the modular x-server (xorg 7.0), all within KDE...

[quote=Fenyx]Unfortunately, Adept is not Synaptic's KDE counterpart. Adept, AFAIK, is something being developed by Kubuntu. KPackage and Kynaptic are the KDE counterparts, with KPackage taking lead. Adept is also very young compared to any of these package managers.[/quote]

Exactly what I've said :) Either one would be a better choice for a production distro. There are others that had problems here. The application is not ready to be the primary package manager of any distro.

[quote=Fenyx]Since I have no experience handling RPM based distros, all I know is that apt-get and it's front-end counterparts informs you of what it will do BEFORE installation, and not during. It sort of tells you to review the changes before proceeding. Of course, Adept does not prompt you, but it displays the information in the status bar. All the others (dpkg, apt-get, Synaptic, KPackage) prompts you before you proceed. However, Adept does not proceed with the installation IF the installation will cause some dependencies will be broken.[/quote]

It doesn't proceed with the installation if some dependencies would be broken, but breaks your system if you ask for a package? Nice behaviour  said:**
> An example situation where a library may be removed is when there is a newer version available.  
An example situation where dependencies might be broken: trying to install a package together an older version of a library, when the most recent version is already installed.

I'm not sure if I understood you well... But asking for an old version shoudn't break, if the old and new versions of the library are binary compatible and you didn't install anything that uses the new features of the library. But if you DID, why would you want to downgrade? :-)

[quote=Fenyx]We really can't diagnose what the problem was with your girlfriend's system, since we don't know what happened exactly. Why not let her try out and RPM-based distro, if that's what you are more used to. Tell her not to get discouraged with this failure (heck I reinstalled Kubuntu 3 times). It happens, even in Windows.  Just learn from these experiences. Make backups of your important data. Put the /home in a separate partition so that data (and sometimes settings, too) can be recovered even after reinstalling.[/quote]

I don't use anything even close to RPM since a bad Mandrake install corrupted my hard drive :) I use Slackware (home) and Gentoo (work), but neither of these are for the faint of heart. I woudn't ask her to edit config files by hand, or to download the whole KDE sources over dial-up to get the system up. (K)Ubuntu was her choice, I agreed with that because the alternatives weren't good (RPM/Slack/Gentoo), and Ubuntu has been so praised on /. that even I considered the idea of installing it :) Yesterday's bunch of updates on slakcware-current made me forget it completely, though. And yes, /home on a different partinion is a good idea. Actually, /boot should be separated, too. I don't know why the "going-with-defaults" on every distro out there installation doesn't offer that...

---

### Post by Jucato on 2006-02-10
Ok, let me just first say that I actually don't like (bordering upon hate) Adept. It's not that adept (forgive the pun) in doing what it should. Ever since I tried out Synaptic I stuck with it. I'm also looking at KPackage, but it's not that good. The only reason that I'm having mercy upon the poor critter is that it's still young. But still not that good. It's fast, though.

Another thing: I'm also a bit new to this stuff so take my opinions with a grain (or a whole spoon) of salt. 
I think there's a difference between removing packages and breaking packages. In removing packages/libraries (and some things that depend on it), apt-get and others merely ask you if this is what you want. In breaking packages, they will not even process the request, and will stop before even downloading/modifying anything. I don't know what are the factors that lead something to be removed or to be broken, but those things happen.

Let me try to be concrete, with an example from my own experience, which led to half of my system (including KDM and Adept) to be removed. I'm working from memory here, so the library name might be wrong.

Almost all KDE apps depend on a library called libxrender (i think that's the repo version). Now, I tried to install the latest GIMP version from a .deb (not in the repo). But GIMP needed a newer version of libxrender, so I  installed that from a .deb also (also not from the repos). Everything went smoothly and now all KDE apps are leaning on that newer libxrender version. Now here's when the problem starts. When I try to install some KDE stuff from the repos, it tells me that it can't proceed because some dependencies will break. Why? Because those apps from the repos depend on the older version of libxrender. It can't install that older version because all the other installed KDE Apps are now dependent on the newer (and installed) libxrender. apt-get, adept, synaptic, and kpackage all warn me about this and stubbornly refuses to continue. So I guess this is an example of breaking dependencies. My memory is now hazy as to what I did to completely uninstall my system, but it happened when I tried to manually downgrade that library. I can't give you a concrete example of a situation where I installed a package, and something gets uninstalled. I've had lots of those, but I didn't document them. Maybe I'll remember something later.

As for a really newbie-friendly distrobution, I'm not really sure, but I've heard that Mepis might be good. I could give you links that could help you decide what to choose: [http://distrowatch.com/]("http://distrowatch.com/") and [Linux Distrobution Chooser]("http://www.zegeniestudios.net/ldc/").

Ubuntu is not really 100% for newbies. It stands nicely in the middle ground between newbies and experts. It doesn't require you to be a genius, but it does require you to try (keyword: try) to know what you are doing. And the community here is great. Don't hesitate to ask.

... and ditch Adept, for now. :D

---

### Post by versaq on 2006-10-17
Sorry to bump such an old thread, but I had this problem last night.

The problem is that the package 'kubuntu-desktop' thinks that it's dependant on everything that came with kubuntu.

I've found replacements for many of the packages that came with kubuntu --like synaptic instead of adept, but if you try to remove adept, it also removes kubuntu-desktop and everything else kubuntu.
Of course, adept will remove everything without question, and without informing you that you just indirectly marked your entire system for removal... unlike synaptic which will warn you if your choice affects other packages.

This 'dependency' is absurd and needs to be removed from ubuntu. There's no good reason for me to have to keep unused programs like adept, kopete, etc.

any ideas? :confused:

---

### Post by skymt on 2006-10-17
> **versaq said:**
> Sorry to bump such an old thread, but I had this problem last night.

The problem is that the package 'kubuntu-desktop' thinks that it's dependant on everything that came with kubuntu.

I've found replacements for many of the packages that came with kubuntu --like synaptic instead of adept, but if you try to remove adept, it also removes kubuntu-desktop and everything else kubuntu.
Of course, adept will remove everything without question, and without informing you that you just indirectly marked your entire system for removal... unlike synaptic which will warn you if your choice affects other packages.

This 'dependency' is absurd and needs to be removed from ubuntu. There's no good reason for me to have to keep unused programs like adept, kopete, etc.

any ideas? :confused:

kubuntu-desktop is a metapackage. It's supposed to depend on everything else. It's completely safe to remove. See the [wiki](https://help.ubuntu.com/community/MetaPackages). If adept is trying to remove everything kubuntu-desktop depends on, then that's a problem. Use dpkg or Synaptic to remove it.

---

### Post by versaq on 2006-10-17
**Thanks!**
I had tried to use adept to remove kopete, and it removed everything (154 packages) and trashed my system.

After removing kubuntu-desktop, I uninstalled kopete (and adept) without issue.

odd.
reverse dependencies?

---

### Post by skymt on 2006-10-17
> **versaq said:**
> **Thanks!**
I had tried to use adept to remove kopete, and it removed everything (154 packages) and trashed my system.

After removing kubuntu-desktop, I uninstalled kopete (and adept) without issue.

odd.
reverse dependencies?

It's Adept. It's no good, so don't use it. Aptitude also tracks and removes unused packages, but it's much better at it.

---


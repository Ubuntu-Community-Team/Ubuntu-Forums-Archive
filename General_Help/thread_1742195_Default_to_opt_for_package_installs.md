---
title: "Default to /opt for package installs?"
date: 2011-04-28
forum: General Help
---

### Post by Lolpanda on 2011-04-28
Friend asked me an interesting question today. We were talking about having a 'fallback' option in Ubuntu / other Linux distros so that if you wanted to default to stock ubuntu with none of your personal additions (excluding updates)

and we came up with the idea that if dpkg / apt would install anything NEW to /opt, then you could go back to a vanilla install by just doing


> sudo rm -rf /opt * (Might have that syntax wrong but you get the idea)

and then you have a essentially a clean install. 

Out of curiosity more than anything else, we started looking around, googling possible ways to phrase that question and nothing came up. So does anyone know of a way to set that up?

I know you can add /opt/ to your PATH variable so that you can put an executable there and BASH will find it. But I didn't  know if you could do it for install things there by default.


If nothing else at least it would give Ubuntu a more centralized place to install applications / view all parts of a applications because roaming through /etc/, /usr/, /bin/ and everything else that comes with the "AWESOME" Filesystem Hierarchy we still have is a pain.

---

### Post by VCoolio on 2011-04-28
You'd have to manually install / compile everything to get it to /opt. Do a clean install, put the names of all installed packages in a txt file. Whenever you want to get back, put all installed packages in a 2nd txt file, remove everything that's only in the 2nd. 
Also, if you install to /opt, you get the same file hierarchy, only in /opt and not in /.

---

### Post by Lolpanda on 2011-04-28
> Also, if you install to /opt, you get the same file hierarchy, only in /opt and not in /.


Really? That seems odd because if I would install wine to /opt/ I would expect it to be


/opt/wine/
/opt/wine/bin
/opt/wine/src
/opt/wine/ .... ... ...

which honestly is a lot more easy to maintain and follow than having some files in

/etc/
/usr/
/bin/
/usr/bin/
/usr/local/bin/
/usr/local/share/

and heaven only knows where else it might install it. Atleast with everything to /opt/ if I wanted to, had to, just get rid of wine completly I could just delete the /opt/wine/ directory and know everything was gone. 

With having everything spread out its a pain to track down every single possible file that got thrown around from Wine when it was installed

---

### Post by VCoolio on 2011-04-28
That is if you install wine to /opt/wine. Then it becomes /opt/wine/{etc,bin,lib,share}. If you install with apt-get or .debs, it's /usr/{etc,bin,lib,share}. If you compile and don't specify prefix, it's local by default: /usr/local/{etc,bin,lib,share}.

You can do dpkg-query -L package to see what files "package" installed where.

---

### Post by mc4man on 2011-04-28
Apt/dpkg doesn't decide where to install packages, that's set in the package(s) itself
So, as noted, you'd need to build and install, (or build, package and install), sources specifying  to install to /opt or /usr/local, whatever

---

### Post by Lolpanda on 2011-04-28
That..is unfortunate. Though even if wine still had etc, usr, bin, local under /opt/ atleast i could still just delete /opt/wine and wipe it out.

And thanks for the response guys. Guess I can just chalk this up as another reason why FHS needs a revamp.

---

### Post by srs5694 on 2011-04-28
Your idea would create several new problems. Off the top of my head:


[list]
[*]Doing an "rm -r /opt/{whatever}", when the Debian package system (or RPM on RPM-based distributions, portage on Gentoo, etc.) installed files there would make the package system inaccurate. This would likely have consequences down the road, such as packages installing without necessary dependencies because the user erased them manually. This is not good.
[*]You'd need a *much* longer PATH environment variable, and it would need to be updated much more frequently. After installing a package (say, foo), you wouldn't be able to run it just by typing "foo argument1 argument2"; you'd need to type "/opt/foo/bin/foo argument1 argument2", at least unless and until you update the PATH variable in the currently-running shell.
[*]Consider fonts, multimedia files, clip art, icons, etc. Whether they're installed as part of a package that does something else (say, the foo MP3 player) or by themselves (say, the bar font collection), putting them in their own subdirectories under /opt makes them harder to locate from other programs. You could, of course, implement a search path akin to the PATH environment variable for each of these file types, but that imposes a burden on every developer to support the new environment variable. Alternatively, you could put such packages outside of /opt, but that then makes your stated goal of being able to revert to an out-of-box configuration by typing "rm -r /opt/*" impossible.
[*]What about updates? If the system installs with, say, foo 1.2 and then foo 1.3 comes out and you install it, where would you put the update? If you replace the original files (located outside of /opt), then your goal of being able to revert to a pristine as-installed state by doing an "rm -r /opt/*" would be compromised. If you remove the original files and then install in /opt, then doing "rm -r /opt/*" will wipe out the foo package. If that package is critical, then the system might not even boot any more.
[*]What counts as something that was part of the original installation? I don't recall what Ubuntu's installer does offhand, but many Linux distributions provide the means to set large groups of packages, or even specific packages, to be installed or omitted at system installation time. Although you could theoretically put all the stuff installed initially outside of /opt and then everything installed later in /opt, that would create a great deal of system-to-system variability that might easily result in confusion or even bugs. Consider a user wondering why the foo binary is /usr/bin/foo on one system but /opt/foo/bin/foo on another. What about when a user posts to a forum "just delete the /opt/foo directory" and it's not there on the system that the reader is using?
[/list]


Although I understand you're trying to create a more humanly-accessible method of accessing programs, it would be a colossal step backward. The Debian package tools (dpkg, apt-get, and so on) provide the means to manage packages very nicely. The system you describe is very Microsoft-like, in the sense that it's similar to what Microsoft does in Windows, and although it's got its merits, it just does not fit well in a Unix-like environment or with the packaging tools that most Linux distributions, Ubuntu included, provide. Those tools handle most of the problems that your system is intended to handle quite well, and this arrangement is time-tested and avoids many of the problems associated with the Microsoft system.

I admit that the FHS system is confusing to newcomers. That's because it's been carefully designed by experts for use by experts. Most modern Unix-type OSes do a good job of hiding the complexity of this layout from casual users, but the complexity is there for a reason, and making the types of changes you suggest is likely to cause problems.

---

### Post by Lolpanda on 2011-04-28
You bring up several valid points srs, but one is invalid. Fourth point down; updates. I mentioned in the original post that I was counting updates as part of the original installation. To keep it going with wine, if Ubuntu would ship with wine 1.3, by default. Update comes along a month later, hey, wine1.4 its still "wine" and therefore would keep its current spot under /etc/ or /usr/

And yes, I was suggesting, on purpose, a more Windows or OS X style Filesystem set up. Mainly because I see a lot of unnecessary overlap. Back in the 80's when it probably would've been common for one university to have only a couple computers and several hundred people, teachers, students, admins, alike all had to use them. It probably made a lot of sense to split things up between /bin, usr/bin, and usr/local/bin, etc. In order to have a very finely tuned set of security and limitations so that a student couldn't play Network Admin and crash everything. 

But I don't really think thats the case now. Computer's are cheap, (in comparison) and 1 or more computers per person, where ONE person is the only one using it, is fairly common. 

Also, yes. The current package manager tools do a VERY excellent job at handling packages...that are in the repo's or that have specific .debs and .rpms. And maybe its my slight OCD acting up, but I like to have a uniform system and that uniformity gets screwed up the second I have to install something thats in .tar.gz because I am NOT spending the next 3hrs to perfectly extract every file and put it the same place the package manager would if I was installing from the repo's. 

How many bin folders does the FHS have? I've counted 4 at a minimum. How many Program Files does windows have (excluding 7 cuz they split it between 32 bit and 64bit) 1. You want to install something? There is absolutely no question where you put it. Mac's (to my knowledge) are the same way, they have /Applications.



Edit: Not that I did take offense to the 'newcomer' comment, because I didn't but just to clarify-- while I do not consider myself a linux guru, I've done quite a few Arch and Gentoo, and even BSD installs to know how things work. This is more about practicality / principle.

Edit2: GoboLinux managed to achieve a more Simplified structure through symlinks (im guessing somewhere around 300 symlinks considering how condensed they got it.) And maintains full, 100% linux compatibility.

So it is possible, if you're careful;


Edit3: First point you made about inconsistencies with the package manager I've thought of a way to prevent it. If we assume that things go under /opt/, then we keep a text file of everything installed there. Packages could have a .info file in their root directory of /opt/ that would say their name, and version. Text file keeps a listing of all these. Then 1 of 2 things happens, or both. If it needs to handle dependencies then it reads the file, if the dependency is installed great it keeps going. If its not, it installs it and adds it to the list. Now every so often, (during boot?) the package manager would do a quick scan of /opt/, adding any new entries, and removing any entries that are no longer there. Similar to how Synaptic keeps a listing of all installed and not installed. 

As for the other point you made, fonts. Fonts are different then programs, I really don't know anyone that actually removes a font after they install it. I think mac keeps them under /System/Fonts, could very easily just have that (or the equivalent) be the default install path for them. Again, do we need per user installed fonts? THere's global fonts and then theres ~/,fonts. Necessary? Doesn't seem so. Who complains about having their brothers/sisters/dads/mothers fonts mixed in with theirs? Most people don't even install custom fonts unless they need them for something art related. 

Icon's and clipart I can't really say I have a fix for

---

### Post by srs5694 on 2011-04-29
I was going to do a point-by-point rebuttal of your latest post, Lolpanda, but it's not worth it. Clearly you want a Microsoft-like OS, at least in how it manages its software installation. I don't. I dealt with that sort of thing for years (mostly in Mac OS and then OS/2, but it was the same thing there), and it was incredibly frustrating to me. Linux package management makes it easy to install and uninstall software, and there's seldom a need for the user to know where individual files go. If there's a program that you can't install in that way, you can put it in /usr/local or create your own package. (That's pretty easy with alien, BTW.)

FWIW, I think the Microsoft way is what it is because of floppies; in the days of DOS, users had no choice but to manage their software manually using floppy disks, isolating each program to a single disk. When hard disks came along, those habits carried over to hard disks; it's just that floppies became directories. Unix, OTOH, had hard disks from the start, so there was no need to organize files in that way and a more sensible system evolved.

I'm not sure why you'd want to do an uninstall of all the software you've installed after system installation, really; certainly I've never wanted to do this. You could probably do it by taking a listing of the packages that are installed immediately after installation (by doing "dpkg --get-selections > installed-software", as described [here](http://ubuntuforums.org/showthread.php?t=261366)), then writing a script that uninstalls anything *not* in that list and using it when you want to revert. (Actually, I think that perhaps just "dpkg --clear-selections && dpkg --set-selections < installed-software && dselect" would do the trick, but I'm not positive of that. I see there's [this thread](http://ubuntuforums.org/showthread.php?t=442974) on the topic, too, although the purpose there seems a bit more complex.) You could also probably do something using LVM's snapshot feature, but that strikes me as an ugly hack. In other words, there are almost certainly ways to do what you want much more cleanly than in the way you propose.

---


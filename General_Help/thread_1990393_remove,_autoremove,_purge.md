---
title: "remove, autoremove, purge"
date: 2012-05-29
forum: General Help
---

### Post by charleswb on 2012-05-29
Looking for an indepth comparison/contrast between remove, autoremove, purge and any other similar commands for uninstalling using apt-get, and also aptitude.

Also, is there and aptitude version of uninstalling? What is aptitude? I installed it, but don't really understand it and don't use it. It seems like an aftermarket program for installing and removing software? Is that correct? What are its advantages or disadvantages?

My knowledge of these things is increasing thanks to you good folks at this forum, but I still think I have a few things to learn about these programs, commands, and their options.

**Edited in Later: ** P.S. - I have been able to run apt-get autoremove on some things, but usually it won't run. apt-get remove always runs, as does apt-get purge. Why is autoremove seemingly finicky about when it will or won't run to remove something?

---

### Post by dniMretsaM on 2012-05-29
> **charleswb said:**
> Looking for an indepth comparison/contrast between remove, autoremove, purge and any other similar commands for uninstalling using apt-get, and also aptitude.

Also, is there and aptitude version of uninstalling? What is aptitude? I installed it, but don't really understand it and don't use it. It seems like an aftermarket program for installing and removing software? Is that correct? What are its advantages or disadvantages?

My knowledge of these things is increasing thanks to you good folks at this forum, but I still think I have a few things to learn about these programs, commands, and their options.

**Edited in Later: ** P.S. - I have been able to run apt-get autoremove on some things, but usually it won't run. apt-get remove always runs, as does apt-get purge. Why is autoremove seemingly finicky about when it will or won't run to remove something?

Take a look at the man pages for [FONT=Courier New]apt-get[FONT=Verdana] and [FONT=Courier New]aptitude[FONT=Verdana]:
```
man apt-get
``````
man aptitude
```If you have any questions after reading those, feel free to ask (man pages can be confusing sometimes).
[/FONT][/FONT][/FONT][/FONT]

---

### Post by charleswb on 2012-05-29
I'll check Wiki for Aptitude info.

As for Apt-Get, I just reread the Man Apt-Get page in terminal and have refined my thoughts/questions to this:[INDENT]I like apt-get autoremove because it uninstalls the app I want gone, AND it also uninstalls its dependencies. [COLOR=DarkRed]**However, autoremove does not remove the configuration file(s).**[/COLOR]

I like apt-get purge because it uninstalls the app I want gone, AND it deletes the config file(s) for that app,[COLOR=DarkRed]** but it does not remove the dependencies.**[/COLOR]
[/INDENT]I want the app gone, its dependencies gone, and its config file(s) gone.** [COLOR=Navy]Is there a command that does all that?[/COLOR]**

---

### Post by charleswb on 2012-05-29
Please refer to my prior post for context.

How about this?

sudo apt-get remove --auto-remove --purge appname

or this?

sudo apt-get remove --purge --auto-remove appname

Other?

How can I uninstall an app, its dependencies, and delete its config file? Is there a way to do that in one step, or in two steps?

The problem I'm seeing (or think I see) is that purge deletes the app and its config file(s), but leaves the dependency files; while autoremove deletes the app and its dependencies, but leaves the config file(s). So neither purge or autoremove are complete removal solutions. They each leave something on hard drive that I want gone. I tried running one, then the other, but the command line griped when trying to runt the second. It said nothing to uninstall, or something to that effect, because the main app was already gone from the first command.

---

### Post by Cheesemill on 2012-05-29
I always use aptitude instead of apt-get for this very reason (you may have to instll it first).
```
aptitude remove <packagename>
```
will remove a package and any unneeded dependencies.
```
aptitude purge <packagename>
```
will remove a package, it's configuration files and any unneeded dependencies.

---

### Post by Cheesehead on 2012-05-29
Cheesemill is right: apt-get won't delete multiple configs, so you'll need to use aptitude.

---

### Post by oldos2er on 2012-05-29
I don't really understand what you mean by 'apt-get autoremove' not running. If there's nothing for it to 'autoremove' it will just return to the command prompt without actually saying something like 'there's nothing for me to do!'

I used to use aptitude exclusively, because it seemed to be a little smarter than apt-get; plus it has apt-get's 'autoremove' function build in to its 'remove'. Unfortunately aptitude has problems with multiarch so I don't use it anymore.

---

### Post by mcduck on 2012-05-30
> **Cheesehead said:**
> Cheesemill is right: apt-get won't delete multiple configs, so you'll need to use aptitude.

rather, he's answer *was* right, years and years ago. :)

That's exactly what the purge and autoremove options for apt-get do. These days the only menaingfull difference between apt-get and aptitude is that aptitude has an optional ncurses-based interface if you want one. From functionality point of view, both do exactly the same things.

---

### Post by dniMretsaM on 2012-05-30
> **charleswb said:**
> I'll check Wiki for Aptitude info.

As for Apt-Get, I just reread the Man Apt-Get page in terminal and have refined my thoughts/questions to this:[INDENT]I like apt-get autoremove because it uninstalls the app I want gone, AND it also uninstalls its dependencies. [COLOR=DarkRed]**However, autoremove does not remove the configuration file(s).**[/COLOR]

I like apt-get purge because it uninstalls the app I want gone, AND it deletes the config file(s) for that app,[COLOR=DarkRed]** but it does not remove the dependencies.**[/COLOR]
[/INDENT]I want the app gone, its dependencies gone, and its config file(s) gone.** [COLOR=Navy]Is there a command that does all that?[/COLOR]**

 Yes there is: ```
sudo apt-get autoremove --purge pkgname
```  Happy removing! ):P

---

### Post by charleswb on 2012-05-31
> **oldos2er said:**
> I don't really understand what you mean by 'apt-get autoremove' not running. If there's nothing for it to 'autoremove' it will just return to the command prompt without actually saying something like 'there's nothing for me to do!'

I used to use aptitude exclusively, because it seemed to be a little smarter than apt-get; plus it has apt-get's 'autoremove' function build in to its 'remove'. Unfortunately aptitude has problems with multiarch so I don't use it anymore.

autoremove runs fine now. I must have mistyped something earlier.

---

### Post by charleswb on 2012-05-31
Based on my tests (installing and uninstalling brasero repeatedly) the following is [COLOR=Red]**what did NOT work**[/COLOR], and [COLOR=DarkGreen]**what did work**[/COLOR].

===

All 3 of the things that did **not** work seem like they should have, but they don't remove dependencies.

===

[COLOR=Red]**This did NOT work. **[/COLOR]It removed brasero and purges config files, but does NOT remove dependencies.

sudo apt-get purge --auto-remove brasero

===

[COLOR=Red]**This did NOT work.**[/COLOR] It removed brasero and purges config files, but does NOT remove dependencies.

sudo apt-get autoremove --purge brasero

===

[COLOR=Red]**This did NOT work.**[/COLOR] It removed brasero and purges config files, but does NOT remove dependencies.

sudo apt-get remove --purge --auto-remove brasero

===

[COLOR=DarkGreen]**Here are two things that did work. **[COLOR=Black]By work, I mean [/COLOR][/COLOR]removed the app, purged config file, and removed dependencies.

[COLOR=Navy]**The purge command must be run before autoremove, and the two must be run as separate commands.**[/COLOR] See below.

===

[COLOR=DarkGreen]**This did work.**[/COLOR] It removed the app file, its config file, and dependencies. This is two commands on one line, but it works and is typing efficient enough. So I'll call this [COLOR=DarkGreen][B]success.
[/B][/COLOR]
sudo apt-get purge brasero && sudo apt-get autoremove brasero

===

[COLOR=DarkGreen]**This did work.**[/COLOR] It removed the app file, its config file, and its dependencies; but is two separate commands on two lines.

sudo apt-get purge brasero

sudo apt-get autoremove brasero

---

### Post by Cheesemill on 2012-05-31
I think I know where you're getting confused. You need to run:
```
sudo apt-get autoremove
```as a single command, it doesn't take a package name or any other arguments. It just removes orphaned packages from your system. This is clearly stated in the command syntax in the man page:

```
apt-get [-sqdyfmubV] [-o= config_string ] [-c= config_file ] [-t= target_release] [-a= default_architecture] {update | upgrade | dselect-upgrade |
               dist-upgrade | install pkg [ { =pkg_version_number | /target_release } ] ...  | remove pkg...  | purge pkg...  |
               source pkg [ { =pkg_version_number | /target_release } ] ...  | build-dep pkg...  | check | clean | autoclean | autoremove | {-v | --version} |
               {-h | --help}}
```Notice how there is no pkg argument after the autoremove option, anything after autoremove is just ignored.

From your example above:
```
sudo apt-get purge brasero && sudo apt-get autoremove brasero
```should just be:
```
sudo apt-get purge brasero && sudo apt-get autoremove
```

This is why:
```
sudo apt-get autoremove brasero
```
by itself doesn't do what you are expecting.

---

### Post by cariboo on 2012-05-31
You can chain the two commands like this:

```
sudo apt-get purge brassero&&sudo apt-get autoremove
```

Never mind, the answer has already been given :-)

---

### Post by dniMretsaM on 2012-06-01
> **cariboo907 said:**
> You can chain the two commands like this:

```
sudo apt-get purge brassero && sudo apt-get autoremove
```Never mind, the answer has already been given :-)

Or if you want to want to purge the dependencies, add [FONT=Courier New]--purge[/FONT] to the end of the above command.

---

### Post by charleswb on 2012-06-03
I ran this:   sudo apt-get autoremove brasero
and it appeared to work dandy. So it appears to me that apt-get autoremove can take a package name argument. Am I missing something?

Just to be sure after reading above posts, I reinstalled brasero, and then again ran this:  sudo apt-get autoremove brasero

[COLOR=Navy]**Below is a copy/paste of my terminal window:**[/COLOR]

myloginname@mycomputername:~$ **sudo apt-get autoremove brasero**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brasero
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 618 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 304740 files and directories currently installed.)
Removing brasero ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
myloginname@mycomputername:~$

**That ^ looks like it worked to me. How did that not work?**

I have also run:  sudo apt-get purge brasero && sudo apt-get autoremove brasero and that also worked, but with the addition of it also removed brasero config file.

---

### Post by charleswb on 2012-06-03
I have also run this (on my host Ubuntu computer and several guest Ubuntu computers both U11.04 and U12.04) and it worked beautifully as far as I can tell. Am I missing something?

Here is what I ran to remove all apps (and their config files and dependencies) that I don't want and to install a couple things I do want, all from one single copy/paste into a terminal window.

sudo apt-get purge computer-janitor-gtk gnome-mahjongg aisleriot gnomine gnome-sudoku brasero && sudo apt-get autoremove computer-janitor-gtk gnome-mahjongg aisleriot gnomine gnome-sudoku brasero && sudo apt-get install ubuntu-restricted-extras xfburn

So now I don't need Ubuntu Super OS anymore. I just install regular Ubuntu 11.04 or 12.04 (I like both) and then get the apps how I want real quick from terminal by copy/pasting that code into terminal.

Then, if U12.04 run this:   sudo apt-get install gnome-panel

Wammo, a bunch of stuff done faster than I could ever do using GUI. It's worked several times for me on several virtual computers now, and two physical computers. Am I missing something?

---


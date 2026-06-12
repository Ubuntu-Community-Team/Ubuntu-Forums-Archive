---
title: "What is the better update command between this two?"
date: 2010-04-15
forum: General Help
---

### Post by aviramof on 2010-04-15
```
sudo apt-get update && sudo apt-get upgrade
``````
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude dist-upgrade
```thanks in advance.

---

### Post by aviramof on 2010-04-15
it's a simple question nobody knows?

---

### Post by Drenriza on 2010-04-15
> **aviramof said:**
> ```
sudo apt-get update && sudo apt-get upgrade
``````
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude dist-upgrade
```thanks in advance.

```
sudo apt-get update && sudo apt-get upgrade
```
will update your package information database to see if their is any new available packages. Then if the first command is executed with success it will then upgrade existing packages on the system to the newest version then install new available packages. And remove old packages that is no longer needed.

aptitude just gives you an front-end (graphical user-interface) to the apt-get command. 

So between these 2 I would not use aptitude.

---

### Post by aviramof on 2010-04-15
ok so is there an improvement i can do to the apt-get command or is it good as it is?

---

### Post by Drenriza on 2010-04-15
for updating & upgrading your system, the command cannot be improved.

---

### Post by aviramof on 2010-04-15
thank you very much any more opinions?

---

### Post by Wardje on 2010-04-15
aptitude is said to handle dependencies better. I myself still use apt-get cause I'm a slave to my habits, but the last time I had a problem with apt-get I simply used aptitude to resolve the issue.
So I'd say aptitude is better at its job.

---

### Post by neednewlaptop on 2010-04-15
I use aptitude because like Wardje said, aptitude handles dependencies better. But note that the graphical interface update manager still uses apt-get. When you update using aptitude and then check update manager the time you last updated is not correct, when using apt-get it does report something like: "was updated less then an hour ago".

---

### Post by aviramof on 2010-04-15
that sound like a bug to me that need to be fix after all if aptitude use apg-get it should report the last update time but any way i think i would check aptitude for some time and see if it's better as far as i see now he save me to use gksu --desktop /usr/share/applications/computer-janitor-gtk.desktop computer-janitor-gtk

---

### Post by nothingspecial on 2010-04-15
I remember reading, along time ago, that it is better not to mix aptitude and apt-get.

I can`t remember why, but for that reason, I only use apt.

---

### Post by mcduck on 2010-04-15
> **aviramof said:**
> that sound like a bug to me that need to be fix after all if aptitude use apg-get it should report the last update time but any way i think i would check aptitude for some time and see if it's better as far as i see now he save me to use gksu --desktop /usr/share/applications/computer-janitor-gtk.desktop computer-janitor-gtk

aptitude doesn't use apt-get.

Also the part about aptitude handling dependencies better than apt-get is pretty much history and hasn't been true for years now. (Some years ago the big difference between the two was that aptitude was able to uninstall packages that were installed as dependencies, while apt-get lacked that feature. These days you can use "apt-get autoremove" to do the same thing, so that difference is just history now.

Still, aptitude works in a bit different way when calculating the changes to be made. If it's better or not is a different thing (I stopped using aptitude when it couple of times tried to be way too smart and suggested doing things that would have broken my desktop, instead of just doing what I told it to do.) For most of the time which one you use is just a personal preference, at least if you don't need the ncurses-based interface aptitude has.

---

### Post by philinux on 2010-04-15
[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGet)

and

[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

Looking at aptitude man pages it does not use dist-upgrade.

Also synaptic uses apt-get however aptitude has its own GUI, try issuing the command aptitude in a terminal.

Personally I use synaptic and apt-get from command line.

Aptitude has a nice search function which I use occasionally.
```

aptitude search whatever
```

---

### Post by aviramof on 2010-04-15
i think aptitude is better in one thing when i used apt-get today i had this problem:
[http://ubuntuforums.org/showthread.php?t=1454910](http://ubuntuforums.org/showthread.php?t=1454910)

and it did not continued to install updates but aptitude did she just skipped the problem completely.

and it does use  dist-upgrade only now it's called full-upgrade
[https://help.ubuntu.com/community/AptitudeSurvivalGuide](https://help.ubuntu.com/community/AptitudeSurvivalGuide)

this is the updated command thanks to this manual and to [[COLOR=#d40000]**philinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=353083")

```
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude full-upgrade
```

---

### Post by snowpine on 2010-04-15
I personally use:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you are in doubt, just use the GUI Update Manager. :)

---

### Post by aviramof on 2010-04-15
the big problem with the GUI Update Manager that he constantly crash and even restarting it doesn't 
help only after using one of this commands he works again.

[https://bugs.launchpad.net/bugs/277902](https://bugs.launchpad.net/bugs/277902)

---

### Post by mcduck on 2010-04-15
> **aviramof said:**
> the big problem with the GUI Update Manager that he constantly crash and even restarting it doesn't 
help only after using one of this commands he works again.

[https://bugs.launchpad.net/bugs/277902](https://bugs.launchpad.net/bugs/277902)

Well, even the bug report tells you that it's not a bug in the Update Manager, it's a bug in specific language pack (language-support-ar) that's causing your problem...

---

### Post by Wardje on 2010-04-15
> **philinux said:**
> 
Aptitude has a nice search function which I use occasionally.
```

aptitude search whatever
```

```
apt-cache search whatever
```
does the same :)

---

### Post by aviramof on 2010-04-15
> **mcduck said:**
> Well, even the bug report tells you that it's not a bug in the Update Manager, it's a bug in specific language pack (language-support-ar) that's causing your problem...

yeah i read the first comment and yet the problem still exist after two years and five days!!!

["Nawaf  Alsallami]("https://launchpad.net/%7Enawaf")             wrote             on 2008-10-04"

sometime i think that ubuntu developers don't have a real sense of time!

---

### Post by philinux on 2010-04-16
> **Wardje said:**
> ```
apt-cache search whatever
```
does the same :)

Try both and see which you prefer ;)

---


---
title: "Grub, Firefox and X question"
date: 2006-02-22
forum: General Help
---

### Post by trommas on 2006-02-22
1.
First, My Grub seems to be adding every new kernel that is installed. The list is now extremly long, how do I delete posts?
Second, how do I uninstall GRUB,without interfering with my winxp install?
 
2.
My firefox is very very slow (compared to firefox in winxp). It uses over 5 seconds just to open a new tab, and even more when starting up. The pages are also slow to appear. 
 
3. I tried upgrading to Dapper flight 3, but when I rebootet, X fail to startup and the error message "X is not configured right" appears. I ran ubuntu breezy with nvidia drivers installed prior to the upgrade. Do I need to reinstall ubuntu, or is this fixable?

---

### Post by yanik on 2006-02-22
[I]1.
First, My Grub seems to be adding every new kernel that is installed. The list is now extremly long, how do I delete posts?
Second, how do I uninstall GRUB,without interfering with my winxp install?[/I]

You need to uninstall those kernel with synaptic

[I]2.
My firefox is very very slow (compared to firefox in winxp). It uses over 5 seconds just to open a new tab, and even more when starting up. The pages are also slow to appear.[/I]

What are your PC specs?  Comparing to WinXP it will always be slower.  You could try Epiphany, it's faster to startup and uses the same rendering engine as firefox.

*3. I tried upgrading to Dapper flight 3, but when I rebootet, X fail to startup and the error message "X is not configured right" appears. I ran ubuntu breezy with nvidia drivers installed prior to the upgrade. Do I need to reinstall ubuntu, or is this fixable?*

If you don't know your way with the comand line and config files, development releases aren't for you mate.

Yanik

---

### Post by Ramses de Norre on 2006-02-22
1) /boot/grub/menu.lst  and delete the entry's you don't want in there. You can also delete the old kernel images if you want, it are the vmlinuz files in /boot (only the old ones!). There are many how to's on setting back your mbr (something with fix mbr on the windows recovery prompt).

2) [give this a try]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4") ,  you can also find a lot of threads about this on the forum.

3) I wouldn't now..

EDIT: to late:) and uninstalling the kernels in synaptic may be safer.

---

### Post by nrwilk on 2006-02-22
For question 2)

Prelinking helped all the slow-loading apps on my system load more than twice as fast.  It's really noticeable.

Also, it's extremely easy.  Follow this howto:
[http://ubuntuforums.org/showthread.php?t=1971](http://ubuntuforums.org/showthread.php?t=1971)


For question 3)

Dapper is a development release, and isn't yet stable enough for a daily install (at least not for a casual user).  It's first stable release won't be for more than a month.  The first beta release is four weeks away.
I hate to say so, but it is too much hassle to downgrade from one version to the last.  You'd probably be better off reinstalling.  Don't worry, though.  This is common.  I've reinstalled maybe 20 times total.  Probably more, actually.

---

### Post by trommas on 2006-02-25
Wow!

Great answers, thanks :)

Now if only X would work instead of freezing up when i install ubuntu, everything would be wonderful :???:

---

### Post by nrwilk on 2006-02-27
Just to follow up, here is a sticky thread telling why not to use Dapper as your main OS, unless you want to bugtest it.
[http://ubuntuforums.org/showthread.php?t=93157](http://ubuntuforums.org/showthread.php?t=93157)

Here is the accompanying discussion thread which details more why not to use it.
Titled, "Don't use Dapper as your primary desktop OS."
[http://www.ubuntuforums.org/showthread.php?t=90743](http://www.ubuntuforums.org/showthread.php?t=90743)

Just in case you wanted some more info on it.  ;) :)

---

### Post by nanotube on 2006-02-27
about firefox speed - the default version on breezy, 1.0.7, is indeed really slow. but if you upgrade to 1.5 it is much faster. (link here: [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) )

i would not agree that it is slower on ubuntu than on winxp no matter what - ff1.5 is as responsive on ubuntu as it is on win, for me.

---


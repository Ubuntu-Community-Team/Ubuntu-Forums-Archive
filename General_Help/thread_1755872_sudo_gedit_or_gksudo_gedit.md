---
title: "sudo gedit or gksudo gedit"
date: 2011-05-11
forum: General Help
---

### Post by ianc1 on 2011-05-11
Real simple one here.

On the terminal if I want to edit a file owned by root with gedit should I use "sudo gedit" or "gksudo gedit"?

From [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) it says that gksudo is the graphical sudo.  Does this mean for launching graphical programs eg gedit as opposed to nano or when used in the desktop as in on launching apps by using Alt+F2?

On the subject of gedit I get the following warning when launching gedit from the terminal with "gksudo gedit" since upgrading to 11.04.```
(gedit:5400): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
ocal/share/recently-used.xbel.L5H2UV': No such file or directory
```I get two copies if I use "sudo gedit"

Thanks in advance for your time and effort.

---

### Post by mc4man on 2011-05-11
> **ianc1 said:**
> Real simple one here.


On the subject of gedit I get the following warning when launching gedit from the terminal with "gksudo gedit" since upgrading to 11.04.```
(gedit:5400): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
ocal/share/recently-used.xbel.L5H2UV': No such file or directory
```I 

Thanks in advance for your time and effort.
Use gksudo

As far as the warning - no big deal. It's simply saying  it can't create that file which is used to have a short history under gedit's File tab

If you wish so, then you'd need to create those 2 dir.'s in /root/[COLOR="Blue"].local/share/[/COLOR] ( I believe they don't exist by default

Or - just delete (move to trash) anything as root - the dir.'s will be automatically created - that's where the root trash is

---

### Post by ianc1 on 2011-05-11
Many thanks mc4man.  I shall use gksudo from now on.  To date I have used "sudo gedit" will this have caused any issues?  I am assuming not.

I shall continue to ignore the warning, I was just suprised as it suddenly appeared on moving to 11.04.

Many thanks for the prompt response.

---

### Post by mc4man on 2011-05-12
Just to add - 
I rarely use gksudo nautilus - there is the nautilus-gksu package which allows you to r. click on a dir. > Open as administrator

In the case of needing to open a root file browser earlier, then I  use the run dialog instead of a terminal
Alt+F2
Do try to refrain from using the root browser in your home dir., certainly don't add files that way.

---

### Post by jerome1232 on 2011-05-12
gksudo keeps graphical apps from taking ownership of config files in your own users home folder (which would cause undesired results when running said graphical app as your regular user)

---

### Post by ianc1 on 2011-05-13
Thanks mc4man that sounds like something I've been looking for.  The packages page [http://www.nongnu.org/gksu/](http://www.nongnu.org/gksu/) indicates its being replaced by policykit and Wikipedia, [https://secure.wikimedia.org/wikipedia/en/wiki/Gksu](https://secure.wikimedia.org/wikipedia/en/wiki/Gksu), warns of some security issues.  Although I suppose most programs have some security flaw unless I never go on the internet.  Should I use nautilus-gksu or policykit?

Sorry jerome1232 could you please explain:

> **jerome1232 said:**
> gksudo keeps graphical apps from taking ownership of config files in your own users home folder (which would cause undesired results when running said graphical app as your regular user)

Thanks guys.

---

### Post by lithopsian on 2011-05-13
sudo pretty much always works from a terminal.  From other locations (like alt-F2) it often won't work because there is nowhere to ask for a password.  Then you have to use gksudo.

Purists would probably tell you to use gksudo in other cases also, such as with gedit.  There are subtle differences to the permissions granted to sudo and gksudo, but nothing that should bother an average desktop user.

---

### Post by jerome1232 on 2011-05-13
Psychocats guide does a fairly good illustration of the difference. Better than I could ever explain it.


Give this a read [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---


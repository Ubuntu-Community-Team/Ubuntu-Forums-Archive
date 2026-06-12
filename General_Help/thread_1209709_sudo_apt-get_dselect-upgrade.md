---
title: "sudo apt-get dselect-upgrade"
date: 2009-07-10
forum: General Help
---

### Post by lorderico on 2009-07-10
What is the difference between:

```
sudo apt-get dselect-upgrade
```

and

```
sudo apt-get upgrade
```

?

Thanks,

Eric

---

### Post by phillw on 2009-07-10
[SIZE=2][FONT=Arial]Hi ...

[/FONT][/SIZE] 				 				**Re: HOWTO Reinstall all of your current packages if you do a fresh Ubuntu install** 			
 			 			 		   		 		 		According to section [6.4.9]("http://www.debian.org/doc/manuals/reference/ch-package.en.html#s-record") of the [Debian Reference Manual]("http://www.debian.org/doc/manuals/reference/"), the following will save both the list of packages installed and their debconf configuration:
 
 	Code:
 	     # dpkg --get-selections "*" >myselections   # or use \*
     # debconf-get-selections > debconfsel.txt 
and the following will reinstall and reconfigure them:

 	Code:
 	     # dselect update
     # debconf-set-selections < debconfsel.txt
     # dpkg --set-selections <myselections
     # apt-get -u dselect-upgrade    # or dselect install 

[SIZE=2][FONT=Arial]The whole of the ins and outs of it all are at 

[http://ubuntuforums.org/showthread.php?t=1057608&highlight=dselect-upgrade](http://ubuntuforums.org/showthread.php?t=1057608&highlight=dselect-upgrade)

It's one long, ongoing, article !!!

Hope it is of help.

Regards,

Phill.
[/FONT][/SIZE]

---

### Post by az on 2009-07-10
Upgrade will follow some basic logic to upgrade as many packages as it can without removing any.  

Dist-upgrade will allow for the removal of some packages to accommodate for some high-priority packages to install themselves and satisfy their dependencies/conflicts.  


For example, if you wanted to upgrade from one release to the next, changing your sources.list and running sudo apt-get upgrade will not be enough.  You probably won't end up with an upgraded system.  Running dist-upgrade will be more aggressive and try harder to get you there.

You can flag some packages for installation/removal.  Dselect is a curses package tool much like aptitude in it's interface.  It marks packages for installation.  Once you are done that, it runs dselect-upgrade and executes your package selections.

Packages can be marked for installation/remove with set-selections, as mentioned.  I think Tasksel also does that.

Anyway, dselect-upgrade is a fairly low-level way to manage packages.  Your better off using, well, anything else that is available to you (apt, add-install, Synaptic...)

---


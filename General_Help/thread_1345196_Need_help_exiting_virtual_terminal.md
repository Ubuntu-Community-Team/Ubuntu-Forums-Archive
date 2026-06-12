---
title: "Need help exiting virtual terminal"
date: 2009-12-03
forum: General Help
---

### Post by bedhead75 on 2009-12-03
Pressing Alt-Ctrl-F7 no longer exits any of the virtual terminals 1 through 6.  Now I have to log in with my username and password, and type "exit" in order to get back to gnome.  It worked fine before I reinstalled Ubuntu 9.04 while keeping my home folder intact.  What could have changed and how do I fix this?

---

### Post by greg963 on 2009-12-03
Well off topic those aren't virtual terminals, those are the real deal.

Quick history debian, on which ubuntu is based, allows for independent tty's on F1-F12 generally the tty number corresponds to the function key, ubuntu (and I expect debian lenny or whtever is current) reserves the tty's above 6 for starting X seesions.  This typically means X will run on tty7, but does not explicitly mean that this will happen.  So if X is running, and it is not running on tt7 try tty8-12 and you will likely find it.

Also you can find out where X is by doing this
```

greg@squizz:~$ ps -ef | grep X
root      1511  1464  3 Nov29 tty9     03:25:08 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
greg     17545 17520  0 20:16 pts/0    00:00:00 grep X
greg@squizz:~$ 

```

X is running on tty9

---

### Post by bedhead75 on 2009-12-03
I get this:

root      3237  3234  1 20:15 tty7     00:01:08 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
1000      7201  7183  0 21:22 pts/0    00:00:00 grep X


     I guess X is running on tty7, but I still can't switch back to it without actually logging in and exiting, which goes right to X rather than to the terminal prompt.  I also can't directly switch from one terminal to another without having to log in on one, exit back to X, and then Alt-Ctrl-Fn[1-6] into another.  

     It's not the biggest deal, but I'd like to understand why or how something like this would/could have changed with the same computer, same hardware.

---

### Post by greg963 on 2009-12-03
Well that sounds strange.. have you made any changes to your xorg.conf, or gdm settings recently?

---

### Post by bedhead75 on 2009-12-03
Not that I know of, but I am using the 190.42 Nvidia drivers.  I did come across this link about changing UseVBios from 1 to 0...

[http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/](http://meandubuntu.wordpress.com/2009/06/09/fixing-missing-virtual-terminal/)

...but that seems to be for a problem of not having any terminals show up in the first place.

---


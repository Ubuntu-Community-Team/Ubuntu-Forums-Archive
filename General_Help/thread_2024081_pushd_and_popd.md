---
title: "pushd and popd"
date: 2012-07-13
forum: General Help
---

### Post by wingnut2626 on 2012-07-13
[http://paste.linuxassist.net/216055](http://paste.linuxassist.net/216055)

Can someone give me the quick rundown on how this works?

---

### Post by Kevin McCready on 2013-03-14
link broken
I would love some help on this too. When I do
info pushd
man pushd
nothing comes up

---

### Post by r-senior on 2013-03-14
It's quite simple; pushd is like cd but it remembers where you were. popd takes you back.

So if you are in your home directory, you can "pushd Documents" and you will be in your ~/Documents directory. "popd" takes you back to your home directory. As you push and pop, the commands show you the directory you are in and the trail of directories you can go back to:

```
$ pushd Documents
~/Documents ~
$ popd
~

```

The reason you can't find a manual page is that it's a bash built-in command. You can find details using:

```
$ man bash
```

... or here: [https://www.gnu.org/software/bash/manual/bash.html#Directory-Stack-Builtins](https://www.gnu.org/software/bash/manual/bash.html#Directory-Stack-Builtins)

---

### Post by Kevin McCready on 2013-03-14
Thanks for that.
It might be easier for me to make my terminal always point at 

~/Documents
when I open the terminal. Because I now use that directory more than any other.
I guess I can do that somehow by
leafpad /home/$USER/.bashrc

Do you know what command I should put in?

---

### Post by r-senior on 2013-03-14
There are several ways, but the way I'd do it is to make a new .desktop file that will appear as an entry in the standard menu:

You mentioned leafpad, so I assume this is Lubuntu?

```

$ mkdir -p ~/.local/share/applications
$ cd ~/.local/share/applications
$ cp /usr/share/applications/lxterminal.desktop ./

```

Edit ~/.local/share/applications/lxterminal.desktop and append "--working-directory="/home/kevin/Documents" to the "Exec" line (which is near the bottom). This will make the LXTerminal entry in the "Start" menu open a terminal with the working directory set to your documents directory (assuming your username is "kevin" -- adjust accordingly).

If you have a shortcut in the panel, you'll need to remove this and re-add the replacement shortcut from the Accessories menu.

---

### Post by Kevin McCready on 2013-03-14
Thanks for that. Yes, Lubuntu
Will your suggestion work if I always start my terminal by
ctrl-alt-t
Alternatively, should I try to edit bash?

---

### Post by r-senior on 2013-03-14
I'm not sure. I tried it in a VM and Ctrl-Alt-T didn't do anything. If it doesn't work, just delete that file from ~/.local.share/applications and add this line to the bottom of ~/.bashrc

```
cd Documents
```

That will apply to all shells, not just those started from menu/panel shortcuts.

---

### Post by Kevin McCready on 2013-03-14
thanks
got it going now!

---


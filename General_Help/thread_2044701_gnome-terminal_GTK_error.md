---
title: "gnome-terminal GTK error"
date: 2012-08-19
forum: General Help
---

### Post by chellrose on 2012-08-19
Hi,

I just upgraded to Ubuntu 11.10.  I'm using the Trinity desktop, which of course comes with Konsole, but I prefer the gnome-terminal.

When I try to open gnome-terminal (from within another terminal), I see this error message:
```

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same p                                                                                                              rocess is not supported

[1]+  Trace/breakpoint trap   gnome-terminal

```

and gnome-terminal won't open.  What's the best way to fix this?

Thanks.

---

### Post by TheFu on 2012-08-19
I don't know how to fix it, but that error says you are mixing two different library versions inside the same program. This is bad.  I suspect that purging the gnome-terminal, then reinstalling it might help. Which earlier release did you upgrade from?  Did it have GTK+2.x and does the newer release have GTK+3.x?  Those libraries are in conflict.

---

### Post by chellrose on 2012-08-19
Sorry, I guess "upgraded" wasn't the correct term.  I did a clean install of 11.10 from a live cd (for some reason the old Trinity build I was using wouldn't allow me to upgrade directly.)  My old version was 10.10, though.

I used the standard Ubuntu live CD and then installed TDE from its repositories.

I tried purging and reinstalling gnome-terminal, but it's still having the same problem.  Looking at installed packages in Adept, I see that both libgtk-3-0 and libgtk-2.0-0 are installed.

Also, when I purged gnome-terminal, dpkg also removed ubuntu-desktop for some reason.  Is that bad?  The package description says "...it is recommended that it not be removed."
I never use Unity anyway, but was sort of hoping to keep it around for a while until I have everything up and working reasonably well in TDE...

Thanks!

---

### Post by TheFu on 2012-08-20
I don't know the answer, but suspect that until you have only 1 of the GTK+v2/3 packages installed, this will keep happening.  Unfortunately, I fear that the cure may be worse than the disease.  Removing either GTK+ package will likely remove many GUI tools and could lead to a system without any GUI at all.

I hate to suggest this, but perhaps punting now is a better idea, assuming TDE is that important to you.  
a) install 12.04 LTS Server - no GUI this way.  I try to only use LTS releases.
b) install TDE over that.
c) install Gnome-terminal over that.

Honestly, this is more work than I'd be willing to do just for a terminal. Personally, I use plain xterms and I spend 95% of my day in a terminal.  The only reason I use a GUI is to have more xterm windows. ;)

My daily desktop is an Ubuntu Server 12.04 with LXDE loaded.  For me, this keeps the Ubuntu-Gui bloat down.  My last desktop was an Ubuntu 10.04 Server with LXDE.    

Just an option for you to consider.

Sorry, no solution. I did google for an answer and the people who solved it appeared to be hard core devs.  They setup specific LD_LIBRARY_PATHs for each specific program using softlinks to the exact GTK+ lib desired.

---

### Post by chellrose on 2012-08-28
OK, thanks anyway.  I'll hunt around for another terminal option.

I'd like to get by with minimal GUI, but don't trust my geek skills quite that much yet :)

---


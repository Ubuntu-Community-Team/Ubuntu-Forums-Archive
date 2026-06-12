---
title: "How can I find the installed .deb program?"
date: 2011-12-23
forum: General Help
---

### Post by Kissell on 2011-12-23
So I have downloaded a packaged .deb file from a 3rd party...  installed it, but it didn't create a shortcut icon or tell me the command to launch it.  

I know it is installed, because if I double-click the .deb file again, it asks me if I would like to "reinstall" it. 

This has happened many times in my many years of using Ubuntu, and I was wondering if anyone knows a way to figure out the path where a .deb file installs it's files to.

The latest problem in question is a game called [Bit Trip Runner]("http://www.humblebundle.com/").

---

### Post by stinkeye on 2011-12-23
Have a look in /opt
**xfce4-appfinder** is also handy to search for apps.
Don't worry about the name...I use it with unity 11.10.
Hover over the app in xfce4-appfinder  and it will show you the command to launch.

---

### Post by Kissell on 2011-12-23
Thanks for playing, but strike two.

There isn't anything in /opt that I don't already know about, and the app finder just showed me my menus and the shortcuts already in them...  it didn't have any programs that the installation didn't create an icon for.

So basically, I am in the situation I always get into with something like this...  I give up and there is an orphaned program somewhere on my system until I reformat.  I guess this is what it would be like if Windows didn't have Program Files and didn't let you choose the path when you installed programs.  Been a computer nerd for decades and always took that for granted.

---

### Post by dcstar on 2011-12-23
> **Kissell said:**
> 
........
This has happened many times in my many years of using Ubuntu, and I was wondering if anyone knows a way to figure out the path where a .deb file installs it's files to.
.......

You simply look at the package Properties in Synaptic and see where the installed files are.

---

### Post by Kissell on 2011-12-23
Oh, that works...  I have rarely ever used the synaptic GUI...  I tend to use command line to install from repositories when possible, so I can script for OS installation or check for programs and install from repos if they are necessary but not installed when I run my other scripts.

Anyway, even though it wasn't in the repos, it shows up in synaptic because I installed the .deb...  so I found the executable, but unfortunately in this case, after running it I get an error: 
/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found

Maybe that error is why it didn't create a launcher.

---

### Post by drmrgd on 2011-12-23
Maybe I'm off on this, but can't you use something like dpkg -p or dpkg -S to search your system for the debian package information.  Running dpkg -S (that's a capital "S" by the way), gives me the locations of all of the components of a particular package on my system.  

Of course, if you know the exact name of the packages executable file,  you could use "which" to find it on the system.  But, I'm guessing that's not the case in this instance.

Anyway, looking at the specifics of dpkg, I wonder if you can find something that might help you.

---

### Post by Lars Noodén on 2011-12-23
You can find the list of files that the package installed using [dpkg -L](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html) followed by the name of the package.

e.g.

```

[s]dpkg --list apache2[/s]
dpkg --listfiles apache2

```

---

### Post by drmrgd on 2011-12-23
> **Lars Noodén said:**
> You can find the list of files that the package installed using [dpkg -L](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html) followed by the name of the package.

e.g.

```

dpkg --list apache2

```


Ahhhh...that's it!  I knew there was a dpkg option that would do it.  Thanks Lars!

---

### Post by stinkeye on 2011-12-23
> **Lars Noodén said:**
> You can find the list of files that the package installed using [dpkg -L](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html) followed by the name of the package.

e.g.

```

dpkg --list apache2

```
Hi Lars Noodén
That's handy, but just to let you know **dpkg --list** didn't work so I looked at the man page
and 
the long form of **dpkg -L** is ```
dpkg --listfiles
```

---

### Post by Lars Noodén on 2011-12-23
> **stinkeye said:**
> the long form of **dpkg -L** is ```
dpkg --listfiles
```
Thanks.  I fixed the typo.

---


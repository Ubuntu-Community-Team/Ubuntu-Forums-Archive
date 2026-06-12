---
title: "Insalling Opera in Ubuntu?"
date: 2010-01-22
forum: General Help
---

### Post by Pipps on 2010-01-22
I have attempted to install Opera by downloading the [Deb file]("http://www.opera.com/download/index.dml?platform=linux") and running:

```
sudo dpkg -i oopera_10.10.4742.gcc4.qt3_i386.deb
```

The installation appears to complete itself successfully. However, when I come to then clicking on the new Opera logo in the panel menu, nothing happens. Even after a restart.

What could I be doing wrong? How should I launch Opera? :confused:

---

### Post by Saiko Berry on 2010-01-22
Run it with terminal using opera & and paste the errors.

---

### Post by Pipps on 2010-01-22
I attempted to launch opera from the terminal by typing:

```
/usr/lib/opera/opera
```

On doing so, I received the following error message:

> /usr/lib/opera/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

Was my run-command correct?

What can this output mean? :confused:

---

### Post by Lars Noodén on 2010-01-22
> **Pipps said:**
> I attempted to launch opera from the terminal by typing:

```
/usr/lib/opera/opera
```

On doing so, I received the following error message:

> 
/usr/lib/opera/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


Was my run-command correct?

What can this output mean? :confused:

It looks like you may have installed the version of Opera with the dynamically linked libraries, but those libraries are missing.  dpkg should have caught that and complained.  

You can search for the package containing [libqt-mt.so.3](http://packages.ubuntu.com/search?searchon=contents&keywords=libqt-mt.so.3&mode=exactfilename&suite=karmic&arch=any) and add it.  Then run again and keep adding any packages that are still missing.

Or you can download the larger, statically linked version of Opera.  

Or you can try adding [Opera's Repository](http://deb.opera.com/) to your list of APT sources.  Then install Opera from the repository like you would any other Ubuntu program.  Using a repository is the option I would recommend strongly over the other choices.

---

### Post by Pipps on 2010-01-22
Thank you for the detailed advice.

I would definitely like to try the repository option.

How should I uninstall and remove the current version of Opera, first?

Would there be a recommended terminal command?

---

### Post by Lars Noodén on 2010-01-22
> **Pipps said:**
> 
How should I uninstall and remove the current version of Opera, first?


Something like this:

sudo dpkg -r ____


You can find what to fill in for ___ in this way:

dpkg -l | grep opera

---

### Post by Pipps on 2010-01-22
Thank you for the advice.

The command:
```
dpkg -l | grep opera
```

Returns the following:

> ii  eject                                 2.1.5+deb1+cvs20081104-6                   ejects CDs and operates CD-Changers under Li
iU  opera                                 10.10.4742.gcc4.qt3                        The Opera Web Browser


So should the remove command be:
> sudo dpkg -r 2.1.5+deb1+cvs20081104-6

I ask, as that doesn't seem right, somehow... :confused:

---

### Post by Leppie on 2010-01-22
> **Pipps said:**
> The command:
```
dpkg -l | grep opera
```Returns the following:
> ii eject 2.1.5+deb1+cvs20081104-6 [COLOR=Red]_**ejects CDs and operates CD-Changers under Li**_[/COLOR]
[COLOR=Black]iU  opera                                 10.10.4742.gcc4.qt3                        The Opera Web Browser                      [/COLOR]So should the remove command be:
[QUOTE]sudo dpkg -r 2.1.5+deb1+cvs20081104-6                      I ask, as that doesn't seem right, somehow... :confused:[/QUOTE]
have you read the descriptions that come after the package names?

---

### Post by sisco311 on 2010-01-22
> **Pipps said:**
> Thank you for the detailed advice.

I would definitely like to try the repository option.

How should I uninstall and remove the current version of Opera, first?

Would there be a recommended terminal command?

Double click the .deb file, the package manager will download and install the dependencies. The opera .deb installer adds the opera repositories to your repo list, you don't have to worry about it ;).

If you want to install it from a terminal :), then run:
```
sudo gdebi opera*.deb
```

---

### Post by Pipps on 2010-01-22
> **sisco311 said:**
> Double click the .deb file, the package manager will download and install the dependencies. The opera .deb installer adds the opera repositories to your repo list, you don't have to worry about it ;). ...
Wow! That worked perfectly!

The easiest solutions are sometimes the best!

Thank you!

---


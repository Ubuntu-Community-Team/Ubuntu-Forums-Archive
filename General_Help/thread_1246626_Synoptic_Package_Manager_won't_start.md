---
title: "Synoptic Package Manager won't start"
date: 2009-08-21
forum: General Help
---

### Post by jbeukema on 2009-08-21
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


As I just started using Ubuntu today, I am now lost...

What do I do now?

---

### Post by dcstar on 2009-08-21
> **jbeukema said:**
> As I just started using Ubuntu today, I am now lost...

What do I do now?

Applications-Accessories-Terminal, and type this in:

```
sudo dpkg --configure -a
```

---

### Post by jbeukema on 2009-08-22
> **dcstar said:**
> Applications-Accessories-Terminal, and type this in:

```
sudo dpkg --configure -a
```

That did the trick :)

No, what did we actually do and will I use these commands often?

is there a tutorial on Ubuntu's command line somewhere?

---

### Post by 3rdalbum on 2009-08-22
> **jbeukema said:**
> That did the trick :)

No, what did we actually do and will I use these commands often?

Well, the package manager had been interrupted while installing packages. Your question about "what's this error message" is very common, which makes me think that Linux newbies close the Synaptic window prematurely.

The command you put in just tells the package manager to resume installing from where it left off.

Also, when people are installing Java on the command-line, they get a text-based license agreement screen where they have to push Tab to highlight the "I Agree" button. If they don't know that, they might close the window and leave the package manager in an inconsistent state. That's why I ALWAYS recommend that people install Java from Synaptic Package Manager, because it brings up the license agreement in a nice, friendly GUI screen.

> is there a tutorial on Ubuntu's command line somewhere?

[www.linuxcommand.org](www.linuxcommand.org) is a good one for general command-line use on Linux. It doesn't go into Ubuntu-specific commands and it doesn't go much into the various options you can use with command-line programs.

There's an on-demand manual system called "man". If you need help with a command, just type "man" and the command name. For instance:

```
man apt-get
man grep
man chmod
```

---

### Post by jbeukema on 2009-08-22
Danke! ^.^

---


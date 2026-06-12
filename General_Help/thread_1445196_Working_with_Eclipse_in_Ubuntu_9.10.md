---
title: "Working with Eclipse in Ubuntu 9.10"
date: 2010-04-02
forum: General Help
---

### Post by caseywise on 2010-04-02
Hi guys, after trial and error, got Java working and Eclipse nearly 100% behaving.  I'm using the Gnome desktop, I have 2 issues, I'm hoping someone has seen this stuff.

1. Eclipse has to be run as root.  I'd like open Eclipse from the panel launcher button.  Right now I have "/home/user1/Downloads/eclipse/eclipse" in the "Command" field when I right click > properties on my Eclipse button.  Anyone know what I can put in the "Command" field to launch Eclipse as root user?

2. In Eclipse, I'm experiencing unexpected results when I mouse click on certain buttons.  For example I want to create a new project.  File > New Java Project.  I enter "test" as the project name, when I click the "Next" button with my mouse, nothing happens.  The "N" is underlined and I'm able to proceed to the next step with ALT+N on the keyboard.  I was wondering if anyone had encountered the same problem?  I'd like if clicking on that "Next" button with my mouse would work.  Any ideas?

Thanks for looking,
Casey Wise

---

### Post by km0r3 on 2010-04-02
> **caseywise said:**
> Hi guys, after trial and error, got Java working and Eclipse nearly 100% behaving.  I'm using the Gnome desktop, I have 2 issues, I'm hoping someone has seen this stuff.

1. Eclipse has to be run as root.  I'd like open Eclipse from the panel launcher button.  Right now I have "/home/user1/Downloads/eclipse/eclipse" in the "Command" field when I right click > properties on my Eclipse button.  Anyone know what I can put in the "Command" field to launch Eclipse as root user?

2. In Eclipse, I'm experiencing unexpected results when I mouse click on certain buttons.  For example I want to create a new project.  File > New Java Project.  I enter "test" as the project name, when I click the "Next" button with my mouse, nothing happens.  The "N" is underlined and I'm able to proceed to the next step with ALT+N on the keyboard.  I was wondering if anyone had encountered the same problem?  I'd like if clicking on that "Next" button with my mouse would work.  Any ideas?

Thanks for looking,
Casey Wise

Sorry for bothering but why do you run Eclipse as root?
Have you compiled Eclipse from source or installed it via *apt-get*?

_To your questions:_

1. Make your ""Comand" Line" look like this:

```
gksu /home/user1/Downloads/eclipse/eclipse
```

2. Sounds like a bug. Are you using the latest version?

---

### Post by caseywise on 2010-04-02
Hi km0r3, thanks for your quick response!

We're running a CMS, when we svn it down, they tell us to do so as root user, therefore it installs as root.  Running Eclipse as root is the only way to make it work then without throwing all sorts of permission errors.

As far as the Java goes with the button not depressing, I tried many different ways of getting it on here, I ultimately ended up installing Sun's.

root@sinister:/home/cmwise# java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)

---


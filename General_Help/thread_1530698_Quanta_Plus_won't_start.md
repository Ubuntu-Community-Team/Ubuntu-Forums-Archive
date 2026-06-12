---
title: "Quanta Plus won't start"
date: 2010-07-14
forum: General Help
---

### Post by max-power2717 on 2010-07-14
Hi Forum,

I realise this is probably a Quanta or KDE problem rather than a Ubuntu one, but any insight would be appreciated. 

I run Ubuntu Jaunty with gnome. I've become quite accustomed to using Quanta for editing website files (.css, .php, .html) etc. This is a KDE application so when I installed it, the software manager installed the KDE stuff to enable it to run. Today I switched the view of the quanta interface to "top level" from the window menu. Everything was working fine until I attempted to open a documenation window - then Quanta had some sort of error so I quit the application and tried to start it again - and it won't start. 

I've restarted my computer to see if that would help, quanta still won't start when chosen from the Ubuntu Applications menu - no error message, nada.

When I try to start from terminal I get this:
```
max@thorbuntu:~$ quanta
kbuildsycoca running...
QObject::connect: Cannot connect (null)::initiateDrag(QWidget *) to QuantaApp::slotTabDragged(QWidget*)
KCrash: Application 'quanta' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
max@thorbuntu:~$ 
```I've been searching google, ubuntuforums and also quanta.kdewebdev.org for some a solution but to no avail so far. I don't even know where to begin with regards troubleshooting this problem locally.

Can anyone suggest anything? I'm grasping at straws here - and I've already spent a solid hour trying to get find a solution. Any input will be greatly appreciated. 

Thanks.

---

### Post by max-power2717 on 2010-07-14
Ok, 

I found my own solution. 

```
max@thorbuntu:/etc$ quanta --help
Usage: quanta [Qt-options] [KDE-options] [File] 

Quanta Plus Web Development Environment

Generic options:
  --help                    Show help about options
  --help-qt                 Show Qt specific options
  --help-kde                Show KDE specific options
  --help-all                Show all options
  --author                  Show author information
  -v, --version             Show version information
  --license                 Show license information
  --                        End of options

Arguments:
  File                      File to open

Options:
  --unique                  Whether we start as a one-instance application
  --nologo                  Do not show the nice logo during startup
  --resetlayout             Reset the layout of the user interface to the default
max@thorbuntu:/etc$ quanta --resetlayout
kbuildsycoca running...
DCOP Cleaning up dead connections.

```

Simply using the --resetlayout option to start quanta fixed whatever problem was preventing quanta application from starting up and I got the default interface for quanta. 

Will have to keep that in mind next time I want to experiment with the 'Top Level' interface.

Cheers,
Max.

---

### Post by amptech on 2010-09-20
Brand new to Quanta. Opened it once, made a few tweaks and locked it out. This solved my problem. 

Many thanks!

---

### Post by complience on 2011-02-28
Many thanks had the exact same problem, even after a complete reinstall.

What caused it was I changed the MDI mode to 'Top Level' 

definitely a few bugs still about

---

### Post by sanketg86 on 2011-07-01
resolve my problem, thank you so much :):D

---


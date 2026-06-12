---
title: "KDE/Qt command line clutter"
date: 2011-09-27
forum: General Help
---

### Post by sloom22 on 2011-09-27
Hi guys,

I do a lot of my work from the command line, and have to run various Qt and KDE applications.  Invariably, running these applications results in a large number of errors and warnings which are sent to the command line. For example, when I open one KDE application and play around with the menus and stuff a bit and then close the application, it outputs the following:

```
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
QLayout::addChildLayout: layout already has a parent
Weaver dtor: destroying inventory.
WeaverThreadLogger: thread (ID: 1) destroyed.
WeaverThreadLogger: thread (ID: 2) destroyed.
WeaverThreadLogger: thread (ID: 3) destroyed.
WeaverThreadLogger: thread (ID: 4) destroyed.
Weaver dtor: done
```

And for a different application:

```
QObject::disconnect: Unexpected null parameter
QFile::open: No file name specified
```

And another:

```
kbuildsycoca running...
KNotify::playTimeout
konqueror: WARNING: KonqFactory::createView : no factory
KNotify::playTimeout
```

The majority of the messages are not even errors - why do I need to know that kbuildsycoca is running? GTK/Gnome applications for example do not have this problem - they only display actual errors, which are rare to nonexistent depending on the program.

Since I also run other programs which send output to the command line, these messages are very annoying and disruptive.

Is there any way of turning them off?

Thanks!

---

### Post by sumski on 2011-09-27
you can try reducing number of messages with kdebugdialog

---

### Post by aeiah on 2011-09-27
well to make sure nothing gets displayed, you'd pipe standard output and standard error to /dev/null
```

program > /dev/null 2>&1
```

if you don't want to pipe stderr (number 2) to the same place as stdout (number 1), then this should suffice, id say:

```

program > /dev/null
```

although maybe a lot of the annoying messages are stderr messages, in which case you'll have to see all or nothing.

---

### Post by sloom22 on 2011-10-02
Problem solved using kdebugdialog. Thanks sumski!

Warning: the kdebugdialog program is hard to use, and (possibly related) you do not see results from it until after restarting KDE.

---


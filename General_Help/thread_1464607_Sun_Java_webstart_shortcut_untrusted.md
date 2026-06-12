---
title: "Sun Java webstart shortcut untrusted"
date: 2010-04-28
forum: General Help
---

### Post by haihovu on 2010-04-28
I created a number of Java webstart applications that place shortcuts on the users' desktop upon installation, i.e. the following fragment is in the JNLP files:

    <shortcut online="true">
      <desktop/>
    </shortcut>

This works fine for Windows, and various flavours of Linux including older Ubuntu distros (pre 8.10), running Gnome desktop. Starting around 8.10, the shortcuts that Sun Java webstart placed on the desktop were marked as untrusted, which upon access gave the users the option of 'Mark as trusted'. While this is clunky the work around is palatable. This behaviour, however, changed with 10.04, the Java webstart shortcuts are still marked as untrusted, but the users are no longer given the option to mark these shortcuts as trusted. A quick peek revealed that the shortcuts, even though owned by the users, do not have the executable bit turned on in the permission property  (this is true on other Linux distros such as CentOS as well, but they work fine), and I had to do this manually, at the command line: chmod u+x <shortcut>, in order to make the shortcuts usable. This is quite tedious for the end users, and I am wondering if there is a better way to address the matter?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
I would file a bug report but you could write a script and hand it out to users as needed.

---

### Post by haihovu on 2010-04-28
Apparently this is a Gnome (well actually Freedesktop.org) 'feature' as alluded to here: [http://www.algorithm-forge.com/techblog/2009/07/executable-application-launcher/](http://www.algorithm-forge.com/techblog/2009/07/executable-application-launcher/) though I have not encountered it in other platforms such as CentOS/RHEL 5, Solaris 10, ...

I want to make it easy for my users to use my apps with as much automation in the deployment as possible giving minimal hassle, but this is going to throw a big wrench into my plan. If I were to raise a bug report who would I raise it against, Sun Java or Ubuntu?

---

### Post by Flimm on 2010-04-29
I think this is a bug with Java's Web Start technology, it should have set the executable bit. I agree, it is quite annoying.

---

### Post by Smigh on 2010-11-16
This bug is reported in Oracle: [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6957030](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6957030)

If your app has permissions on the client's filesystem you can easily set the executable bit from inside Java when the application first runs.

---


---
title: "Problem with alien converting RPM with %defattr in spec and maintaining permissions"
date: 2010-11-10
forum: General Help
---

### Post by ChazzMichaelMichaels on 2010-11-10
Hey everyone,

Just joined the group to post this question as I can't find a good answer for it.

I have an RPM that has the following in the spec:

%defattr(-,someuser,someuser)
            /opt/myapplication

When I go to install the RPM, the file permissions for everything in /opt/myapplication are set to root:root.  This RPM installs properly in RPM based distros and maintains the correct permissions. 

When I run alien -i --scripts --veryverbose myapplication.rpm as root, I can see it chmod'ing everything to 755.

Has anyone else had this problem?  I tried --fixperms as well and that did nothing.

Thanks!

---

### Post by ChazzMichaelMichaels on 2010-12-15
Resurrecting this thread from the dead.

I'm working on a new image for my employer (64 bit) and I'd like to see if I can figure out if this is resolvable.

---


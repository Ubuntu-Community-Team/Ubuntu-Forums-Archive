---
title: "Problem with remote files in java-based editors"
date: 2009-12-02
forum: General Help
---

### Post by ManiacDan on 2009-12-02
Here's an odd problem that might be Java's fault, but might be the OS:  I use Zend and Eclipse PDT at work to edit PHP files.  These files (per company policy) reside on another server.  Saving a file in either Zend or PDT will sometimes (usually) cause that file to become "desynchronized."  The editor window will go blank, and prompt me to reload the file from the filesystem.  This is the behavior the editor exhibits whenever someone changes an open file while it is open in the editor.  For instance, if I open foo.php in the editor, then go and change foo.php in vi, the editor will blank and prompt me to reload.

This issue ONLY affects the two editors I've mentioned: Eclipse PDT and Zend (powered by Eclipse).  Unfortunately they're BOTH Eclipse-based, but they're the only editors with sufficient capabilities to allow me to work in this enormous coding environment.

For a while I attempted to simply use gedit, and that did NOT exhibit the problems accessing files that I've seen on the Java-based software, but I haven't been able to find any bug reports similar to mine.  

I also suspected it may be a problem with the system time of the file being in the future whenever it was saved, so I monkeyed with the local time settings a few minutes in either direction, that didn't help.

Any thoughts?

Thanks,
Dan

---


---
title: "Decrippling Evince?"
date: 2006-02-05
forum: General Help
---

### Post by fubarbundy on 2006-02-05
EDIT: I've answered my own question! See below

I don't know how many people know this, but Ubuntu ships with a crippled version of Evince by default that implements OPTIONAL PDF copy restriction flags present in some PDF documents.

1. This is not legally required. It is up to the software author whether or not to implement this part of the spec.

2. I believe Evince comes with a configure flag to disable this "feature".

3. It's retarded. Although for instance you can't use edit-copy/ctrl-c, highlight and middle click paste STILL WORKS! Holy pointless batman.

So, question is, does anyone know what the relevant flag is?

For anyone wanting to test this, try this PDF from our good friends at Intel:

[http://www.intel.com/pressroom/kits/events/ces2006/Transcript_PSO%20keynote_CES2006.pdf](http://www.intel.com/pressroom/kits/events/ces2006/Transcript_PSO%20keynote_CES2006.pdf)

---

### Post by fubarbundy on 2006-02-05
If anyone is interested, there's a bug report here:

[http://bugzilla.gnome.org/show_bug.cgi?id=305818](http://bugzilla.gnome.org/show_bug.cgi?id=305818)

and from the bug report, a patch in CVS to add a GConf key to override permissions, here:

[http://bugzilla.gnome.org/attachment.cgi?id=49224&action=view](http://bugzilla.gnome.org/attachment.cgi?id=49224&action=view)

---

### Post by fubarbundy on 2006-02-05
Here are patched copies of the two files from the Ubuntu sources that will give you the option of overriding restrictions in PDF's. If anyone needs further instructions on how to install a patched Evince, let me know.

---

### Post by stoffe on 2006-02-05
Sure hope it will ship with this "feature" disabled in the future. Even though I could do the toggle myself, I don't like being restricted.

---


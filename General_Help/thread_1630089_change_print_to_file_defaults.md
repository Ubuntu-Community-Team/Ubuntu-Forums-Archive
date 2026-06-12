---
title: "change print to file defaults"
date: 2010-11-24
forum: General Help
---

### Post by aeronutt on 2010-11-24
In 10.04LTS, when selecting print to file, the default settings are .ps, and home directory. Can those defaults be changed? I've looked around in CUPS, ubuntu-tweak, and searched on here, to no avail.

---

### Post by aeronutt on 2010-11-25
Anyone?

---

### Post by efflandt on 2010-11-25
What file format were you looking for?

If you want something that will make pdf files instead, install cups-pdf.  Anything you print using that as a printer will create a pdf file in ~/PDF/ (it will create that dir if it does not exist).

---

### Post by aeronutt on 2010-11-25
Thanks for the reply. I can already create PDF's, I'd just like to change the default file type to pdf (not .ps) and the default directory to something other than home (in the gui that pops up when I want to print).

---

### Post by nickpj on 2010-12-02
I'd like the same thing - default to PDFs rather than PS when using "print to file". Yes it's only one click, but it's a nice touch. PDF is certainly far more familiar and useful to most users now that postscript. Is it worth logging this as a trivial-grade enhancement request upstream? If so, is it a gnome thing or a cups thing, or what?

---

### Post by ndstate on 2011-01-28
I am also looking for how to do this.  Has anyone been able to figure it out?

---


---
title: "Gedit plugin to collapse blocks"
date: 2009-10-10
forum: General Help
---

### Post by J V on 2009-10-10
I'm looking for a gedit plugin to collapse blocks of code/text, anyone know of one? (Like with little +/- icons near the line numbers)

---

### Post by J V on 2009-10-11
Nowhere? Aww cmon, last thing I need is to have to run notepad++ in wine...

---

### Post by mcduck on 2009-10-11
No, there isn't one. It's often requested feature, but would require major changes to the GtkSourceView library that Gedit uses to show the source code. Collapsing code blocks would of course require the program to actually recognize blocks from the code. At least currently GtkSourceView doesn't do that.

---

### Post by J V on 2009-10-11
Well blocks of code are usually things between { and } or in the case of python, indented...

Recognizing the code blocks isn't that hard, its the collapsing that's difficult, the entry would need to display horizontal lines on collapsed code blocks...

It is definitley a high-ish profile feature, if the library would need major changes I think it should get it, I've never seen an advanced text editor without this feature...

[SOLVED]

---

### Post by mcduck on 2009-10-11
No, it definitely isn't that simple. At least when you consider the amount of different code syntaxes Gedit/GtkSourceView supports.. Some languages would be as simple as what you suggested, but for many others it sure is a lot harder than that.

---

### Post by CyruzDraxs on 2009-12-11
Could you not just do selection collapsing? It'd be more flexible that way and it'd be completely separate from that.

---

### Post by VCoolio on 2009-12-11
This one works:
[http://code.google.com/p/gedit-folding/downloads/list](http://code.google.com/p/gedit-folding/downloads/list)

---

### Post by trusktr on 2012-10-02
> **VCoolio said:**
> This one works:
[http://code.google.com/p/gedit-folding/downloads/list](http://code.google.com/p/gedit-folding/downloads/list)

We need to update the above folding plugin for Gedit 3. I'll post it up if I get to it.

---


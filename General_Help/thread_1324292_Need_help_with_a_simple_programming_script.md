---
title: "Need help with a simple programming script"
date: 2009-11-12
forum: General Help
---

### Post by Raizor on 2009-11-12
I have an application that I run that requires user input at regular intervals and I would like to automate the input (as it's quite repetitive) but I have absolutely no idea on how to do this.

The application generates a window in GDM and what I would like to do is send specific, timed input into that window from a script of via the command line in the background.  This would allow me to multitask appropriately without having to do these repetative tasks.

Example:  I need to hit a / key, once every 10 seconds, followed by a space key, followed by a repeat / key.

Any ideas on where to start or to how to get this done?  I'm not new to Ubuntu but am new to scripting for the ubuntu GDM interface.

(I also apologize for putting this in the wrong location in the forums, if I have in fact selected the area incorrectly)

---

### Post by Giblet5 on 2009-11-12
I use the python-dogtail package (available in Synaptic), and have read good things about ldtp (also in Synaptic).

These are test-automation frameworks that allow you to automate the testing of gui interfaces.

That sounds like it might be what you want.


It's easy to automate text-based applications that read stdin and output to stdout. It's a bit more complicated to automate gui interfaces...

---


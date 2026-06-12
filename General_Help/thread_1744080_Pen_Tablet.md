---
title: "Pen Tablet"
date: 2011-04-30
forum: General Help
---

### Post by Julian Luna on 2011-04-30
Damn! Me again and my tablet :(
Upgraded to 11.04 and my graphical tablet is recognized no longer
Any idea how can I set it up? Wizardpen is not working, the ppa on my repository says something about "Natty" instead of "Maverick" (As than before)
Sorry for my lame english and hope this topic helps a lot of more persons that are having the same or alike problem

If I type lsusb on my terminal then this line appears:

```
Bus 003 Device 002: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
```Which is completely false because the Genius MousePen 5x4 Tablet is this one[IMG]http://www.dsystem.com.br/loja/images/Image2/DSYSgeniusmousepen5x4.gif[/IMG]
And I have the Genius Easypen i405, which is this one
[[IMG]http://www.testseek.com/labs/wp-content/uploads/2009/08/easypen-i405_upclose-by-genius-300x251.jpg[/IMG]]("http://www.testseek.com/labs/wp-content/uploads/2009/08/easypen-i405_upclose-by-genius-300x251.jpg")

Any idea how can I set it up?

---

### Post by Julian Luna on 2011-05-02
Bump ._.

---

### Post by Favux on 2011-05-02
Hi Julian,

The WizardPen driver doesn't seem to be in the Natty repository anymore so it may have been dropped.  You'd have to do some research to find out why.

Maybe there's a new driver a UC-LOGIC tablet is suppose to use?

So unless and until DoctorMO updates his WizardPen PPA for Natty you may be stuck.

You could try placing your tablet on the Aiptek or Wacom driver I suppose.  Right now it is probably falling through to the evdev driver.  Which from what you are saying doesn't work for the tablet.

And I'd assume what the lsusb is showing is that the internals (the digitizer) of the two tablets is identical as far as the kernel is concerned.

---

### Post by YAFU on 2011-05-02
Hello.
See the following links:
[https://answers.launchpad.net/wizardpen/+question/153998](https://answers.launchpad.net/wizardpen/+question/153998)
[https://bugs.launchpad.net/wizardpen/+bug/715904](https://bugs.launchpad.net/wizardpen/+bug/715904)
How to (in spanish):
[http://www.kubuntu-es.org/foro/201105/instalar-driver-wizardpen-tabletas-graficas-genius-natty-narwhal-1104](http://www.kubuntu-es.org/foro/201105/instalar-driver-wizardpen-tabletas-graficas-genius-natty-narwhal-1104)

Greetings.

PS: I also have the tablet EasyPen i405, but "lsusb" still showing as UC-Logic Technology Corp. Genius MousePen 5x4 Tablet.
But at least now it works.

---

### Post by YAFU on 2011-05-03
Ok, it does not matter.
The WizardPen driver for Natty Narwhal - 11.04 soon be available in the PPA:
[https://launchpad.net/~doctormo/+archive/xorg-wizardpen](https://launchpad.net/~doctormo/+archive/xorg-wizardpen)

Thanks to "mnemoc" and "Martin Owens":
[https://bugs.launchpad.net/wizardpen/+bug/715904](https://bugs.launchpad.net/wizardpen/+bug/715904)

---


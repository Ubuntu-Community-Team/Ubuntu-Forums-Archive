---
title: "jvm problem"
date: 2006-03-15
forum: General Help
---

### Post by mach5 on 2006-03-15
i have jdk1.5 installed, but still it uses the gnu jvm.. 
what changes are to be done, so that i will be able to use the jvm of jre1.5
.................!!

---

### Post by Ramses de Norre on 2006-03-15
sudo update-alternatives --config java and choose the right one.

---

### Post by mach5 on 2006-03-15
choose the right one means !!

---

### Post by Stormbringer on 2006-03-15
You choose the line that reads "j2re1.5-sun"...

[EDIT]
Since you installed the jdk - look out for a line reading something like "j2dk1.5-sun"
[/EDIT]

If you run...

# sudo update-alternatives --config java

...you get the following output (may look different on your system):

```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

```

In the example you would type in "2" and press enter.

Simple as that.

Storm.

---


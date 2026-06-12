---
title: "MonoDevelop won't find installed assemblies"
date: 2010-10-09
forum: General Help
---

### Post by ygoe on 2010-10-09
I  have just installed the package monodevelop on Ubuntu 10.4 and wanted  to try it out. I'm a long-time .NET developer using Visual Studio  2005/2008 on Windows so I'm familiar with the concepts. I created a new  Gtk# project in MonoDevelop, but the empty project already won't compile  because almost all referenced assemblies are missing. Here's the build  error messages: 

Warning: Die Referenz 'gtk-sharp, Version=2.12.0.0,  Culture=neutral, PublicKeyToken=35e10195dab3c99f' ist ungültig für das  Ziel-Framework des Projekts. (test1) 
Warning: Die Referenz 'gdk-sharp, Version=2.12.0.0, Culture=neutral,  PublicKeyToken=35e10195dab3c99f' ist ungültig für das Ziel-Framework  des Projekts. (test1) 
Warning: Die Referenz 'glib-sharp, Version=2.12.0.0,  Culture=neutral, PublicKeyToken=35e10195dab3c99f' ist ungültig für das  Ziel-Framework des Projekts. (test1) 
Warning: Die Referenz 'glade-sharp, Version=2.12.0.0,  Culture=neutral, PublicKeyToken=35e10195dab3c99f' ist ungültig für das  Ziel-Framework des Projekts. (test1) 
Warning: Die Referenz 'pango-sharp, Version=2.12.0.0,  Culture=neutral, PublicKeyToken=35e10195dab3c99f' ist ungültig für das  Ziel-Framework des Projekts. (test1) 
Warning: Die Referenz 'atk-sharp, Version=2.12.0.0, Culture=neutral,  PublicKeyToken=35e10195dab3c99f' ist ungültig für das Ziel-Framework  des Projekts. (test1) 
/home/yves/Projects/test1/test1/MainWindow.cs(7,7): Error CS0246:  The type or namespace name `Gtk' could not be found. Are you missing a  using directive or an assembly reference? (CS0246) (test1) 

Did I do something wrong? Did I not install some required (but  not depending-upon) packages? What's the problem here that a clean  installation fails from the beginning with the easiest test case?

---

### Post by isomz on 2010-11-18
I am having the very same problem.  How can I fix this?

---

### Post by krismatth3 on 2010-11-18
Have you installed gtk#? 
```

# sudo aptitude install gtk-sharp2

```

There are some nice tutorials here: [http://www.mono-project.com/GtkSharpBeginnersGuide](http://www.mono-project.com/GtkSharpBeginnersGuide)

---

### Post by directhex on 2010-11-19
Ensure you have the development packages for GTK# installed. These will be installed on new MD installs, but not on upgrades from Lucid to Maverick.

---

### Post by isomz on 2010-11-19
Thanks!  That did it.  I just had to install gtk-sharp2.

---


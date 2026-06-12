---
title: "Intel Atom Processor"
date: 2011-11-16
forum: General Help
---

### Post by Irwin109 on 2011-11-16
I'm using Ubuntu on my Netbook, I was using the Ubuntu Netbook Remix but updated it, it is now running Ubuntu 11.10. My problem is my graphics (in system settings -> system info) comes up as unkown and has no driver, I know my processor is an Intel Atom Processor but being an Ubunt-n00b I don't know how to go about getting it to work. Here's the graphics section of my System Testing Report:

graphics/resolutionPASSED  
graphics/minimum_resolutionPASSED  
graphics/displayPASSED  
graphics/xrandr_detect_modesPASSED  
graphics/compiz_checkPASSED  Gathering information about your system...   Distribution:          Ubuntu 11.10  Desktop environment:   GNOME  Graphics chip:         Intel Corporation N10 Family Integrated Graphics Controller  Driver in use:         vesa  Rendering method:      AIGLX  Checking if it's possible to run Compiz on your system...  [SKIP]   Checking for hardware/setup problems...           [SKIP]  At least one check had to be skipped:  Error: vesa driver in use   Would you like to know more? (Y/n)   

Thanks for any help

---

### Post by Docaltmed on 2011-11-16
go to the terminal, type in lspci:

```
$ lspci
```

Look down the list for something with video controller or VGA on the line. That will be your graphics card/chipset.

---

### Post by gordintoronto on 2011-11-16
> **Irwin109 said:**
> I'm using Ubuntu on my Netbook, I was using the Ubuntu Netbook Remix but updated it, it is now running Ubuntu 11.10. My problem is my graphics (in system settings -> system info) comes up as unkown and has no driver, I know my processor is an Intel Atom Processor but being an Ubunt-n00b I don't know how to go about getting it to work. Here's the graphics section of my System Testing Report:

...  Graphics chip:         Intel Corporation N10 Family Integrated Graphics Controller  Driver in use:         vesa...


What makes you think it's not working? Do you have a GUI when you run Ubuntu 11.10?

BTW, you have an Intel N10 graphics controller.

---


---
title: "configure desktops"
date: 2012-06-09
forum: General Help
---

### Post by Pedroski55 on 2012-06-09
How can I change the default 4 desktops in 12.04?? I would like more desktops, and have them stacked up one on top of the other, so that I can just ctrl alt up or ctrl alt down to switch between them

---

### Post by Rodney9 on 2012-06-09
How Can I Have More Than 4 Workspaces? - [http://www.omgubuntu.co.uk/2012/05/solve-six-common-gripes-with-ubuntu-12-04](http://www.omgubuntu.co.uk/2012/05/solve-six-common-gripes-with-ubuntu-12-04)

Rodney

---

### Post by gldvorak on 2012-06-09
Righr click in the pager area and select Settings. Then select Virtual Desktops. Here you can configure the number and the names of the desktops.

---

### Post by deadflowr on 2012-06-09
Adding workspaces is relatively easy. It depends on how daring you want to be.Two ways I have found is either installing the compizconfig-settings-manager opening up the general options section, clicking on desktop size and changing the vertical and horizontal setting as I'd like. 
Another way is install the gconf-tool, opening configuration editor going to apps, then compiz1, then general, then screen0, then options, then set the vsize and hsize as I'd like.
But be very warned, these two tools have lots of fun options which can make tweaking different settings feel impulsive, and doing something like changing a value you don't understand can junk up your system.

---


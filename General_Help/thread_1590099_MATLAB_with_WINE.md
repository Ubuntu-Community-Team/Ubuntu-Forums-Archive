---
title: "MATLAB with WINE?????"
date: 2010-10-07
forum: General Help
---

### Post by liquidmonkey on 2010-10-07
so i have MATLAB R2007b installed on my win7 partition and i would like to use MATLAB in LINUX of which i have version 10.04.

i have installed WINE but have no clue how to make MATLAB work although i have been told and read that its totally possible.


any ideas please????


ps, i'm sort of new to LINUX so please be general :)

---

### Post by Cilph on 2010-10-07
Matlab has unix versions that runs just fine on Ubuntu 10.04. I run r2010b (supplied by university) on Arch. There is no need to run it under Wine.

You can find the Unix versions on the Mathworks website. You can then run the installation script which will launch a nice GUI for installation and registration.

---

### Post by dargaud on 2010-10-07
Yes, but the Matlab unix version installs FlexLM for license management which is a major unreliable piece of ****. The open-source Octave is partially compatible with Matlab, so you may give it a try, depending on your needs.

---

### Post by Cilph on 2010-10-07
> **dargaud said:**
> Yes, but the Matlab unix version installs FlexLM for license management which is a major unreliable piece of ****. The open-source Octave is partially compatible with Matlab, so you may give it a try, depending on your needs.

It's integrated into matlab (it doesn't install it separately), and not a separate daemon you have to keep up 24/7. The windows version does the same. I have to supply it with a license file or account on the first time I run it and then it never bothers me with licenses ever again.

---

### Post by goltoof on 2010-10-07
> **liquidmonkey said:**
> so i have MATLAB R2007b installed on my win7 partition and i would like to use MATLAB in LINUX of which i have version 10.04.



In that case why not just run W7 as a virtual machine in Ubuntu and run MATLAB, and all other windows programs, inside of that?  Assuming you got a banging system with enough resources :)

Stay away from Wine, that's the best advice I ever received.  Running any software in an environment that it wasn't originally designed for is just a bad idea from the very beginning.

---

### Post by 3Miro on 2010-10-07
If you want to get good performance with MATLAB, wine will be better than VirtualBox. However, I tried running 2007 with wine once and it didn't run. At any rate, running the Linux version will be better.

As for the licencing, I thought that was only when you connect to a server for licencing. You can have a "standalone" copy which requires no daemons. Universities usually run licence services since they have many copies installed that draw licencing from the same server. Licences suck.

Octave is free, however, it is not 100% compatible with MATLAB.

---


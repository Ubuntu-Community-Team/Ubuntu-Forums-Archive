---
title: "Gimp install corrupted - how to fix?"
date: 2012-08-09
forum: General Help
---

### Post by RideABike on 2012-08-09
Hello all.. I need to get gimp working again. It has somehow become corrupted. In the terminal, I type 'gimp' to start it, and it returns the following error message:

 'error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory'

I have removed it with apt-get autoremove, reinstalled, but still has the error. I have also removed it through the package/SW manager, but that didn't help either. 

Any ideas on how to fix this to get gimp working again? I'm running Ubuntu 12.04.

---

### Post by RideABike on 2012-08-12
> **RideABike said:**
> Hello all.. I need to get gimp working again. It has somehow become corrupted. In the terminal, I type 'gimp' to start it, and it returns the following error message:

 'error while loading shared libraries: libgegl-0.0.so.0: cannot open shared object file: No such file or directory'

I have removed it with apt-get autoremove, reinstalled, but still has the error. I have also removed it through the package/SW manager, but that didn't help either. 

Any ideas on how to fix this to get gimp working again? I'm running Ubuntu 12.04.

Anyone?

---

### Post by SeijiSensei on 2012-08-12
First, "autoremove" only removes packages you no longer need.  To remove GIMP itself, run "sudo apt-get purge gimp*".

However, before you do that, let's trying installing the missing libgegl library and see if that fixes the problem.  Run "sudo apt-get -f install libgegl-0.0-0" and see if that works.  (The "-f" parameter "forces" an installation.) 

You might want to consider [upgrading to GIMP 2.8]("http://www.ubuntugeek.com/how-to-install-gimp-2-8-in-ubuntu-using-ppa.html") which is available in a PPA.  I'd remove the existing version first using "apt-get purge" before trying 2.8.

---

### Post by RideABike on 2012-08-12
> **SeijiSensei said:**
> First, "autoremove" only removes packages you no longer need.  To remove GIMP itself, run "sudo apt-get purge gimp*".

However, before you do that, let's trying installing the missing libgegl library and see if that fixes the problem.  Run "sudo apt-get -f install libgegl-0.0-0" and see if that works.  (The "-f" parameter "forces" an installation.) 

You might want to consider [upgrading to GIMP 2.8]("http://www.ubuntugeek.com/how-to-install-gimp-2-8-in-ubuntu-using-ppa.html") which is available in a PPA.  I'd remove the existing version first using "apt-get purge" before trying 2.8.

Thanks! I really appreciate your response. I was not aware of using purge. I purged the previous version of gimp and installed 2.8. All is working well now. Thanks again, very helpful.

---


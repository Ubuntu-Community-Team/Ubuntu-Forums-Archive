---
title: "Problem with php and mysql during LAMP Install"
date: 2010-04-05
forum: General Help
---

### Post by eshorebizgal on 2010-04-05
Okay I'm real new to Ubuntu so I hope I have put this in the right area.  I was installing the php and msql parts to continue install of LAMP and something went wrong.  I shut down the terminal, probably shouldn't have done that, and now if I open the terminal or the Synaptic Package Manager I get the following error.

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

I can't seem to find anything on how to do this, any help would be greatly appreciated.

---

### Post by djoxyk on 2010-04-05
it just warn you about the issue you need to resolve. type in terminal
sudo dpkg --configure -a

it should correct your installation and it will configure your packages like php and mysql.

---

### Post by eshorebizgal on 2010-04-05
Hi,

Thanks very much, as a beginner I included the ' before and after and I think that's why nothing happen.  Now everything seems to be fine, thanks for your advice.

---


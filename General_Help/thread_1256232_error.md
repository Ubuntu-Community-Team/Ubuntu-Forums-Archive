---
title: "error"
date: 2009-09-02
forum: General Help
---

### Post by aman25292 on 2009-09-02
the following is displayed when i run add remove program:-

(This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f')
when i run sudo apt-get update in terminal i displays 
"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."
please help me.

---

### Post by oldos2er on 2009-09-02
Open a terminal and run **sudo dpkg --configure -a**

---


---
title: "CHANGE DEFAULT LOCATION OF VMWARE VIRTUAL pc"
date: 2011-02-02
forum: General Help
---

### Post by nilanjan1988 on 2011-02-02
i have installed vmware server 2.0.2.
when i am creating a virtual pc it stores in my root(/) directory which has a small space free.....so i wanted to change the location of virtual pc in another hard drive.


main thing i wat to change location of virtual machines from (/var/lib/vmware/Virtual Machines/) main hdd to (/home/usrename/anotherdir)another hdd
[COLOR="DarkOrange"][SIZE="7"][FONT="Impact"]please help me please[/FONT][/SIZE][/COLOR]

---

### Post by gmargo on 2011-02-03
> **nilanjan1988 said:**
> 
[SIZE=1][COLOR=DarkOrange][FONT=Impact]help me[/FONT][/COLOR][/SIZE]

Is there a **/etc/vmware/** directory? (There was in vmware 1.x, don't know about 2.x)  The config file in that directory specifies the virtual machine directory.  Or you could always uses symbolic links.

---

### Post by nilanjan1988 on 2011-02-03
> **gmargo said:**
> Is there a **/etc/vmware/** directory? (There was in vmware 1.x, don't know about 2.x)  The config file in that directory specifies the virtual machine directory.  Or you could always uses symbolic links.

thank you.................

---


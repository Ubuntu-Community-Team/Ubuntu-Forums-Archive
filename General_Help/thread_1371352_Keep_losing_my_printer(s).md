---
title: "Keep losing my printer(s)"
date: 2010-01-03
forum: General Help
---

### Post by cjwescott on 2010-01-03
I have a networked printer and it keeps evaporating from my printer configuration.

When I open system\admin\Printing the "New" button is greyed out and there are no printers listed.  Only way I can rejuvenate this is to uninstall cups and reinstall it, then the "New" button is active and I can then reinstall my printer. I have done this four times now.

Any suggestions what is going on?

---

### Post by cjwescott on 2010-01-07
I continue to lose cups which also means I lose my printer and configurations.

I need help.  I experimented removing anything with the name cups in it in the synaptic package manager with the plan of only adding back only what I need.  Now I no longer have nor can find the package which will give me my gui interface to configure a printer (system/admin/printing).

Can someone help me with the package which will restore this?

Chris

---

### Post by cjwescott on 2010-01-08
I thought this would be an easy answer. I hope I do not need to reinstall the software to get it back.

Anyone?

---

### Post by plucky on 2010-01-08
> **cjwescott said:**
> I continue to lose cups which also means I lose my printer and configurations.

I need help.  I experimented removing anything with the name cups in it in the synaptic package manager with the plan of only adding back only what I need.  Now I no longer have nor can find the package which will give me my gui interface to configure a printer (system/admin/printing).

Can someone help me with the package which will restore this?

Chris

**system-config-printer-gnome**

Good Luck

---

### Post by cjwescott on 2010-01-08
That was it.  Thank you.

BTW:  How do you mark a thread as Solved?

---

### Post by gaffajoiner on 2010-01-09
where do i go to download cups for my printer, it is a HP photosmart premium

---

### Post by Robbyx on 2010-01-12
> **plucky said:**
> **system-config-printer-gnome**

Good Luck

My version of Ubuntu Karmic is not showing the path you mention above. 

Under system there is no entry for config. I have system--admin--printing. I do have  a printer configuration -local host. That does not allow me to add any new printers or find any old ones.

Robin

---

### Post by plucky on 2010-01-12
> **Robbyx said:**
> My version of Ubuntu Karmic is not showing the path you mention above. 

Under system there is no entry for config. I have system--admin--printing. I do have  a printer configuration -local host. That does not allow me to add any new printers or find any old ones.

Robin

**system-config-printer-gnome** is the name of the package in the Synaptic Package manager you have to install to be able to open the **system-config-printer** GUI located under **System > Administration > Printing** which is used to configure a printer.(See screenshot)


Good Luck

---

### Post by Robbyx on 2010-01-12
> **plucky said:**
> **system-config-printer-gnome** is the name of the package in the Synaptic Package manager you have to install to be able to open the **system-config-printer** GUI located under **System > Administration > Printing** which is used to configure a printer.(See screenshot)


Good Luck

Thank you. I now have my printers showing up again.

---


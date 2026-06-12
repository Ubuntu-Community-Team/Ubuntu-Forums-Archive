---
title: "Samba extra restriction"
date: 2012-09-10
forum: General Help
---

### Post by Jorel on 2012-09-10
Hi guys,

I had my samba working fine but i just wanna know if there's a way to add an extra restriction on the folders that i'm going to organize?

example i created:

[employee]
comment = for employee
browseable = yes
guest ok = no
path = /office/samba/employee
valid users = @employee
write list = @employee
create mask = 0755

and within that employee folder i have:
folder1 , folder2 , folder3

but i cant restrict folder1 from accessing folder2 and folder3,, is there a way for folder1 cannot access folder2 and folder3?
 

Thanks

---

### Post by luvshines on 2012-09-11
> **Jorel said:**
> 
and within that employee folder i have:
folder1 , folder2 , folder3

but i cant restrict folder1 from accessing folder2 and folder3,, is there a way for folder1 cannot access folder2 and folder3?

folder accessing folder ??
Do you mean employee accessing the folder ?

---

### Post by Jorel on 2012-09-12
> **luvshines said:**
> 
Do you mean employee accessing the folder ?

yup,, thats what i ment, employee accessing his own folder yet can also access another folder... all i can do is make other user have a read only access to other folder and have a read and write access to his folder... and all that will happen in just one specific folder...

ex. in my samba share, i have employee folder, submitting folder, PDF folder,, and all employee are restricted to other folder except the employee folder, but within that employee folder, i subdivided it into many folders again that i wanted it to have another restrictions so other employee cannot access other employee folder...

Thanks and hope i express well my thoughts..

---


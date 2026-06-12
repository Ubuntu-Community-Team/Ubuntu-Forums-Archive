---
title: "software*index*corrupt*cannot*install*anything"
date: 2010-02-16
forum: General Help
---

### Post by mikee286 on 2010-02-16
Hi

I*am*new*here*and*have*been*
an*on*and*off*ubuntu*user.**I*tried*upgrading*firefox*to*version*3.6*and*it*failed*now*I*get*this*message*every*time*I*try*to*install*something.

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

---

### Post by Ahadiel on 2010-02-16
> **mikee286 said:**
> Hi

I*am*new*here*and*have*been*
an*on*and*off*ubuntu*user.**I*tried*upgrading*firefox*to*version*3.6*and*it*failed*now*I*get*this*message*every*time*I*try*to*install*something.

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

Maybe*try*doing*what*it*says:
```
sudo apt-get update
sudo apt-get install -f
```

---

### Post by mikee286 on 2010-02-16
I have tried both of those actually nether seemed to help

---

### Post by mikee286 on 2010-02-18
> **Ahadiel said:**
> Maybe*try*doing*what*it*says:
```
sudo apt-get update
sudo apt-get install -f
```

I*did*that*and*got*the*following*message*in*the*terminal

 Malformed line 54 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.


any*other*Ideas,*also*what*about*the*problem*with*my*posts*turning*out*all*weird*when*posting*from*ubuntu?**it*looks*normal*as*I*type.**When*I*copy*and*paste*it*turns*out*fine*also

---

### Post by Ahadiel on 2010-02-18
> **mikee286 said:**
> I*did*that*and*got*the*following*message*in*the*terminal

 Malformed line 54 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.


any*other*Ideas,*also*what*about*the*problem*with*my*posts*turning*out*all*weird*when*posting*from*ubuntu?**it*looks*normal*as*I*type.**When*I*copy*and*paste*it*turns*out*fine*also

Paste the contents of /etc/apt/sources.list. Also, which version of Ubuntu are you using?

---

### Post by estyles on 2010-02-18
> **mikee286 said:**
> I*did*that*and*got*the*following*message*in*the*terminal

 Malformed line 54 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.


any*other*Ideas,*also*what*about*the*problem*with*my*posts*turning*out*all*weird*when*posting*from*ubuntu?**it*looks*normal*as*I*type.**When*I*copy*and*paste*it*turns*out*fine*also

Please post your sources.list file.  You can either browse to the file and copy-paste the text, or else just post the output of "cat /etc/apt/sources.list".

---


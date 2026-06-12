---
title: "Package install, gdebi-gtk doesn't work right."
date: 2012-06-08
forum: General Help
---

### Post by irv on 2012-06-08
I just notice that when I click on a deb file to install it, it open the Launch Application dialog box to run gdebi-gtk to install the deb file.
[ATTACH]219394[/ATTACH] 
The only problem is when you select the gdebi-gtk it opens it but it is blank.
[ATTACH]219395[/ATTACH]

---

### Post by dino99 on 2012-06-08
hm, mine works, but only have 2 packages installed: gdebi & gdebi-core

otherwise use dpkg : sudo dpkg -i mydeb2install

---

### Post by irv on 2012-06-08
> **dino99 said:**
> hm, mine works, but only have 2 packages installed: gdebi & gdebi-core

otherwise use dpkg : sudo dpkg -i mydeb2install

I don't have mydeb2install listed in package manager. What repository do I need?
I tried to reinstall gdebi and the gdebi-core, but this didn't help. I guess I could try completely removing them and then re-installing them again. I don't know why they just quite working.

---

### Post by dino99 on 2012-06-08
you're joking right ?

"mydeb2install" or "thispackagethatiwanttoinstallonthatdamnos", but you can use something else too :lolflag:

---

### Post by irv on 2012-06-08
OK, something strange happened. I completely remove gdebi and gdebi-core and did a reinstall. First I selected gdebi and marked it for install and it came up with a message that it needed the depended gdebi-core, but that it was not going to install it.(for some unknown reason, it didn't say.) So I canceled the install and selected gdebi-core first then selected the gdebi and they both installed, but I still have the same problem. I also checked for broken packages but didn't have any. It looks like something is wrong with gdebi-core but I am not sure how to fix it.

---

### Post by irv on 2012-06-08
> **dino99 said:**
> you're joking right ?

"mydeb2install" or "thispackagethatiwanttoinstallonthatdamnos", but you can use something else too :lolflag:
I got up really early this morning or maybe I just had a brain freeze. Da. At leasts we both can laugh at this one. :P

---


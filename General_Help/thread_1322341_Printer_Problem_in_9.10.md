---
title: "Printer Problem in 9.10"
date: 2009-11-10
forum: General Help
---

### Post by xenos90 on 2009-11-10
I recently upgraded to 9.10 form 9.04. I have an HP p1006 printer which worked fine on all previous versions of ubuntu. However it has stopped working on 9.10. When I send a print command it labels it as processing but never actually prints. I tried reinstalling the printer but that didn't work. 

Any help is greatly appreciated thanks.

---

### Post by fluffman86 on 2009-11-10
make sure that hplip is installed.  that' really helps.

---

### Post by xenos90 on 2009-11-10
I installed it, it keeps giving me two different errors. One says communications error, the other says unknown error 1018. I am still at a loss.

---

### Post by dalesomers on 2009-11-27
exact same problem here

---

### Post by XubuRoxMySox on 2009-11-27
Try this:

Open a browser and navigate to [http://localhost:631](http://localhost:631)

It's a graphical representation of HPLIP for your browser. Click on the **Administration** tab (you will be asked for your username and password - same as your computer) and look for your printer there. If not found, select **Add Printer** and choose yours from the drop-down list.

You can even set it up to share a network printer from there.

Let us know....

-Robin

---


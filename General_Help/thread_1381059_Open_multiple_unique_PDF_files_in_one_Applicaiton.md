---
title: "Open multiple unique PDF files in one Applicaiton"
date: 2010-01-14
forum: General Help
---

### Post by lawrencius on 2010-01-14
Hello everyone,

I read a lot of PDF documents using the default Document Viewer and I am wondering whether there is an application or a hack to have several PDF files concurrently open in one application (maybe like tabs in a browser?) since switching between one application to a specific PDF always takes time.(Especially with more than 4 PDF files concurrently running.)

Any help would be appreciated.

Thank ahead,
Nicholas

---

### Post by leandromartinez98 on 2010-01-14
I posted that as an idea in the Ubuntu Brainstorm a while
ago, but it does not seem very popular, it wasn't even aproved:

[http://brainstorm.ubuntu.com/idea/21412/](http://brainstorm.ubuntu.com/idea/21412/)

I don't know of an application that does that either.

---

### Post by jaezcurra on 2010-01-14
There is a package called pdfsam that you can install from Synaptic.  It lets you merge several pdf documents into one.  Maybe this is not what you are looking for.

---

### Post by Cheesemill on 2010-01-14
Adobe Acrobat Reader has a tabbed interface.
Go to System > Administration > Software Sources, click on the 'Other Software' tab and make sure the partner repositories are checked. Close Software Sources then just do:
```
sudo apt-get update && sudo apt-get install acroread
```Hit TAB then ENTER to agree to the license when prompted and you're good to go.

---

### Post by lawrencius on 2010-01-14
Thank you Cheesemill! That's exactly what I meant.

---

### Post by inearlygaveup on 2010-02-28
> **Cheesemill said:**
> Adobe Acrobat Reader has a tabbed interface.
Go to System > Administration > Software Sources, click on the 'Other Software' tab and make sure the partner repositories are checked. Close Software Sources then just do:
```
sudo apt-get update && sudo apt-get install acroread
```Hit TAB then ENTER to agree to the license when prompted and you're good to go.
Hi Cheesemill
Do you know of anything like this for 8.10 Intrepid Ibex

---


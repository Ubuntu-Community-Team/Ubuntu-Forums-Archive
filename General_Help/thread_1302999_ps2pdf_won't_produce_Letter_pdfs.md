---
title: "ps2pdf won't produce Letter pdfs"
date: 2009-10-27
forum: General Help
---

### Post by leorolla on 2009-10-27
Hi!

I run the command
```
ps2pdf -sPAPERSIZE=letter mypaper.ps mypaper.pdf
```and still I get A4-size documents.

I'm runing Ubuntu 8.04.3 in an Acer Aspire One netbook, and have installed livetex.

**pdflatex** is doing fine, **dvipdf** is doing bad, but anyway I need to go through **.ps** because I use the **latex package** **psfrag**.

Thank you in advance!

---

### Post by leorolla on 2009-10-28
PS: I serached the forum and did not find a report of the same problem.

I have tryied different machines and I get the same output.

---

### Post by leorolla on 2009-10-28
**Solved**

The admins of my department found the solution:

It seems that ps2pdf no longer chooses the paper size, so it must be in the ps file:

dvips -t letter mypaper

or

dvips -t a4 mypaper

---


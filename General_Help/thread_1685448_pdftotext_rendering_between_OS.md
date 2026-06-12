---
title: "pdftotext rendering between OS?"
date: 2011-02-10
forum: General Help
---

### Post by kernelgpf on 2011-02-10
I had a working pdftotext script working and custom made a parser for the info in it, but upon moving from CentOS 5.5 to Ubuntu (version unknown) and installing poppler-utils, pdftotext works, but the rendering is different by quite a bit causing a ton of issues. I also tried on another CentOS (5.2 this time) and it rendered the same as Ubuntu.

I'm trying to figure out the problem so it renders the same, I'm using the same code and everything.

---

### Post by code_expert on 2011-06-14
I was wondering how did you solved this issue? I have a pdf file and all the parsing is done on ubuntu, and it works fine. When I move it to CentOS however, the pdftotext creates a very different txt file and causes lots of problems.

---

### Post by code_expert on 2011-06-14
Ok, I solved the problem. You need to use '-raw' with your pdftotext so it works on both systems the same way.

---


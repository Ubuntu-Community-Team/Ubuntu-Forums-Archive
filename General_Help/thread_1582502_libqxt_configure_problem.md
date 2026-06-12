---
title: "libqxt configure problem"
date: 2010-09-26
forum: General Help
---

### Post by pooya_mr2009 on 2010-09-26
hi all
i want to install libqxt so i used : ./configure
but i saw : 
checking for qt4     failure
but i have qt4 so what's problem?
tnx.

---

### Post by pooya_mr2009 on 2010-09-29
no help?

---

### Post by luigi_mb on 2010-09-29
> **pooya_mr2009 said:**
> hi all
i want to install libqxt so i used : ./configure
but i saw : 
checking for qt4     failure
but i have qt4 so what's problem?
tnx.

When you say that you have qt4, do you mean Qt SDK? If so, add these lines to your ~/.bashrc

export QTDIR=/opt/qtsdk-2010.05
export PATH=/opt/qtsdk-2010.05/qt/bin:$PATH
export LD_LIBRARY_PATH=/opt/qtsdk-2010.05/qt/lib:$LD_LIBRARY_PATH

(Change "2010.05" to whatever version you installed).

/luigi

---


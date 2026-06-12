---
title: "Qt headers??? Source installation woes..."
date: 2006-04-11
forum: General Help
---

### Post by gigi1234 on 2006-04-11
I am trying to install an application from source and I keep getting the following error:

*checking for Qt... configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!*

I tried installing the qt-dev packages in Synaptic but I am still getting the error. 

I also ran the following: 

*apt-get install libqt3-headers*

I received a message that these headers were already installed. I am pretty lost. Does anyone know how to solve this issue?

Thanks!!!

---

### Post by az on 2006-04-11
You probably need th libqt3-mt-dev package and it's dependencies.

---

### Post by gigi1234 on 2006-04-11
Thanks I will give it a try!

---


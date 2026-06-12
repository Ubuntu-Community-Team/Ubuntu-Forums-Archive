---
title: "How to install Gambas 2"
date: 2009-09-14
forum: General Help
---

### Post by abhishek3535 on 2009-09-14
I am new to Ubuntu ,i am running Ubuntu 8.04LTS , i am having a tough time installing Gambas 2 which i require for my college project, since a single .deb package is not available ... Can Some one Who is using Gambas 2 make a single .deb package with all dependencies and share it.. it will be very helpful for me...

thenk you..... enjoy the spirit of ubuntu....

---

### Post by SteveDee on 2009-09-15
> **abhishek3535 said:**
> I am new to Ubuntu ,i am running Ubuntu 8.04LTS , i am having a tough time installing Gambas 2...
....

You don't give details of your problem or what you have tried, so I'm going to suggest this:-
- go to System > Administration > Software Sources > Third Party Software
- add this APT line: deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) hardy main
- close this window, which forces an update.
- go to Applications > Add/Remove and type in the search box: gambas
- this should display the option to install Gambas2

You should now be able to get started with Gambas.

---


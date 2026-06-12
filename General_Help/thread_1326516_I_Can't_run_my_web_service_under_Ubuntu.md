---
title: "I Can't run my web service under Ubuntu"
date: 2009-11-14
forum: General Help
---

### Post by rafaelangarita on 2009-11-14
I have a web service that works perfectly fine when I deploy it on my macos x and windows xp machines. Now I'm need to deploy it on a virtual machine with Ubuntu and I get this exception when I invoque the method of my web service

```

java.lang.ExceptionInInitializerError
    at ve.usb.HibernateUtil.<clinit>(HibernateUtil.java:28)
    at ve.usb.TestHelper.<init>(TestHelper.java:21)
    at ve.usb.USB_RegCivil.USB_RegCivil_consulta(USB_RegCivil.java:28)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke

```I also found this:
```

Caused by: java.lang.NoClassDefFoundError
        at ve.usb.TestHelper.<init>(TestHelper.java:21)
        at ve.usb.USB_RegCivil.USB_RegCivil_consulta(USB_RegCivil.java:28)


```I'm using Glassfish and Java 5.
Someone told me to make sure that I am are using a Sun VM, not the GNU dito that often is distributed with Linux etc. 

I think I correctly installed the Sun VM but I'm still having the same problem.

Thenk you very much for your help.

---


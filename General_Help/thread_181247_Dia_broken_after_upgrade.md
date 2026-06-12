---
title: "Dia broken after upgrade"
date: 2006-05-23
forum: General Help
---

### Post by [S|G] on 2006-05-23
Hello,

I upgraded my system using adept today and after the upgrade my Dia (it's a program that draws diagrams) won't work. It was removed by adept and it won't reinstall now. Here is the output from apt-get:

```

diego@SnowGust:~$ sudo apt-get install dia
dia: Depende: dia-common (= 0.94.0-17.1ubuntu2) mas 0.94.0-17.1ubuntu3 está para ser instalado
       Depende: dia-libs (= 0.94.0-17.1ubuntu2) mas 0.94.0-17.1ubuntu3 está para ser instalado

```

Basically it says that it depends on an older version of dia-libs that has been installed on my system (installed version is 0.94.0-17.1ubuntu3). I tried uninstalling dia-coomon and dia-libs, but even so Dia won't install.

Are there any solutions, such as forcing apt-get to force install of the Dia package or do I have to download and compile from source?

---


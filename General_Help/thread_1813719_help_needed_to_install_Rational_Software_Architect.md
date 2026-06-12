---
title: "help needed to install Rational Software Architect 7.5 on Natty 64bit"
date: 2011-07-28
forum: General Help
---

### Post by magowiz82 on 2011-07-28
Hi,
I need to reinstall IBM RSA 7.5 on a 64bit Natty (I previously installed it successfully in Maverick) but since the installer (and the program) is for 32-bit systems I got some library issues (I attached a full log).
The key lines are :
```
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

```

After these lines the installer shows an error message and then closes.

I previously solved a similar issue with libpixbuff like described here : [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/781870](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/781870) (the second workaround).

What should I try?

---

### Post by jerrrys on 2011-07-28
i do not use this package, but got some hits

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wrong+ELF+class&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wrong+ELF+class&sa=Search&cof=FORID:9#926)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgvfsdbus&sa=Search&cof=FORID:9#986](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgvfsdbus&sa=Search&cof=FORID:9#986)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgiobamf&sa=Search&cof=FORID:9#996](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgiobamf&sa=Search&cof=FORID:9#996)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=IBM+RSA&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=IBM+RSA&sa=Search&cof=FORID:9#926)

good luck

---

### Post by magowiz82 on 2011-07-29
> **jerrrys said:**
> i do not use this package, but got some hits

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wrong+ELF+class&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=wrong+ELF+class&sa=Search&cof=FORID:9#926)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgvfsdbus&sa=Search&cof=FORID:9#986](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgvfsdbus&sa=Search&cof=FORID:9#986)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgiobamf&sa=Search&cof=FORID:9#996](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=libgiobamf&sa=Search&cof=FORID:9#996)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=IBM+RSA&sa=Search&cof=FORID:9#926](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=IBM+RSA&sa=Search&cof=FORID:9#926)

good luck

I had no luck with the links you suggested me, regarding libgvfsdbus.so I have both versions installed in my system: 
```
locate libgvfsdbus.so
/usr/lib/gio/modules/libgvfsdbus.so
/usr/lib32/gio/modules/libgvfsdbus.so

```

---

### Post by jerrrys on 2011-07-29
sorry to hear that.  i took a look at there forums and did not find any linux support to speak of.  perhaps if you keep bumping your thread (especially on the weekends) you will find someone that is actually using this software.  also, since this is such a "special category" question, you may want to consider other linux forums to post in.  like maybe [ask.com  ]("http://www.ask.com/web?q=linux&search=&qsrc=0&o=0&l=dir"). good luck

---


---
title: "Conky problem with command ${totalup wlan0}"
date: 2011-12-09
forum: General Help
---

### Post by esbrinartot on 2011-12-09
I have a problem with conky installed in Ubuntu 11.04 64bits.

The command:
${GOTO 36}Enviado:${GOTO 120}${totalup wlan0}

Give me an incorrect result. Give me that I've uploaded 2.39 Gib and it's totally incorrect. Doesn't matter if I restart/clean the system or not the result is always incorrect. You can have a look on my desktop in order you can check what I tell you:

[http://img845.imageshack.us/img845/1699/readetrabajo1001d.png]("http://img845.imageshack.us/img845/1699/readetrabajo1001d.png")

Enviado: 2.39 GiB     (Total traffic uploaded: 2.39 Gib)

I've tried everything and in other computers the same command works properly.

Can anyone help me to fix the problem?

Alguien me sabe indicar como averiguar el problema y solucionarlo?

---

### Post by stinkeye on 2011-12-09
From man conky
> totaldown (net) 
 Total download, overflows at 4 GB on Linux with 32-bit arch and there doesn't seem to be a way to know how many times it has already done that before conky has started. 

totalup (net) 
 Total upload, this one too, may overflow
Whatever that means??? :confused:

Could try vnstat.
```
sudo apt-get install vnstat
```
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9650052&postcount=6[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9650052&postcount=6")

---

### Post by esbrinartot on 2011-12-09
> **stinkeye said:**
> From man conky

Whatever that means??? :confused:

Could try vnstat.
```
sudo apt-get install vnstat
```
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=9650052&postcount=6[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9650052&postcount=6")

Thks to reply.

After 3 days with the problem has disappeared. I think it's because I've switch off the router. But I'm not sure,

I will close the topic. If in the future I have new problem I will install the packet you advised me.

thks

---


---
title: "Problem with compiz ubuntu 10.10, window borders disappear"
date: 2010-10-11
forum: General Help
---

### Post by mahado051 on 2010-10-11
Hello,

I just installed ubuntu 10.10 on my notebook, and I had a problem with compiz, it loses the windows borders, when i excecute

```
compiz --replace
```


i get this output

```
Starting gtk-window-decorator
compiz: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_property_to_quads
```

Does anyone know something about this problem?

Greetings

---

### Post by Tekmoor on 2010-10-11
I had this problem and fixed it by completely removing all compiz packages and then reinstalling them.

I think the problem resulted for me from using the Compiz Packagers PPA, so I made sure to remove that source so that the default compiz packages would be installed.

---

### Post by tuwxyz on 2010-10-11
> **Tekmoor said:**
> I had this problem and fixed it by completely removing all compiz packages and then reinstalling them.

I think the problem resulted for me from using the Compiz Packagers PPA, so I made sure to remove that source so that the default compiz packages would be installed.

Exactly. I had the same error message. I have found that libdecoration0 is form PPA and changed it to version 1:0.8.6-0ubuntu9. Works like a charm.

---

### Post by mahado051 on 2010-10-11
thanks both!

I fix that issue, now compiz behaves better, but it's still without the window borders =/, it could be another package with a wrong version, but i had uninstalled all packages and remove them from the cache, so i don't know wich package could be

and also, i dont get this error message again

> **mahado051 said:**
> ```
Starting gtk-window-decorator
compiz: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_property_to_quads
```

thanks, i hope to solve this problem

---

### Post by muecoy on 2010-10-12
> **mahado051 said:**
> thanks both!

I fix that issue, now compiz behaves better, but it's still without the window borders =/, it could be another package with a wrong version, but i had uninstalled all packages and remove them from the cache, so i don't know wich package could be

and also, i dont get this error message again



thanks, i hope to solve this problem

One solution I found, was to install "libdecoration0 v0.8.4" by Lucid and it worked very well, I got to reinstall the software

look, here you can find package
https: / / launchpad.net/ubuntu/lucid/i386/libdecoration0/1 :0.8.4-0ubuntu4

[I][FONT=Comic Sans MS]Una solucion que encontre, fue instalar "libdecoration0 v0.8.4" de LUCID y me funciono muy bien, me toco reinstalar el soft

mira, aqui puedes encontrar el paquete
[https://launchpad.net/ubuntu/lucid/i386/libdecoration0/1:0.8.4-0ubuntu4](https://launchpad.net/ubuntu/lucid/i386/libdecoration0/1:0.8.4-0ubuntu4)

[/FONT][/I]I hope it works for you ;)

---

### Post by pirron on 2010-10-12
I had the same problem and I solved downgrading libdecoration0. Thanks!!

---

### Post by carlosjimy on 2010-10-14
Muchas gracias por las ideas dadas, me han ayudado a solucionar el problema!

Ocurre que al instalar (o actualizar) ubuntu 10.10 y luego de instalar y configurar los efectos de escritorio con compiz al reiniciar desaparecieron los bordes de ventana y no era posible activar los efectos de escritorio. La solución:

Reinstalar compiz y sus dependencias forazando la versión 1:0.8.6-0ubuntu9(maverik) desde Synaptic (en lugar de dejar la 1:0.9.0)

Los archivos re-instalados fueron:

**compiz** 1:0.8.6-0ubuntu9(maverik)
**compizconfig-beckend-gconf** 0.8.4-1ubuntu5
**compiz**-**plugins** 1:0.8.6-0ubuntu9(maverik)
**compiz-core **1:0.8.6-0ubuntu9(maverik)
**compiz-fusion-plugins-main** 0.8.6-0ubuntu2
**compiz-genome **1:0.8.6-0ubuntu9(maverik)
**libdecoration0** 1:0.8.6-0ubuntu9(maverik)
**libcompizconifg0** 0.8.4-0ubuntu3

Reinicié el servidor X (ctrl+alt+back) y todo volvió a funcionar perfecto). No sé a qué se deba el problema ni estoy seguro sobre volver a actualizar estos archivos, sin embargo ahora todo funciona bien. Espero les sea de ayuda a más personas. [Lo dejé en español porque no encontré más información en español en otros sitios]

Saludos.
Carlos.

---

### Post by dan1701a on 2010-10-14
I had the same problem, and noticed I also had the Compiz Packagers PPA enabled, so I disabled it, removed all Compiz packages (including the fusion-icon and emerald), then refreshed the sources in Synaptic and reinstalled. So far it seems to work (the fusion-icon works, at least). I thought at first it was due to the Elementary theme, but from what I've read it doesn't seem to matter what theme is being used. Hopefully some of these tips will help others, because it was a huge pain in the neck while it didn't work. 

Summary:

Disabled Compiz Packagers PPA in sources
Removed all compiz packages (including fusion-icon and emerald)
Refreshed sources in Synaptic
Reloaded compiz (including fusion-icon and emerald)
Re-enabled normal visual effects in System>Preferences>Appearance>Visual Effects

---

### Post by Tumpster on 2010-10-16
> **dan1701a said:**
> I had the same problem, and noticed I also had the Compiz Packagers PPA enabled, so I disabled it, removed all Compiz packages (including the fusion-icon and emerald), then refreshed the sources in Synaptic and reinstalled. So far it seems to work (the fusion-icon works, at least). I thought at first it was due to the Elementary theme, but from what I've read it doesn't seem to matter what theme is being used. Hopefully some of these tips will help others, because it was a huge pain in the neck while it didn't work. 

Summary:

Disabled Compiz Packagers PPA in sources
Removed all compiz packages (including fusion-icon and emerald)
Refreshed sources in Synaptic
Reloaded compiz (including fusion-icon and emerald)
Re-enabled normal visual effects in System>Preferences>Appearance>Visual Effects


This does not work, I have the latest NVIDIA drivers installed through command line and have no other problems, looking for solutions to get Compiz working properly.

---

### Post by evelio on 2010-10-16
Thank you Carlos! for the tip of install those packages versions... my mistake was to use compiz ppa that comes in ubuntu tweak and re-install without cleaning the cache or update packages list

I've followed this steps:

- backed up my compiz configurations (I've worked a lot on them ;) )
- Deleted compiz ppa
- purged all compiz packages
- cleaned apt cache
- updated packages list
- installed compiz again
- log out and log in
- I was getting the ugly blue compiz window decoration so just opened gconf-editor and set apps/gwd/use_metacity_theme to TRUE. 
- restored my settings

et voilà I get back my beautiful maverick :)

---

### Post by dan1701a on 2010-10-16
> **Tumpster said:**
> This does not work, I have the latest NVIDIA drivers installed through command line and have no other problems, looking for solutions to get Compiz working properly.

Not sure where to go from here, then. My NVIDIA drivers are current as well, yet my process worked for me (and continues to work). The only difference may be that I installed the NVIDIA drivers through System>Administration>Additional Drivers instead of the command line.

Have you tried the Nouveau drivers instead of the NVIDIA drivers?

---

### Post by Tumpster on 2010-10-20
> **evelio said:**
> Thank you Carlos! for the tip of install those packages versions... my mistake was to use compiz ppa that comes in ubuntu tweak and re-install without cleaning the cache or update packages list

I've followed this steps:

- backed up my compiz configurations (I've worked a lot on them ;) )
- Deleted compiz ppa
- purged all compiz packages
- cleaned apt cache
- updated packages list
- installed compiz again
- log out and log in
- I was getting the ugly blue compiz window decoration so just opened gconf-editor and set apps/gwd/use_metacity_theme to TRUE. 
- restored my settings

et voilà I get back my beautiful maverick :)


Doing this fixed it, it's the Compiz PPA that breaks it for me. After following your steps I have no problems.

---

### Post by serein on 2010-11-02
this ain't fixin it for me... the error's still there.
i added compiz and x-swat ppa at the same time, and the **** just crashed down on me. so, i purged all nvidia and compiz, removed the ppas, cleaned the cache, updated repos, reinstalled and that error is still mocking me... what the f**k!?

edit: sry. seems there's no problem now... ehrm... even though i purged and cleaned and purged and updated lidecoration0-0.9 stayed with me and janked my chain. fixed that and voila.

---


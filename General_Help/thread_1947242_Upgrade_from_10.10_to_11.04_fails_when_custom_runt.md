---
title: "Upgrade from 10.10 to 11.04 fails when custom runtime is present"
date: 2012-03-26
forum: General Help
---

### Post by mfema on 2012-03-26
[FONT=Cambria][SIZE=3][COLOR=#0033cc]On doing an upgrade from 10.10. to 11.04 using Upgrade Manager everything works fine.[/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc]But on installing a software that bundle its owns runtime environment( loader and system files) and installs the custom runtime ( basically loader) in the location where  the native one resides, the above mentioned upgrade fails.(Upgrade starts and after sometime it encounters an error and aborts.)[/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc] [/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc]Basically , /usr/bin/dpkg throws up an error on being unable to locate a system shared library in the  aforesaid third party runtime folder ( /usr/bin/dpkg should not search  the third party runtime folder.Instead it should look at the system default folder)[/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc] [/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc]But if we remove the installed third party loader from the default system location /lib and place it in some other location , the upgrade problem goes away.[/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc] [/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc]This makes me believe /usr/bin/dpkg invokes(loads) the wrong loader and as such goes  looking for the dependent  libraries in the third party folder."[/COLOR][/SIZE][/FONT]
[FONT=Cambria][SIZE=3][COLOR=#0033cc][/COLOR][/SIZE][/FONT] 
[FONT=Cambria][SIZE=3][COLOR=#0033cc]Can some one from the group throw more insight on this ? [/COLOR][/SIZE][/FONT]

---


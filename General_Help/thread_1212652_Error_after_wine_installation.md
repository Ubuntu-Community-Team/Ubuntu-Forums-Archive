---
title: "Error after wine installation"
date: 2009-07-13
forum: General Help
---

### Post by jubop on 2009-07-13
Tried installing wine on Ubuntu 8.10. sorry can't find the website where I got the instructions, but basically something must have gone wrong and now I can't use synaptic package manager get this error:

E: Type '--2009-07-13' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

And if I try to open update manager get this message:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--2009-07-13' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.'

does anyone know how to fix it? If you can help please explain things in detail not the most savvy ubuntu user :( (but I'm learning)

Thanks

---

### Post by x33a on 2009-07-13
open a terminal, post the output of
```
cat /etc/apt/sources.list.d/winehq.list
```

---

### Post by jubop on 2009-07-14
gives me this:

--2009-07-13 23:01:00--  [http://wine.budgetdedicated.com/pt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/pt/sources.list.d/intrepid.list)
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-07-13 23:01:01 ERROR 404: Not Found.

---

### Post by x33a on 2009-07-14
actually i wanted to see the contents of the winehq.list file.

ok, press alt+f2, then paste this into the box:
```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```

then paste the contents of that file here, and please embed it into a code box.

---

### Post by Marked One on 2009-07-14
I hava a similar problem, but with playonlinux. (it's based on WINE)
The error code is the same, but when I looked in the sources dir, I found no sources.list, only playonlinux.list, with read only permissions, which I can't edit. (but I'm root)

I typed ```
 rm ~/etc/apt/sources.list.d/playonlinux.list
```, but it gives me ```
rm: cannot remove `/home/insignia/etc/apt/sources.list.d/playonlinux.list': No such file or directory

```

---

### Post by jubop on 2009-07-14
> **x33a said:**
> actually i wanted to see the contents of the winehq.list file.

ok, press alt+f2, then paste this into the box:
```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```

then paste the contents of that file here, and please embed it into a code box.

did that pretty sure i got the same thing:

```
--2009-07-13 23:01:00--  http://wine.budgetdedicated.com/pt/sources.list.d/intrepid.list
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-07-13 23:01:01 ERROR 404: Not Found.
```

---

### Post by CatKiller on 2009-07-14
> **jubop said:**
> gives me this:

--2009-07-13 23:01:00--  [http://wine.budgetdedicated.com/pt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/pt/sources.list.d/intrepid.list)
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-07-13 23:01:01 ERROR 404: Not Found.

For some reason, rather than putting the list of package sources into the file you've put a bunch of error messages in there instead. Best delete it and try again. ```
sudo rm /etc/apt/sources.list.d/winehq.list
```

---

### Post by CatKiller on 2009-07-14
> **Marked One said:**
>  I typed ```
 rm ~/etc/apt/sources.list.d/playonlinux.list
```, but it gives me ```
rm: cannot remove `/home/insignia/etc/apt/sources.list.d/playonlinux.list': No such file or directory

```

Why did you type that? The ~ signifies your Home folder, which is why you're trying to delete a completely different file. Which isn't there.

---

### Post by jubop on 2009-07-14
thanks I removed it and both synaptic package manager and system update are working now, I updated my system and restarted my computer but in accesories it still shows wine. just want to make sure this is correct.

---

### Post by CatKiller on 2009-07-14
Yes. You haven't removed Wine, just a listing of a place that you could get a newer version of Wine if the listing hadn't been broken.

---

### Post by Marked One on 2009-07-15
Oh, OK thanks, I found the solution elsewhere.

thanks for your help.

---

### Post by wyrless2002 on 2009-09-17
Thanks to all! I was having the same problem, I couldn't find PlayOnLinux in the /etc/apt/sources (because it was in /etc/apt/sources.list.d).

---


---
title: "Text not showing up in FLASH (firefox)"
date: 2006-06-03
forum: General Help
---

### Post by maka on 2006-06-03
I installed the flash plugin with: sudo apt-get install flashplugin-nonfree, sudo update-flashplugin

this works and installs the flash.  everything works but text doesnt show up.

I've looked through almost all the threads in the forum, most solutions for this problem were to install the gsfonts, gsfonts-X11, and msttcorefonts.  I've installed all these and used: sudo fc-cache -f -v

Text still doesnt show up!! anyone share this prob?  help me, i like ubuntu but text in flash is very important for me so i dont want to have to resort to windows.

Thanks! ](*,)

---

### Post by adwait on 2006-06-03
same here........any solutions?

---

### Post by pyromithrandir on 2006-06-03
I had this problem a long time ago. I don't remember what I did to fix it, though, sorry. But just so you know, there is hope :)

I was just googling around and found this bug report that says that it' is fixed with the new dapper packages, so make sure you are up to date: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/3204](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/3204)

---

### Post by maka on 2006-06-03
[QUOTE=pyromithrandir]I had this problem a long time ago. I don't remember what I did to fix it, though, sorry. But just so you know, there is hope :)

I was just googling around and found this bug report that says that it' is fixed with the new dapper packages, so make sure you are up to date: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/3204](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/3204)[/QUOTE]

thanks for the hope :)  but i'm getting increasingly frustrated with this problem.  

I was just wondering if anyone knew if theres a way to find out what FONT is being used in a flash on a website.  I'm asking this because I want to see if I have that font actually installed...

If that doesnt work, is there any workaround? like is there a way to force all flash players to only use one type of font?  maybe a browser/addon that does that?

I really need flash up and running fully. :confused:

---

### Post by porschemad911 on 2006-06-03
Perhaps try manually installing the Flash 7.0 plugin somewhere from the tar.gz file, then linking it in ~/.mozilla/plugins (or /usr/lib/firefox/plugins I guess).

Then apt-get install gsfonts-x11.

That's all I've done and fonts in flash work perfectly.

---

### Post by david.vikstrom on 2006-06-03
You aint getting no text or is it just when the text is loaded externally? Cos I had that problem and the actual fix was to remove ALL flashplayers and then install the nonfree one. In someway the free ones were blocking the nonfree... :(

---

### Post by maka on 2006-06-03
[QUOTE=david.vikstrom]You aint getting no text or is it just when the text is loaded externally? Cos I had that problem and the actual fix was to remove ALL flashplayers and then install the nonfree one. In someway the free ones were blocking the nonfree... :([/QUOTE]

hmm, when theres a flash player loaded and I have to input values, and I type, I dont see the text that I am typing. :(

Also, I basically have a clean install of dapper... The first and only Flash I installed was the flashplugin-nonfree from the extra repos.

---

### Post by Poka64 on 2006-06-03
[QUOTE=porschemad911]Perhaps try manually installing the Flash 7.0 plugin somewhere from the tar.gz file, then linking it in ~/.mozilla/plugins (or /usr/lib/firefox/plugins I guess).

Then apt-get install gsfonts-x11.

That's all I've done and fonts in flash work perfectly.[/QUOTE]
This is the solution for me

```
sudo apt-get install gsfonts-x11
```

Thx for this porschemad911 !

---

### Post by brownrl on 2006-06-03
Flash sites that have missing fonts are weird background things are generally the flash sites made by amateurs. They compile the flash in the latest version with no compatibility set for older version. So they make it on Mac or Windows using flash 8 but flash 7 is what is on linux...

---

### Post by fluid_motion on 2006-06-09
[QUOTE=Poka64]This is the solution for me

```
sudo apt-get install gsfonts-x11
```

Thx for this porschemad911 ![/QUOTE]

Worked for me too! Thanks porschemad911! :)

---


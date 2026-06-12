---
title: "Forcing a module to unload"
date: 2006-02-28
forum: General Help
---

### Post by ashrack on 2006-02-28
how can I force to unload a module???
when I try
```
rmmod -f ****
```
it still will not unload a module that is being used.
ps.how can I see which app is using a module?

---

### Post by joneberger on 2006-02-28
maybe this is infantile, but does modprobe -r (module name) work?

---

### Post by ashrack on 2006-02-28
[QUOTE=joneberger]maybe this is infantile, but does modprobe -r (module name) work?[/QUOTE]
yes it works on a module that is not being used. 
But I would like to force to unload a module that is being used?

---

### Post by wrtrdood on 2006-02-28
Check first with lsmod.  There is probably a dependency.  For example, I used to have to unload the orinoco module but couldn't because orinoco_pci depended on it.  I had to first remove orinoco_pci and then orinoco would remove without a problem.

The lsmod command will return this for you and should list the dependent modules, if any.

---

### Post by ashrack on 2006-03-07
but isnt there a way that I could forcefully unload a module even if it is being used without me having first to remove dependencies and all??

 I thought that was the reason for
```
rmmod -f ****
```

---

### Post by ashrack on 2006-03-08
i quess not. but then why would:
```
rmmod -f ****
```
even exist than if it cant forcefully unload a module?

---

### Post by bb002 on 2006-03-08
It is possible but you would have to write a frontend to modprobe.

1) the script would take a list of modules from the command line, running each of them through lsmod to get their dependencies. As well as the dependencies dependencies. Whiel, building a list of the modules to remove in the proper order to avoid failed removals.
2) print a list of modules and ask if this is ok.
3) quit or begin removal depending on user resonse.


That maybe a over simplication but you get the idea. I'd write you a script but my scripting skills are not all that great.


[edit]
inorder for "rmmod -f *" to work CONFIG_MODULE_FORCE_UNLOAD must have been enabled when the kernel was compiled. No idea if the stock kernel have it enabled or not...

---

### Post by ashrack on 2006-03-09
BB002
My scripting skills are NONE.
ps. will check if I have CONFIG_MODULE_FORCE_UNLOAD compiled into my custom made kernel.

---

### Post by codejunkie on 2006-03-09
[QUOTE=ashrack]BB002
My scripting skills are NONE.
ps. will check if I have CONFIG_MODULE_FORCE_UNLOAD compiled into my custom made kernel.[/QUOTE]
adding the module to /etc/modprobe.d/blacklist will keep the module from loading just add it to the bottom of the file like this
```
blacklist nameofmodule
```
and reboot and the module should be removed, however i noticed that some modules like agpgart will reload unless you blacklist the things that depend on them also.

---


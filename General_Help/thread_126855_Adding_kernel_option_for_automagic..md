---
title: "Adding kernel option for automagic."
date: 2006-02-07
forum: General Help
---

### Post by chaumurky on 2006-02-07
I've just discovered I need the irqpoll pci=irqroute combination of kernel options for an old machine I just  purchased and I just wanted to confirm the best place to add these lines in grub's menu.lst so that these options are added on kernel upgrades. Should I add it to the 'kopt' line like below?

i.e.

```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# [COLOR=Red]kopt=root=/dev/hda1 ro irqpoll pci=irqroute[/COLOR]

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##
```

It looks right to me but I just wanted to confirm with others. 

Thanks for your time. :)

---

### Post by dcstar on 2006-02-08
[QUOTE=chaumurky]I've just discovered I need the irqpoll pci=irqroute combination of kernel options for an old machine I just  purchased and I just wanted to confirm the best place to add these lines in grub's menu.lst so that these options are added on kernel upgrades. Should I add it to the 'kopt' line like below?

i.e.

```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# [COLOR=Red]kopt=root=/dev/hda1 ro irqpoll pci=irqroute[/COLOR]
......
## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
**# nonaltoptions=quiet splash**
......
## ## End Default Options ##
```

It looks right to me but I just wanted to confirm with others. 

Thanks for your time. :)[/QUOTE]
I am told that you are supposed to use "nonaltoptions" for this sort of thing (as it keeps it after a kernel upgrade),  but give your method a go.

---

### Post by chaumurky on 2006-02-09
Both methods keep the options on new kernel installs. 'kopt' adds options to all boot items (except memtest, of course). 'nonaltoptions' only options to the primary item. Anyway, it is working for me. Thanks.

---


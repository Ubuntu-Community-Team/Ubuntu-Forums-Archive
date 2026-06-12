---
title: "Burg Verbose boot"
date: 2011-01-06
forum: General Help
---

### Post by hiever1 on 2011-01-06
When I use burg to theme Grub it enters Ubuntu in verbose boot? I've tried fixing it by using startupmanger, no go.

---

### Post by stinkeye on 2011-01-06
```
gksudo gedit /etc/default/burg
```

and uncomment or add the line (line 7 in my file)
(ie remove the # symbol from the start of that line.)
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Then run...
```
sudo update-burg
```

---

### Post by hiever1 on 2011-01-06
That didnt help.

---

### Post by stinkeye on 2011-01-07
> **hiever1 said:**
> That didnt help.

If that didn't help, explain exactly what you mean by 
> enters Ubuntu in verbose boot

---

### Post by dcstar on 2011-01-07
> **stinkeye said:**
> If that didn't help, explain exactly what you mean by

$5 says it is just the Plymouth splash screen not loading.

---

### Post by hiever1 on 2011-01-07
> **dcstar said:**
> $5 says it is just the Plymouth splash screen not loading.

Yup, but I have a whole bunch of text at startup.  Which is verbose boot, right?

---

### Post by stinkeye on 2011-01-07
Do you see the burg loading screen.

---

### Post by QLee on 2011-01-07
[QUOTE=hiever1]When I use burg to theme Grub it enters Ubuntu in verbose boot? I've tried fixing it by using startupmanger, no go.[/QUOTE]

Just for clarity, you didn't use burg to theme GRUB, you replaced GRUB with BURG, it is the bootloader you are now using.

---

### Post by stinkeye on 2011-01-07
Thanks, Clarence. :rolleyes:

---

### Post by hiever1 on 2011-01-07
Yes. How do I get my Plymouth splash screen back?

---

### Post by stinkeye on 2011-01-07
Theres a few solutions but this works for me.
```
 gksudo gedit /etc/default/burg
```

and look for a line 
```
GRUB_GFXPAYLOAD_LINUX=
```

Uncomment or add the line using your desktop resolution.
eg my line reads..
```
GRUB_GFXPAYLOAD_LINUX="[COLOR="Magenta"]1680x1050[/COLOR]"
```


This should show your desktop resolution
```
xdpyinfo | grep "dimensions:"
```


Lastly run...
```
sudo update-burg
```

---

### Post by hiever1 on 2011-01-07
> **stinkeye said:**
> Theres a few solutions but this works for me.
```
 gksudo gedit /etc/default/burg
```and look for a line 
```
GRUB_GFXPAYLOAD_LINUX=
```Uncomment or add the line using your desktop resolution.
eg my line reads..
```
GRUB_GFXPAYLOAD_LINUX="[COLOR=Magenta]1680x1050[/COLOR]"
```
This should show your desktop resolution
```
xdpyinfo | grep "dimensions:"
```

It has nothing to do with desktop resolution.

---

### Post by stinkeye on 2011-01-07
OK.
I think I've got something better to do.
):P

---

### Post by hiever1 on 2011-01-07
> **stinkeye said:**
> OK.
I think I've got something better to do.
):P

No, please!

---

### Post by stinkeye on 2011-01-07
--

---

### Post by dcstar on 2011-01-07
> **hiever1 said:**
> When I use burg to theme Grub it enters Ubuntu in verbose boot? I've tried fixing it by using startupmanger, no go.

There is a new Burg Manager tool that may fix up things:

[http://www.unixmen.com/software/1072-burg-manager-install-and-configure-burg-the-easy-way](http://www.unixmen.com/software/1072-burg-manager-install-and-configure-burg-the-easy-way)

---


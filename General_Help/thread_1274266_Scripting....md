---
title: "Scripting..."
date: 2009-09-24
forum: General Help
---

### Post by exploreRPG on 2009-09-24
I am new to ubuntu and linux and am having trouble understanding the terminal & scripting. It seems to be similar to perl, but I can't get a grasp of the commands and syntax..

For example This script runs when copied to a terminal prompt but fails when inserted into a .sh and ran.

  for DEVICE in /sys/bus/usb/devices/*; do
    [ -f $DEVICE/product ] && cat $DEVICE/product
    [ -f $DEVICE/idProduct ] && cat $DEVICE/idProduct
    [ -f $DEVICE/idVendor ] && cat $DEVICE/idVendor
  done

Specifically what is the -f parameter? - It seems like a very cryptic language, so any explanation will help.

I am having difficulty finding devices...

---

### Post by ibuclaw on 2009-09-24
> **exploreRPG said:**
> I am new to ubuntu and linux and am having trouble understanding the terminal & scripting. It seems to be similar to perl, but I can't get a grasp of the commands and syntax..

For example This script runs when copied to a terminal prompt but fails when inserted into a .sh and ran.

  for DEVICE in /sys/bus/usb/devices/*; do
    [ -f $DEVICE/product ] && cat $DEVICE/product
    [ -f $DEVICE/idProduct ] && cat $DEVICE/idProduct
    [ -f $DEVICE/idVendor ] && cat $DEVICE/idVendor
  done

Specifically what is the -f parameter? - It seems like a very cryptic language, so any explanation will help.

I am having difficulty finding devices...

I have no issues running it...

```

#!/bin/sh

for DEVICE in /sys/bus/usb/devices/*; do
    [ -f $DEVICE/product ] && cat $DEVICE/product
    [ -f $DEVICE/idProduct ] && cat $DEVICE/idProduct
    [ -f $DEVICE/idVendor ] && cat $DEVICE/idVendor
done

```

the **-f** switch tests that the next argument exists and is a regular file.

The trick with if statements in bash is that you must not think of [ ] as brackets. **[** is a command that works exactly like **test** except that the last commandline argument must be **]** for syntactical sugar reasons.

```
[ -f $DEVICE/product ] && cat $DEVICE/product;
```
is exactly the same as
```
test -f $DEVICE/product && cat $DEVICE/product;
```

Regards
Iain

---


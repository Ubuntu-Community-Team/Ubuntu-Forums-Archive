---
title: "help with a script"
date: 2011-06-28
forum: General Help
---

### Post by Avidanborisov on 2011-06-28
In a big script of mine I need to execute the following command:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label "grub" --loader "\\EFI\\grub\\grub.efi"
```
using some variables from the script. but when executing this code (Here is a sample of what this section in the script should do):
```
#!/bin/bash
set -x -e
GRUB2_UEFI_NAME="grub"
EFISYS_PART_DEVICE="$(grub-probe --target=device /boot/efi/efi/grub/grub.efi)"
EFISYS_PARENT_DEVICE=${EFISYS_PART_DEVICE:0:8}
EFISYS_PART_NUM=${EFISYS_PART_DEVICE:8:1}
sudo efibootmgr --create --gpt --disk ${EFISYS_PARENT_DEVICE} --part ${EFISYS_PART_NUM} --write-signature --label ${GRUB2_UEFI_NAME} --loader "\\EFI\\${GRUB2_UEFI_NAME}\\${GRUB2_UEFI_NAME}.efi"
```
Will execute efibootmgr as this:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader '\EFI\grub\grub.efi'
```
but what I need is that here:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature **--label grub** --loader '\EFI\grub\grub.efi'
```
It will have brackets before and after grub.
And here
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader **'\EFI\grub\grub.efi'**
```
it will look like: (with brackets and two slashes).
```
**"\\EFI\\grub\\grub.efi"**
```
I tried many variations but really don't know how should I execute it in the script so it will look like I described.

---

### Post by erind on 2011-06-28
Try to add two more backslashes, and another pair of escaped double-quotes:

```
sudo efibootmgr --create --gpt --disk ${EFISYS_PARENT_DEVICE} --part ...  --loader "\"[COLOR=Red]\\[/COLOR]\\EFI[COLOR=Red]\\[/COLOR]\\${GRUB2_UEFI_NAME}[COLOR=Red]\\[/COLOR]\\${GRUB2_UEFI_NAME}.efi\""
``````
$ GRUB2_UEFI_NAME="grub"
$ set -x
$ echo "\"\\\\EFI\\\\${GRUB2_UEFI_NAME}\\\\${GRUB2_UEFI_NAME}.efi\""
+ echo '"\\EFI\\grub\\grub.efi"'
"\\EFI\\grub\\grub.efi"
$
```

---

### Post by Avidanborisov on 2011-06-28
> **erind said:**
> Try to add two more backslashes, and another pair of escaped double-quotes:

```
sudo efibootmgr --create --gpt --disk ${EFISYS_PARENT_DEVICE} --part ...  --loader "\"[COLOR=Red]\\[/COLOR]\\EFI[COLOR=Red]\\[/COLOR]\\${GRUB2_UEFI_NAME}[COLOR=Red]\\[/COLOR]\\${GRUB2_UEFI_NAME}.efi\""
``````
$ GRUB2_UEFI_NAME="grub"
$ set -x
$ echo "\"\\\\EFI\\\\${GRUB2_UEFI_NAME}\\\\${GRUB2_UEFI_NAME}.efi\""
+ echo '"\\EFI\\grub\\grub.efi"'
"\\EFI\\grub\\grub.efi"
$
```

That will give me the following output:
```
sudo efibootmgr --create ... --loader [COLOR="Red"]'[/COLOR]"\\EFI\\grub\\grub.efi"[COLOR="Red"]'[/COLOR]
```
I don't need the single brackets before the brackets.

---

### Post by Avidanborisov on 2011-06-28
Also, what about the brackets before and after grub?

---

### Post by KoolPenguin on 2011-06-28
When I try your code this is the output I get:

efibootmgr --create --gpt --disk /dev/sdb --part 1 --write-signature --label grub --loader \EFI\grub\grub.efi

What are you exactly trying to achieve?

Best

--
Chris

---

### Post by Avidanborisov on 2011-06-28
> **KoolPenguin said:**
> When I try your code this is the output I get:

efibootmgr --create --gpt --disk /dev/sdb --part 1 --write-signature --label grub --loader \EFI\grub\grub.efi

What are you exactly trying to achieve?

Best

--
Chris

Well when I am executing this code:
```
sudo efibootmgr --create --gpt --disk ${EFISYS_PARENT_DEVICE} --part ${EFISYS_PART_NUM} --write-signature --label ${GRUB2_UEFI_NAME} --loader \\\\EFI\\\\${GRUB2_UEFI_NAME}\\\\${GRUB2_UEFI_NAME}.efi
```
the output will be:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader [COLOR="Red"]'[/COLOR]\\EFI\\grub\\grub.efi[COLOR="Red"]'[/COLOR]
```
Bash will insist to include these one character brackets before and after, and I need that to be without them.

I am trying to achieve this:
```
sudo efibootmgr --create --gpt --disk /dev/sda --part 1 --write-signature --label grub --loader \\EFI\\grub\\grub.efi
```

---

### Post by Avidanborisov on 2011-06-28
Also I forgot to mention that I have tested and I don't need any brackets at all so it will look like I posted above.

---

### Post by the-ridikulus-rat on 2011-06-29
> **Avidanborisov said:**
> Also I forgot to mention that I have tested and I don't need any brackets at all so it will look like I posted above.

Hey man, What KoolPenguin mentioned is how it should come out. The reason 2 backward slashes are added is that the first backward slash escapes the next one so that the actual path comes out to be

```

\EFI\grub\grub.efi

```

instead of 

```

EFIgrubgrub.efi

```

The double backward slashes is for the shell. The path that should be passed to efibootmgr should be \EFI\grub\grub.efi , not \\EFI\\grub\\grub.efi . Anyway try the latest script at [https://github.com/skodabenz/My_Shell_Scripts/blob/master/grub2/grub2_uefi.sh](https://github.com/skodabenz/My_Shell_Scripts/blob/master/grub2/grub2_uefi.sh) .

---


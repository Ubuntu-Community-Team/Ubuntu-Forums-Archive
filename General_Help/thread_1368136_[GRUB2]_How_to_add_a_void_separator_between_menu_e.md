---
title: "[GRUB2] How to add a void separator between menu entries (???)"
date: 2009-12-30
forum: General Help
---

### Post by RodGer GR on 2009-12-30
Hello. I'm trying to add a line between some of my boot menu entries (between linux and memtest and between memtest and other OS's). So I created two files in the /etc/grub.d directory named 15_separator and 25_separator and I also remembered to make them executable.

The content of these files is like this:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "-----------------------------------------------------------------"{
    saved_entry=${chosen}
    save_env saved_entry
}
```and this:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "-------------------------Automatically detected OS's--------------------------"{
    saved_entry=${chosen}
    save_env saved_entry
}
```Of course, I also remembered to 'sudo update-grub' after creating the custom entries with the separators.

Is there something I do wrong ??? cause nothing changed in my boot menu. Any hint would be appreciated. Thanks in advance.

---

### Post by RodGer GR on 2009-12-30
There must really be somebody who knows grub2 that well. I know there is.

:lolflag:Hey, you there, yes, you the guru. Can you please help here a little ?

---

### Post by meierfra. on 2009-12-31
If the first character in the title is a "-",  grub treads the title as an argument, resulting in an "unknown argument" error.

So just use

```
menuentry " ------------------------------------------------------" {
any_thing 
}
```

---

### Post by MestreLion on 2010-12-30
> **RodGer GR said:**
> 
```

menuentry "-----------------------------------------------------------------"{
    saved_entry=${chosen}
    save_env saved_entry
}
```

What are the "saved_entry" and "save_env" entries for? What do they do? 

I currently use "echo 'Select an option'" as the content for my fake entries. It works, but its an awful, ugly workaround.

Any ideas on how to make the separtors actions as unobtrusive as possible is really appreciated!

---

### Post by joeborder on 2011-01-22
I was just looking on how to do this myself and the method you Have at the moment works. I think your issue is that you are running update-grub after you edit the file, which automatically writes the grub.cfg again and removes what you have entered

---

### Post by MestreLion on 2011-01-22
To fully customize the menu while still allowing update-grub to run and NOT ruin my hard work, here's what i do:

- Before making changes, i update-grub once, so my /boot/grub/**grub.cfg** is updated with the lastest OSes and options (memtest, recovery, windows, etc)
```
sudo update-grub
```- Copy and paste all entries i want from the generated /boot/grub/**grub.cfg** to /etc/grub.d/**40_custom** (or, in some grub versions, /boot/grub/**custom.cfg** can also be used intead)
```
gedit /boot/grub/grub.cfg /etc/grub.d/40_custom &
```- The relevant entries are usuallly betwen these lines:
### BEGIN /etc/grub.d/10_linux ### and ### END /etc/grub.d/10_linux ### (Linuxes)
 ### BEGIN /etc/grub.d/20_memtest86+ ### and ### END /etc/grub.d/20_memtest86+ ### (memtest)
### BEGIN /etc/grub.d/30_os-prober ### and ### END /etc/grub.d/30_os-prober ### (Windows)

- Edit and modify them at will in **40_custom **(customized OS names, separators, "Main OS" and "Recovery Options" grouping, remove uselss metest serial console, etc)

- A **very** important change is: in Linuxes entries, change the kernel and initrd from /boot/vmlinuz-x.x.x-xxxx to their symlinks at /. This way the OS will always boot to latest kernel version,  so you dont need to update grub everytime you update kernel version. Kernel updates atumatically change the symlinks to point to latest one. So, change:

```
linux /boot/vmlinuz-2.6.32-21-generic
initrd /boot/initrd.img-2.6.32-21-generic

```to

```
linux /vmlinuz
initrd /initrd.img
```Same can be done with "(recovery mode)" entries.

As for the previous kernel, you can use linux **/vmlinuz.old** and **/initrd.img.old**

- Another useful modification is to add a **savedefault** option in each entry. This way grub will remember the last used choice, and use it as default for next boot (useful when you want several reboots using windows)

- Disable /etc/grub.d/10_linux , 20_memtest and 30_osprobe files, by turning off their executable bit, so future grub-updates wont re-create the automatic entries in grub.cfg
```
cd /etc/grub.d
sudo chmod -x 1* 2* 3*
```If anyone wants, i can post my current 40_custom file after all the customizations and the end result.

Hope that helps!

---

### Post by MestreLion on 2011-02-11
> **joeborder said:**
> I was just looking on how to do this myself and the method you Have at the moment works. I think your issue is that you are running update-grub after you edit the file, which automatically writes the grub.cfg again and removes what you have entered

Im **not** editing /boot/grub/grub.cfg, im editing **/etc/grub.d/40_custom**, which is the proper file to add customizations so update-grub will not remove.

As for the fake separator, i discovered another workaround.:

```
menuentry ' '{
     true
}
```You can still "select" it, but if you press ENTER, screen will only blink, and nothing will happen. **Important: if you want the label to be blank, or you want to add a " ----- NOTE ----" that begins with "-", use a blank space as the 1st character, or the entry wont work at all**. 

The old solution was:
```
menuentry ' '{
     echo "Please select an option"
}
```When chose, it shows this a blank screen with the message along with "Press any key to continue" and then return to the menu.

---


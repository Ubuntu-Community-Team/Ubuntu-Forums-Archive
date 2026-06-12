---
title: "Windows being opened in a loop"
date: 2011-02-09
forum: General Help
---

### Post by Rodayo on 2011-02-09
I just turned on my desktop a little earlier and it's doing this weird thing, where file-manager windows start appearing in the panel(the one that shows your open programs) and it just keeps going for infinity. None of the windows actually pop up or anything either. 

Using the system monitor, I figured it must be nautilus because it's hogging up a lot of cpu...

---

### Post by dino99 on 2011-02-09
sudo shutdown now -R

---

### Post by Rodayo on 2011-02-09
> **dino99 said:**
> sudo shutdown now -R
 
I tried a restart already. It's a lowercase r btw

---

### Post by matt_symes on 2011-02-09
Hi

Open a terminal and type

```
nautilus -c
```

Does that return any errors ?

Have you tried reinstalling nautilus ?

Kind regards

---

### Post by Rodayo on 2011-02-09
> **matt_symes said:**
> Hi

Open a terminal and type

```
nautilus -c
```Does that return any errors ?

Have you tried reinstalling nautilus ?

Kind regards

I seem to be getting one error, but I don't know what to make of it
> Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory

(nautilus:18106): Gtk-WARNING **: Unable to locate theme engine in module_path: "mist",
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container

---

### Post by matt_symes on 2011-02-09
Hi

> Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory

(nautilus:18106): Gtk-WARNING **: Unable to locate theme engine in module_path: "mist"

I am not sure if that is the problem but i don't get that on mine

> matthew@matthew-laptop:~$ nautilus -c
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
matthew@matthew-laptop:~$ 

Can you post the output of

```
ls -l /usr/lib/gtk-2.0/modules/
```

That is a small L above.

Are there any nautilus errors in your ~/.xsession-errors file ?

You could just reinstall nautilus and see if that fixes it (nut i think that may be more in hope).

Kind regards

---

### Post by Rodayo on 2011-02-09
> **matt_symes said:**
> Hi



I am not sure if that is the problem but i don't get that on mine

 

Can you post the output of

```
ls -l /usr/lib/gtk-2.0/modules/
```That is a small L above.

Are there any nautilus errors in your ~/.xsession-errors file ?

You could just reinstall nautilus and see if that fixes it (nut i think that may be more in hope).

Kind regards

I reinstalled nautilus and for some reason my desktop just went fubar. It logged me out. When I try to log back in it just took me back to the login screen again. I tried other accounts including root. Nothing worked.

I'm reinstalling my OS right now...

---

### Post by matt_symes on 2011-02-09
Hi

Sorry about that :( There was obviously a major underlying problem there. I certainly did not expect that to happen just by reinstalling nautilus. Hopefully you're not too mad at me.

Kind regards

---


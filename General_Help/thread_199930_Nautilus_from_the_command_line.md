---
title: "Nautilus from the command line"
date: 2006-06-19
forum: General Help
---

### Post by bohboh on 2006-06-19
How do i open nautilus from the command line and have it open at a specified directory?

I want to do:

me@mymachine> nautilus  "/home/me/dir1/dir2/"

and have it open at "/home/me/dir1/dir2/".

It opens but then immediately closes.

Thanks

---

### Post by Half-Left on 2006-06-19
Should be nautilus --no-desktop /home/me/dir

---

### Post by bohboh on 2006-06-19
[QUOTE=Half-Left]Should be nautilus --no-desktop /home/me/dir[/QUOTE]

Still no joy. Even tried --no-default-window. Exactly the same.

---

### Post by johnc4510 on 2006-06-19
I really don't understand, I can open any file folder with nautilus at the command line, as in the example below:

nautilus /usr/share/pixmaps

This takes me right to the folder.

---

### Post by bohboh on 2006-06-19
This definately doesnt work. The window appears then dissapears. Must be something wrong here but i cant think what.

---

### Post by Najand on 2006-06-19
Why don't you check nautilus using:> nautius -c and see if everything is fine or not?

---

### Post by bohboh on 2006-06-19
Did, got:

```

running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory

```

Still doesnt work. What other file explorers can i try? Is this a problem confined to nautilus? What other programs can i execute from the command line to see if this is an issue across all programs.

---

### Post by AirRaven on 2006-06-19
[QUOTE=bohboh]Did, got:

```

running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory
running nautilus_self_check_file_utilities
running nautilus_self_check_file_operations
running nautilus_self_check_directory
running nautilus_self_check_file
running nautilus_self_check_icon_container
running nautilus_self_check_icon_factory

```

Still doesnt work. What other file explorers can i try? Is this a problem confined to nautilus? What other programs can i execute from the command line to see if this is an issue across all programs.[/QUOTE]
Try Konqueror or Thunar, if you have Kubuntu-desktop or xubuntu-desktop installed.

---

### Post by bohboh on 2006-06-19
Konqueror works, but the command line hangs until i close konqueror. Can i do it so i can continue to type into the console?

---

### Post by scxtt on 2006-06-19
try

[indent]$:> konqueror &[/indent]

and

[indent]$:> nautilus ~[/indent]

worked fine for me ...

---

### Post by bohboh on 2006-06-19
Thanks everyone for your help. After the toil and trouble of trying x, y and z. I managed to get it to work, i needed to reboot after an update and behold doing nautilus "/path/" worked. 

Again, thanks, much appreciated!

:p :p :p

---


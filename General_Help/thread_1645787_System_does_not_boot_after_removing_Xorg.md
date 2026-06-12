---
title: "System does not boot after removing Xorg"
date: 2010-12-15
forum: General Help
---

### Post by beyondwithinitself on 2010-12-15
Running Ubuntu 10.10 on a Sony Vaio VGN-NR430E laptop.

My system had been running noticeably slow lately, so I decided to poke around the system monitor and see what was eating my resources.  Xorg peaked at around 50% cpu, so I decided (in a rash decision) to remove it.

Went to Syanptic Package Manager -> completely remove all "Xorg server" packages
( was alerted that Xorg itself would have to be reinstalled for this to happen, "OK" ).  After Syanptic finished, I looked back to the System Monitor and saw Xorg still there, still eating CPU.  Out of frustration, I selected "End Process".  Big mistake: haven't been able to get back in since.

The grub loader still works so I can switch between kernel versions and "recovery" mode, but a normal boot simply takes me to a black screen.  I tried sudo apt-get update from Recovery mode, only to get an error when connecting to the repositories.  Any ideas?

---

### Post by NCLI on 2010-12-15
> **beyondwithinitself said:**
> Running Ubuntu 10.10 on a Sony Vaio VGN-NR430E laptop.

My system had been running noticeably slow lately, so I decided to poke around the system monitor and see what was eating my resources.  Xorg peaked at around 50% cpu, so I decided (in a rash decision) to remove it.

Went to Syanptic Package Manager -> completely remove all "Xorg server" packages
( was alerted that Xorg itself would have to be reinstalled for this to happen, "OK" ).  After Syanptic finished, I looked back to the System Monitor and saw Xorg still there, still eating CPU.  Out of frustration, I selected "End Process".  Big mistake: haven't been able to get back in since.

The grub loader still works so I can switch between kernel versions and "recovery" mode, but a normal boot simply takes me to a black screen.  I tried sudo apt-get update from Recovery mode, only to get an error when connecting to the repositories.  Any ideas?

Do you have any idea what Xorg *is*??

---

### Post by afrodeity on 2010-12-15
You should still be able to boot up in recovery mode. (press shift) and chose option. Boot, then see more options, there should be one to reinstall xorg, otherwise boot normally or drop down to console, reinstall xorg"

```

sudo apt-get install --reinstall xorg
```

---

### Post by beyondwithinitself on 2010-12-15
A google search led me to believe it was for servers (which I presumed my machine is not)... 

I'm hoping this isn't quite on par with trying to delete c:/windows

---

### Post by beyondwithinitself on 2010-12-15
> **afrodeity said:**
> You should still be able to boot up in recovery mode. (press shift) and chose option. Boot, then see more options, there should be one to reinstall xorg, otherwise boot normally or drop down to console, reinstall xorg"

```

sudo apt-get install --reinstall xorg
```

As I remember, the "normal boot" from Recovery also yielded a black screen, but my memory has betrayed me before.. I will give this a shot.

---

### Post by NCLI on 2010-12-15
> **beyondwithinitself said:**
> A google search led me to believe it was for servers (which I presumed my machine is not)... 

I'm hoping this isn't quite on par with trying to delete c:/windows
Not quite, but close. Xorg is a display server, that means it is responsible for actually drawing what you see on your screen. What you describe is entirely expected if you remove the display server. 

You'll have to plugin your laptop with an ethernet cable, then run ```
sudo apt-get install xserver-xorg
```

---

### Post by beyondwithinitself on 2010-12-15
> **NCLI said:**
> Not quite, but close. Xorg is a display server, that means it is responsible for actually drawing what you see on your screen. What you describe is entirely expected if you remove the display server. 

You'll have to plugin your laptop with an ethernet cable, then run ```
sudo apt-get install xserver-xorg
```

This fixed everything for me. :KS :KS :KS  

Thank you !  :popcorn:

---

### Post by NCLI on 2010-12-15
> **beyondwithinitself said:**
> This fixed everything for me. :KS :KS :KS  

Thank you !  :popcorn:

Always a pleasure ;)

In the future, remember to investigate any packages thoroughly before removing them ;)

---

### Post by amsterdamharu on 2010-12-15
I thought xorg is only for the desktop (graphic programs). Pressing control + alt + F1 would still take you to tty1 which is text only (tty1 to 6 I believe are text only corresponding to F1 through F6)

---


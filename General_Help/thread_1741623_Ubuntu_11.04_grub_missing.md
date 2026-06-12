---
title: "Ubuntu 11.04 grub missing"
date: 2011-04-28
forum: General Help
---

### Post by renke86 on 2011-04-28
I had Windows 7 and Kubuntu 10.10 on separate hard drives. I replaced the Kubuntu with the Ubuntu Natty.
When I boot where the grub screen used to be my monitor only writes "*input not supported*", and after a few seconds Ubuntu starts.

How can I get the grub screen back?

---

### Post by Sinopa on 2011-04-28
I'm having the same problem.
Tried to change the resolution in grub to 800x600, but that didn't work :(

---

### Post by Sinopa on 2011-04-28
Think I solved it.

I edited grub again, but this time I changed the resolution to 1024x768. 

GRUB_GFXMODE=1024x768

and it worked for me :)

---

### Post by Sinopa on 2011-04-28
Don't forget to update grub afterwards :)

---

### Post by renke86 on 2011-04-29
OK I'm really newbie, exactly witch file have to I edit?

---

### Post by Sinopa on 2011-04-29
> **renke86 said:**
> OK I'm really newbie, exactly witch file have to I edit?

Open a terminal and write:

```
sudo gedit /etc/default/grub
```

It will ask for your password.

Once you have opened grub, find the line that says 

#GRUB_GFXMODE=640x480 and change it to 
GRUB_GFXMODE=1024x768 

(remember to remove # sign)

Save and type in terminal 

```
update-grub
```

then reboot.

That's it :)

---

### Post by renke86 on 2011-04-29
And it works. Thanks for your help:D

---

### Post by kelver69 on 2011-05-01
This should be a sticky.

Thanks Sinopa!!

---

### Post by carloquinto66 on 2011-05-02
HELP ME PLEASE, I DID THE CHANGE ON THE RESOLUTION BUT WHEN I TRY TO DO THE  UPADTE THIS IS THE MESSAGE : gedit:1715): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
carlos@carlos-T3646:~$ update-grub
grub-mkconfig: You must run this as root

HOW CAN I DO???  THANKS A LOT

---

### Post by Sinopa on 2011-05-14
> **carloquinto66 said:**
> HELP ME PLEASE, I DID THE CHANGE ON THE RESOLUTION BUT WHEN I TRY TO DO THE  UPADTE THIS IS THE MESSAGE : gedit:1715): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
carlos@carlos-T3646:~$ update-grub
grub-mkconfig: You must run this as root

HOW CAN I DO???  THANKS A LOT

Do what it says. Run it as root. Just add **sudo** before the command.

---

### Post by Ranimator on 2011-05-21
This was very helpful and solved my problem as well. 

THANKS!!!

---

### Post by John Coulthard on 2011-06-04
Thank you - worked for me. (I got and ignored the warning messages).

---

### Post by Jerry Story on 2011-11-01
After:
sudo gedit /etc/default/grub

In these lines in grub:

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

What would happen if I change it like so:

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

Would it screw the computer so it can't boot?

Would it change from graphical to text and bypass all graphical problems and show grub?

---

### Post by Jerry Story on 2011-11-02
> **Jerry Story said:**
> After:
sudo gedit /etc/default/grub

In these lines in grub:

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

What would happen if I change it like so:

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

I tried it (and of course, sudo update-grub)and it worked. I got grub. Previously I did not get grub.

---


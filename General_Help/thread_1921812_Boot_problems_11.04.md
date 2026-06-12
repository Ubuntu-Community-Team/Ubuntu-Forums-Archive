---
title: "Boot problems 11.04"
date: 2012-02-07
forum: General Help
---

### Post by moustii on 2012-02-07
Hey

I'm having trouble booting in to ubuntu. At first I couldn´t install ubuntu because there was something wrong with my boot parameters I changed these (on installation from live cd). But after installation and rebooting these sittings were sett back to default. 

Can somebody tell me how to change the setting in the boot menu. I´m not sure which commands to use.


On installation I changed the parameters 
noapic
nolapic
and deleted quiet splash--

---

### Post by lechien73 on 2012-02-07
The temporary - per session - fix would be to:

[LIST]
[*]Reboot your PC and - after the self-test screen - hold down the Shift key so that the Grub menu appears.
[*]Press **e** to edit the Grub command line.
[*]After where it says "quiet splash", add or delete your other boot parameters
[*]Press **Ctrl-X** to boot
[/LIST]
To make it permanent, open a terminal window and type the following:

```
gksu gedit /etc/default/grub
```

This will prompt you for your password and then open a text editor with a complex-looking file open.

Scroll down to the line that reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

Add your other boot parameters between the quotes - and delete *quiet splash* if you so wish.

Save the file and quit from the text editor.

Now, at the command prompt, type:

```
sudo update-grub
```

That will make the changes permanent, and you won't have to add it each time you boot.

---

### Post by moustii on 2012-02-07
> **lechien73 said:**
> The temporary - per session - fix would be to:

[LIST]
[*]Reboot your PC and - after the self-test screen - hold down the Shift key so that the Grub menu appears.
[*]Press **e** to edit the Grub command line.
[*]After where it says "quiet splash", add or delete your other boot parameters
[*]Press **Ctrl-X** to boot
[/LIST]
To make it permanent, open a terminal window and type the following:

```
gksu gedit /etc/default/grub
```This will prompt you for your password and then open a text editor with a complex-looking file open.

Scroll down to the line that reads:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```Add your other boot parameters between the quotes - and delete *quiet splash* if you so wish.

Save the file and quit from the text editor.

Now, at the command prompt, type:

```
sudo update-grub
```That will make the changes permanent, and you won't have to add it each time you boot.

Thanks!!! It finally works :)

---

### Post by lechien73 on 2012-02-07
You're welcome - glad it's sorted :)

If you get chance, could you please use the **Thread Tools** menu above the first post and mark the issue as [SOLVED]?

Thanks

---


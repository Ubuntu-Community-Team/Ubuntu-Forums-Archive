---
title: "installed new kernel now x wont start"
date: 2006-04-15
forum: General Help
---

### Post by bunnieofdoom on 2006-04-15
tryed reinstalling nvidia drivers and it said they were allready updated.
ran dpkg-reconfigure on xserver and still same result. 
any thoughts?

---

### Post by johnc4510 on 2006-04-15
Try:
sudo nvidia-glx-config enable
Note: Only if glx is the driver you installed

---

### Post by bunnieofdoom on 2006-04-15
ok it says it cont load modual nvidia or nv (from modprob) help please? heh

---

### Post by johnc4510 on 2006-04-15
Try:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-kernel-commom
sudo nvidia-glx-config enable

---

### Post by bunnieofdoom on 2006-04-15
sudo apt-get install nvidia-glx <--------allready newest version
sudo apt-get install nvidia-kernel-commom <---- allready newest version
sudo nvidia-glx-config enable <----------- does nothing when typed in text mode

---

### Post by johnc4510 on 2006-04-15
Sorry, the only other thing I know to try is:ctrl>alt>backspace to restart. 
Maybe someone else will help.

---

### Post by trent dillman on 2006-04-15
By 'x won't start' do you mean GDM gives an error on a blue screen?

If so, there should be an error message.

Also, try looking through /var/log/Xorg.0.log and look for errors there.

---

### Post by bunnieofdoom on 2006-04-15
yes it says 
Fatal cant load module nvidia 

modprob says module nvidia is not installed same for nv

---

### Post by dcstar on 2006-04-15
[QUOTE=bunnieofdoom]tryed reinstalling nvidia drivers and it said they were allready updated.
ran dpkg-reconfigure on xserver and still same result. 
any thoughts?[/QUOTE]
What "new kernel"?

If it was an official Ubuntu one, then the updated drivers should also be available, if it is one you have compiled yourself, then all bets are off.........

---

### Post by trent dillman on 2006-04-15
Try using the 'vesa' driver until you get this worked out.

You should try completely removing nvidia-glx, then installing it again...

---

### Post by bunnieofdoom on 2006-04-15
its 2.6.16

---

### Post by trent dillman on 2006-04-15
Snap. You installed a custom kernel, eh?

OK, uninstall nvidia-glx. Then, boot as normal. Say ok to the blue screens.

When you get to the console, log in and do this:

```
sudo -s
/etc/init.d/gdm stop
wget http://download.nvidia.com/XFree86/Linux-x86/1.0-8756/NVIDIA-Linux-x86-1.0-8756-pkg1.run
sh NVIDIA-Linux-x86-1.0-8756-pkg1.run -a -e
```

Use defaults until::

When it asks about lib directories, change

```
/usr/X11R6
``` to ```
/usr/lib/xorg
```
and
```
/usr/lib/xorg/lib/modules
``` to ```
/usr/lib/xorg/modules
```

Defaults after that, and everything should be ok...

```
/etc/init.d/gdm start ; exit
```

---

### Post by bunnieofdoom on 2006-04-15
thanks that fixed ill have to commit that to memory :)

---

### Post by trent dillman on 2006-04-15
No problem...

...I had to do that before I reinstalled Flight 6

---


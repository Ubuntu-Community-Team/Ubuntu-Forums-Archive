---
title: "How to bypass Grub"
date: 2009-12-19
forum: General Help
---

### Post by drchohan on 2009-12-19
I have dual boot system WindowsXP and Windows7. Then I installed Ubuntu 9.10 inside windows 7. After installation, when computer boots up I have three options to boot
1. Earlier Version of Windows
2. Windows 7
3. Ubuntu
When I select windows 7 or earlier Version of windows, they straight away boot without showing anyother screens. Where as, if I select Ubuntu option. Grub boot loader appears with its own options. 
I want ubuntu to boot, straight like, Windows7 or WindowsXP. 
I donot know how to hide/deactivate Grub? So that grub doesn't appear and Ubuntu goes to its login screen straight. 
Can anyone help me out?
Thankyou in advance. 
Cheers

---

### Post by yoyoned on 2009-12-19
Did you install ubuntu using wubi?

---

### Post by philinux on 2009-12-19
> **drchohan said:**
> I have dual boot system WindowsXP and Windows7. Then I installed Ubuntu 9.10 inside windows 7. After installation, when computer boots up I have three options to boot
1. Earlier Version of Windows
2. Windows 7
3. Ubuntu
When I select windows 7 or earlier Version of windows, they straight away boot without showing anyother screens. Where as, if I select Ubuntu option. Grub boot loader appears with its own options. 
I want ubuntu to boot, straight like, Windows7 or WindowsXP. 
I donot know how to hide/deactivate Grub? So that grub doesn't appear and Ubuntu goes to its login screen straight. 
Can anyone help me out?
Thankyou in advance. 
Cheers

You need to edit this file /etc/default/grub

```
gksu /etc/default/grub
```

Edit line 7.
GRUB_TIMEOUT="10"

Change the timeout to say 1 and then save the file.

then run

```
sudo update-grub
```

---

### Post by joes7 on 2009-12-19
startup manager is your friend.

---

### Post by drchohan on 2009-12-19
> **yoyoned said:**
> Did you install ubuntu using wubi?

Thanks for reply, 

Yes, I used Wubi to install Ubuntu in Windows7

---

### Post by Leppie on 2009-12-19
> **philinux said:**
> ```
gksu //etc/default/grub
```

Edit line 7.
GRUB_TIMEOUT="10"

Change the timeout to say 1 and then save the file.

then run

```
sudo update-grub
```

did you edit your grub configuration?
```
gksudo gedit /etc/default/grub ##gksudo maybe gksu on some systems. replace gedit with whatever editor you prefer (e.g. gvim, leafpad, mousepad, etc.)
```

change the line GRUB_TIMEOUT="10" to something like GRUB_TIMEOUT="1"
this will still show you the grub menu, but only for 1 second (which will leave you the possibility to enter the grub shell if required).
then update the grub configuration:
```
sudo update-grub
```

---

### Post by drchohan on 2010-02-19
Thankyou Lepie, 
 
gksu //etc/default/grub 
 
didn;t work with my system but the second one you wrote
 
gksudo gedit /etc/default/grub works without hasle. After editing grub I ran
 
sudo update-grub
 
and thats it!
 
It suits me very well. 
 
Again Thankyou!

---


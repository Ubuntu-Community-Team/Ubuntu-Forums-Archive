---
title: "Cannot see how to edit GRUB using Terminal"
date: 2010-07-18
forum: General Help
---

### Post by Enigmaman on 2010-07-18
I am using Ubuntu 10.04 and would like to change the default O/S in GRUB. I have found an old thread telling me to run the command: 

sudo gedit /boot/grub/menu.lst 

I have done so but the resulting file seems to be empty. 

Can anyone please help?    

Thanks.

---

### Post by wojox on 2010-07-18
Try

```
gksudo gedit /etc/default/grub
```

---

### Post by AndyCinDallas on 2010-07-18
You could also install Startup-Manager if you don't like working in Terminal and prefer a GUI-based option.

After install, you'll find it under System -> Administration -> Startup-Manager

---

### Post by Mark Phelps on 2010-07-18
> **Enigmaman said:**
> I am using Ubuntu 10.04 and would like to change the default O/S in GRUB. I have found an old thread telling me to run the command: 

sudo gedit /boot/grub/menu.lst 

I have done so but the resulting file seems to be empty. 

Can anyone please help?    

Thanks.

That "old thread" is no good anymore because 10.04 GRUB2 does NOT use that file.

You have to edit the /etc/default/grub file and change the number in the default line to match the entry number of the entry you want to boot by default.

---

### Post by Enigmaman on 2010-07-18
Thanks for these helpful replies. I can now access the relevant file.

Mark, when you mention changing the number in the default line, are you referring to the list of options in the boot menu - i.e. if Windows is the eighth item in the list, should I enter the number 8?

Also at the top of the file I can see the message: 

"If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg."

How would I do this?

---

### Post by wojox on 2010-07-19
Just run to update:

```
sudo update-grub
```

---


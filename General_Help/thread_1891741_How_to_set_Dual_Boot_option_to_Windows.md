---
title: "How to set Dual Boot option to Windows"
date: 2011-12-06
forum: General Help
---

### Post by DaleD55 on 2011-12-06
Hi Everyone

I have a PC with Windows XP & Ubuntu 11.10 on it.

I love using Ubuntu but my wife would rather use Windows!!

How do I set the computer so that it automatically boots up in Windows instead of Ubuntu

Thanks in advance 

Dale

---

### Post by didinium on 2011-12-06
Unless you uninstall ubutu you will always have thee option at the begining, it won't be able to boot to either ubuntu or windows automatically.

---

### Post by DaleD55 on 2011-12-06
Thanks for the reply - I seem to remember on an earlier version of Ubuntu that in the system settings there was a Start Up box which allowed you to set either Windows or Ubuntu

I can't seem to find this in the  new version of Ubuntu

---

### Post by BC59 on 2011-12-06
To change the default booting system you have to install from Ubuntu Software Center the application Startup Manager. Then you open it and there is an option to change the order of which system is booting first. You can change the waiting time as well. The default is 10 sec but if your wife likes to use windows you can change it to something like 2 sec of waiting.

---

### Post by enterdavertex on 2011-12-06
you should try installing windows firstly , and secondly try to think about upgrading your win OS  to Windows 7. Windows xp support ends in a short period of time . And after everything is done install Ubuntu.

---

### Post by DaleD55 on 2011-12-06
Thanks for the advice

I checked up in the Software Centre and found Startup manager - but it is saying that it is already installed

I can't seem to find it anywhere

---

### Post by BC59 on 2011-12-06
Push the upper left corner the **Dash** and then right to the search box, Startup. The icon should be there.

---

### Post by BC59 on 2011-12-06
You should not confuse the Startup Disk Creator with the Startup Manager.

---

### Post by DaleD55 on 2011-12-06
I've found it now thanks but the strange thing is it's showing that it will boot to windows first & it doesn't -

---

### Post by BC59 on 2011-12-06
In that case you have to do it the hard way.

Check here if this guide can help you:

> How to make XP boot up as the default OS with Grub2

[http://www.youtube.com/watch?v=wOZwiwNWJzo](http://www.youtube.com/watch?v=wOZwiwNWJzo)

---

### Post by amalafrida on 2011-12-06
Isn't this simply a matter of sudo-editing /etc/default/grub and setting
GRUB_DEFAULT=x where x is the zero-base o/s that is listed in /boot/grub/grub.cfg?

then sudo update-grub.

a.

---

### Post by DaleD55 on 2011-12-06
Thanks again

It looks a bit too complicated for me - I think we will just have to carry on as we are for the moment

---

### Post by BC59 on 2011-12-06
I suggest you, if you are not sure you can do it, just leave it as it is, because dealing badly with Grub Menu, could cause the whole system to crash.

---

### Post by stinkeye on 2011-12-06
You could do this with grub-customizer.
To install copy/paste these commands one at a time into the terminal.
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Then open the dash and start typing in grub-customizer.

Once opened, click on the preferences button and choose your Windows install
from the **Default Entry > Predefined** dropdown.
Select from the right hand column... ie by name.

Then close that window and hit the save button.
Done.

---


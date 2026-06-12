---
title: "Restore GNU Grub Default Colors."
date: 2012-06-08
forum: General Help
---

### Post by UAdnan on 2012-06-08
Hello guys,

I have recently messed up with Plymouth on Ubuntu 12.04, despite that I haven't seen on any website that it works on this version on Ubuntu, I did it, and it worked fine, I rebooted and made sure.

But then I wanted to get more themes, there was only those in the list...

So there's a mistake I've made, (I can't really tell, if it's so important I'll try to recall it) I ended up with a black login screen (In fact, I had no login options, just a black screen after the splash one which took hours to finish up) and a X shaped cursor, that I can move around with my mouse.

Great, after some researches I fixed that, I can get to login with no problem, the Ubuntu is working fine.

But there's something up there. I remember very well that the dual boot screen ( I use the Ubuntu's one ) was always purple, but it after the stuff I made it became black and white, and that's sad, I prefer purple.

I know that this issue is not that necessary but let me fix it, please !

Oh, and, how am I going to get more themes for plymouth without messing it up again ? 

Thanks,
UAdnan.

---

### Post by wilee-nilee on 2012-06-08
I would just purge and reinstall grub from the ubuntu desktop to get it back to stock again.

```
sudo apt-get purge grub-pc grub-common
```
```
sudo apt get install grub-pc grub-common
```
When asked where you want grub it is in the mbr only use the space key to tick this.

The mbr is sdX the X being the HD no partition numbers.

Custom background I have no idea about.

---

### Post by UAdnan on 2012-06-08
The restoring of Grub didn't solve any problem, it just modified the  resolution of the splash screen ( I guess it returned back to default). But "the screen where you choose the OS to boot with" (Just to make it easier) is still black and white. IT WAS PURPLE !

And, I have no idea what you wrote after the last code.

---

### Post by drs305 on 2012-06-08
I believe the purple background color originates from the /etc/grub.d/05_debian_theme script, which looks a /lib/plymouth/themes/default.grub file.

See if you have the following in these files:
```
grep plymouth -A3 /etc/grub.d/05_debian_theme 
```
> 	if [ -e /lib/plymouth/themes/default.grub ]; then
		sed "s/^/${1}/" /lib/plymouth/themes/default.grub
	fi


```
cat /lib/plymouth/themes/default.grub
```
> if background_color 44,0,30; then
  clear
fi

If you get an error using the above command it could be the file does not exist.

```
grep background_color /boot/grub/grub.cfg
```
> ### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi

If you aren't using a theme, don't have an image file in /boot/grub and aren't using the 'console' mode these lines should produce the purple background.

---

### Post by wilee-nilee on 2012-06-08
> **UAdnan said:**
> The restoring of Grub didn't solve any problem, it just modified the  resolution of the splash screen ( I guess it returned back to default). But "the screen where you choose the OS to boot with" (Just to make it easier) is still black and white. IT WAS PURPLE !

And, I have no idea what you wrote after the last code.

drs305 is your best source here in this area altogether.

---

### Post by drs305 on 2012-06-08
> **wilee-nilee said:**
> drs305 is your best source here in this area altogether.


Well, I actually saw this thread earlier but I thought your recommendation to purge/reinstall would work. In fact, I am not sure why it didn't unless there is an image file remaining in /boot/grub or the default.grub plymouth file doesn't exist after messing with Plymouth.

---

### Post by UAdnan on 2012-06-09
I followed your instructions, and everything went well. 
Except that the second code you've written was incorrect, wasn't it ? I just replaced it with sudo gedit ...

The file was missing, and the two last lines in the quote, I added them.

Thank you for your support.

---

### Post by drs305 on 2012-06-09
> **UAdnan said:**
> I followed your instructions, and everything went well. 
Except that the second code you've written was incorrect, wasn't it ? I just replaced it with sudo gedit ...

The file was missing, and the two last lines in the quote, I added them.

Thank you for your support.

Actually I only provided troubleshooting commands and hadn't given remedial steps as yet, but you figured that out on your own. :-)

If everything is resolved, please mark the thread SOLVED via the Thread Tools link near the top right of the first post.

Happy Ubuntu-ing!

---


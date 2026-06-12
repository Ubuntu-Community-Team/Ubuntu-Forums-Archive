---
title: "command line brightness adjustment?"
date: 2010-11-27
forum: General Help
---

### Post by princeofnam on 2010-11-27
Since switching to AWN I've noticed there to be no brightness applet with the program or AWN-extras.  I might have to rest to the terminal to adjust the brightness.  I've tried 

> **echo -n 100 > /proc/acpi/video/VGA/LCD/brightness**

with no success

---

### Post by zapaces on 2010-11-29
Same problem here.
I love AWN, but I can't believe there's no brightness applet.
Would love to have a command line command or an applet for awn.

---

### Post by matt_symes on 2010-11-29
Hi

> Since switching to AWN I've noticed there to be no brightness applet  with the program or AWN-extras.  I might have to rest to the terminal to  adjust the brightness.  I've tried 

 	Quote:
 	 	 		 			 				**echo -n 100 > /proc/acpi/video/VGA/LCD/brightness** 			 		 	 	 
with no success

I do not use awn, but i was able to change the brightness at the command line. What is did was

sudo -i

to enter a root shell

echo -n 100 > /proc/acpi/video/VGA1/LCD/brightness

to set the brightness to max. Notice i had to use VGA1 and not VGA. What error messages were you getting?

Kind regards

---


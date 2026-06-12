---
title: "Rotate Screen, not running X windows"
date: 2009-07-18
forum: General Help
---

### Post by Q345 on 2009-07-18
Hello,

I'm booting into the command line, not running X windows.  Is there a way to rotate the screen (command line)?   :confused:

---

### Post by LightningCrash on 2009-07-18
> **Q345 said:**
> Hello,

I'm booting into the command line, not running X windows.  Is there a way to rotate the screen (command line)?   :confused:

Should be possible via fbcon
> 
	4. fbcon=rotate:<n>
	
	        This option changes the orientation angle of the console display. The
	        value 'n' accepts the following:
	
		      0 - normal orientation (0 degree)
		      1 - clockwise orientation (90 degrees)
		      2 - upside down orientation (180 degrees)
		      3 - counterclockwise orientation (270 degrees)
	
		The angle can be changed anytime afterwards by 'echoing' the same
		numbers to any one of the 2 attributes found in
		 /sys/class/graphics/fbcon
	
			rotate     - rotate the display of the active console
			rotate_all - rotate the display of all consoles
	
		Console rotation will only become available if Console Rotation
		Support is compiled in your kernel.
	
		NOTE: This is purely console rotation.  Any other applications that
		use the framebuffer will remain at their 'normal'orientation.
		Actually, the underlying fb driver is totally ignorant of console
		rotation.


ie:
sudo -s
echo 1 > /sys/class/graphics/fbcon/rotate_all
exit


or put `echo 1 > /sys/class/graphics/fbcon/rotate_all` in your /etc/rc.local

---

### Post by Q345 on 2009-07-18
Thanks LC,

I should have mentioned that I'm running eeebuntu.  I was hoping there was some generic way to do it.  I guess I'll have to figure out how to compile a custom eeebuntu kernel.  There's no fbcon under the /sys/class/graphics/ directory.


added the following to /etc/rc.local:

modprobe fbcon
echo 1 > /sys/class/graphics/fbcon/rotate_all

Doesn't appear to be doing anything though...

---

### Post by LightningCrash on 2009-07-18
you may have to comment out your video card in /etc/modprobe.d/blacklist-framebuffer


oh, and check dmesg for framebuffer / fbcon related entries
i seem to remember having to set a grub kernel boot param like video=vesa or some jazz.

---

### Post by Q345 on 2009-07-19
Update:

I commmented out intelfb in/etc/modprobe.d/blacklist-framebuffer.  If I pass vga=791 as a kernel parameter it errors but gives me an option to select different VGA and VESA modes (800x600x32). After it boots there's a /sys/class/graphics/fb0/rotate file.  I commented out the modprobe fbcon line in /etc/rc.local and changed the line with the echo to echo 1 > /sys/class/graphics/fb0/rotate. 
It seems to be getting closer but the screen is blank. Hopefully I'm on the right track. Any thoughts?

Thanks for the help! :D

OK - It seems I need to leave the fbcon stuff in rc.local. If I leave fbcon, and do the vga= stuff above, then dmesg | grep frame has some stuff about vesa that isn't otherwise listed.

vesafb: framebuffer...
and
fb0: VESA VGA frame buffer device...

In /sys/class/graphics there's fb0 and fbcon but the echo stuff doesn't produce any changes still.

---

### Post by LightningCrash on 2009-07-19
wish I could help you more, but I've never actually set up fbcon myself :D

sounds like you're getting closer, though.

---

### Post by Q345 on 2009-07-19
Well, thanks for all your help.  I'll keep experimenting and post the results if I figure it out.
:D

---


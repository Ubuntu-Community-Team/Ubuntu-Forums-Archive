---
title: "Problems setting default brightness with /etc/rc.local"
date: 2012-09-23
forum: General Help
---

### Post by totitoll on 2012-09-23
Hey,

I can change my display brightness in the file /sys/class/backlight/intel_backlight/brightness with the command "echo x > /sys/class/backlight/intel_backlight/brightness" were x is a certain brightness level. 
I want to use this command to set a default brightness level for every reboot since the actual one is much to bright.

The above command doesnt work right away, as I found out I first have to change the permissions for /sys/class/backlight/intel_backlight/brightness.
I did this with "sudo chmod a+w" (don't know if that's the right way, but it works...?). 
But these permissions aren't permanent, when i reboot they're gone, so i tried the following: 

I added to /ect/rc.local the two lines (opened with gksudo gedit ...):

chmod a+w /sys/class/backlight/intel_backlight/brightness
echo 134 > /sys/class/backlight/intel_backlight/brightness                              #(*)

in order to achieve what I described ahead.

But this doesn't work as it sure changes the file permissions (I can use the command "echo x > /sys/.../backlight" afterwards without any "permissions denied"-output),
but the actual command, which i denoted #(*) doesn't get executed, so my display stays bright, if I don't change it "by hand".

For any recommendations thank you very much in advance!

---

### Post by totitoll on 2012-09-23
solved it: I added a "sleep 1"  in between the two lines in rc.local, now it works :)
Can someone explain why this is so?

but there's another problem now: 

No matter on which level I set brightness in the above way (=changing the value in the file brightness), if I use then the Fn-Keys to adjust brightness it always jumps again to full brightness (on startup) or the level I just adjusted to with the Fn-keys beforehand. That is annoying. Is there any way to "synchonize" the current Fn-Key brightness level with the one in the file (I have a Sony Vaio z11x9e with Ubuntu 12.04)?

---

### Post by totitoll on 2012-09-23
ok now I should try first and then write, but here is what is found out now:

if i take 
/sys/class/backlight/acpi_video1/brightness
instead of  
/sys/class/backlight/intel_backlight/brightness
it is indeed syncronized with the Fn-Keys.

Now again there is a but: Now not even the first command is executed on boot
I have:
chmod a+w /sys/class/backlight/acpi_video1/brightness
sleep 1
echo 1 > /sys/class/backlight/acpi_video1/brightness

on the other hand typing "sudo /etc/rc.local start" works...


By the way: there are actually three folders in /sys/class/backlight/ namely acpi_video0, acpi_video1 and intel_backlight. The file ....acpi_video/brightness is the only one of those three which changes it's values if I hit the Fn-Keys. So for what are these other two anyway?

---

### Post by dcstar on 2012-09-24
> **totitoll said:**
> solved it: I added a "sleep 1"  in between the two lines in rc.local, now it works :)
Can someone explain why this is so?


Because rc.local can be run before the other services (like X) have started. It may only be a fluke that it works due to the randomness of the times each service takes to fire up.

---

### Post by totitoll on 2012-09-27
ah if someone else has the problem:

putting the sleep in front(!) works:

 sleep 1
 chmod a+w /sys/class/backlight/acpi_video0/brightness
 chmod a+w /sys/class/backlight/acpi_video1/brightness
 chmod a+w /sys/class/backlight/intel_backlight/brightness
 echo 191 >/sys/class/backlight/intel_backlight/brightness
 echo 1 >/sys/class/backlight/acpi_video0/brightness
 echo 1 >/sys/class/backlight/acpi_video1/brightness

sometimes it's hard to see the obvious...;)

---


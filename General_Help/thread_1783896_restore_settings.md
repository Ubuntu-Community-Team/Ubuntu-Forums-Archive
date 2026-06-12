---
title: "restore settings"
date: 2011-06-16
forum: General Help
---

### Post by VVAW on 2011-06-16
Last night I upgraded to 11.04 from 10.10

1.i have 2 issues first I can't do the cube on add driver is says this
You need to install this driver if you wish to use the Unity desktop, enable desktop effects, or run software that requires 3D acceleration, such as some games.
I can't find a way to enable them.

2.Trying to enable the cube I messed something up and now there is no  close minimize at the top of windows How do convert back to oringnal settings

---

### Post by VVAW on 2011-06-16
i need  help on this after playing with somemore now it boots up in command line.
I really like to recover this but I can't how can I get a file and copy it to a usb drive through command line.

So I can reinstall the OS


PLEASE HELP ME ON THIS

---

### Post by seawolf167 on 2011-06-16
What did you do when "playing with it"? What error messages do you get on boot? What settings did you change? etc.

The drivers the message was referring to were the graphics driver which are available by hitting the Ubuntu button and typing in "Additional Drivers"

---

### Post by VVAW on 2011-06-16
I went to metacity theme and then 
I change something in compiz icon

My screen went blank SO i rebooted and now it boots to a command line interface..

---

### Post by seawolf167 on 2011-06-16
What happens if you enter the following commands

```
startx
---or---
sudo service gdm restart
```

---

### Post by VVAW on 2011-06-16
1 command
xiint giving up
xinit unable to connect t X server connection refused
xinit server erros

Fatal server error no screens found

2 command
I get 
gdm start/running, process 2496

---

### Post by VVAW on 2011-06-16
here is what is say when I boot 

intel ips 0000:00:1f.6: failed to get i915 symbol graphics turbo disabled.

24.941121 drm mouveau 0000:01:00.0 pointer to bit loadval table invalid 

ubuntu 11.04 name tty1

name login:

---

### Post by VVAW on 2011-06-16
is this fixable or do I need to re-install OS.
if so I can a copy a file to a usb drive via the command line

or how can I access it in window7 64 bit

---

### Post by VVAW on 2011-06-16
finally got back into through safe mode I enabled indirect rendering that is when it went south

---

### Post by VVAW on 2011-06-16
So I am back were I started How to I restore compiz settings back to default settings.

Here is a pictures when I try to enable drivers 

everything worked fine on 10.10

---

### Post by VVAW on 2011-06-16
Fixed all of my issues after upgrade to get my cube back working
I followed this
[http://www.youtube.com/watch?v=lVR1y9cJHWA](http://www.youtube.com/watch?v=lVR1y9cJHWA)

to reset my compiz settings I went into ubuntu tweak 
Desktop applications compiz and clicked reset 

reboot followed youtube video all is good now2

---


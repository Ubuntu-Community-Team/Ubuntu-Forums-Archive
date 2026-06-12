---
title: "S-vido cable not working on ubuntu 11.04"
date: 2011-08-21
forum: General Help
---

### Post by Mikeybz2 on 2011-08-21
I have my TV connected through my laptop via an S-cable. It worked will on the previous versions of Ubuntu. I really like the new user interface and how it works with my TV any help would be great.

---

### Post by realzippy on 2011-08-21
run
```
xrandr -q
```
and post output

---

### Post by Mikeybz2 on 2011-08-22
mike-dida@mikedida-Satellite-A105:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
TV1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0* 
   800x600        30.0  
mike-dida@mikedida-Satellite-A105:~$

---

### Post by realzippy on 2011-08-22
As you can see,the TV is connected.
Is it a laptop?
=> Fn +F4 or F8

---

### Post by Mikeybz2 on 2011-08-22
Yes, I have tried pressing the fn keys since i have to use that when i connect to a monitor. When I do it for the tv the laptop screen goes blank and nothing shows up on the tv. i can see the tv screen jumping like there is a signal but it doesn't get any picture. On the previous version of ubuntu i did not even have to push the button it just came up

---

### Post by realzippy on 2011-08-22
what happens when running

```
xrandr --auto --output TV1 --mode 640x480 --right-of LVDS1
```


which TV model is it?

---

### Post by Mikeybz2 on 2011-08-22
I tried the code and nothing really happens. I know the TV is connected because i can see the picture on the TV when the computer starts up. its just as soon as Ubuntu loads it goes back to the laptop screen and wont go on the TV. maybe there is an older driver i need to use i have a Toshiba laptop with Intel graphics

---

### Post by realzippy on 2011-08-23
Which intel graphics?

```
lspci | grep VGA
```

Which kernel?

```
uname -a
```

Which TV model (already asked ;-) ) ?

---


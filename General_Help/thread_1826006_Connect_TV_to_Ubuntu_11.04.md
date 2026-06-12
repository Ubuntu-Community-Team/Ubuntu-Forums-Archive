---
title: "Connect TV to Ubuntu 11.04"
date: 2011-08-16
forum: General Help
---

### Post by bhogal on 2011-08-16
Hello,

I have connected my Samsung TV to Ubuntu 11.04 via VGA Cable. It all works, but the problem is that on the TV screen its 2 cm to the right. 

I don´t have an option on the TV like on the monitors to move right or left or Auto adjust. 

I have also tired under Monitor in System Settings, No Option and also under nVidia. 

Can some suggest what to do?

---

### Post by HermanAB on 2011-08-16
Try the program called 'xrandr'.  Read the man page for details.

---

### Post by bhogal on 2011-08-16
Thank you HermanAB, 

I still have the same problem.

---

### Post by bhogal on 2011-08-16
How to move to left.

This is what I get

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 0mm x 0mm
   1360x768       50.0*    51.0     52.0  
   1024x768       53.0     54.0     55.0  
   832x624        56.0  
   800x600        57.0     58.0     59.0  
   720x450        60.0  
   680x384        61.0     62.0  
   640x480        63.0     64.0     65.0     66.0     67.0     68.0  
   576x432        69.0  
   512x384        70.0     71.0     72.0  
   416x312        73.0  
   400x300        74.0     75.0     76.0  
   320x240        77.0     78.0     79.0

I have also tired this command xrandr -o left

---


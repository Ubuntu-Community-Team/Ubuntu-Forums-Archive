---
title: "Trying to install 915 resolution... =/"
date: 2010-06-30
forum: General Help
---

### Post by Mi11z on 2010-06-30
Okay so here is where i'm at any help would be greatly appreciated and the reason i'm installing 915 resolution is because i need to get a custom resolution (my proper correct resolution) for the BURG kernel loader. heres a command line paste of where i'm at with the problem:

```
mi11z@Samsung-R610:~$ sudo aptitude install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
No candidate version found for 915resolution
No candidate version found for 915resolution
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

``` 

cheers, and thank you. :)

---

### Post by gvernold on 2010-06-30
As far as I know 915resolution is no longer in the repos because it isn't needed. With the newer versions of Xorg there is no xorg.conf either but you can still create one if you need to and customize the resolution you need in your custom xorg.conf.

---

### Post by Mi11z on 2010-06-30
> **gvernold said:**
> As far as I know 915resolution is no longer in the repos because it isn't needed. With the newer versions of Xorg there is no xorg.conf either but you can still create one if you need to and customize the resolution you need in your custom xorg.conf.

Gonna need a little more please...?

---

### Post by davidmohammed on 2010-06-30
just type

xrandr 

for all resolutions your PC supports.

---

### Post by Mi11z on 2010-06-30
> **davidmohammed said:**
> just type

xrandr 

for all resolutions your PC supports.

Here:

```
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0* 
   1360x768       51.0  
   1024x768       52.0     53.0  
   960x540        54.0  
   840x525        55.0  
   832x624        56.0  
   800x600        57.0     58.0     59.0     60.0     61.0  
   800x512        62.0  
   720x450        63.0  
   720x400        64.0  
   700x525        65.0  
   680x384        66.0     67.0  
   640x512        68.0     69.0  
   640x480        70.0     71.0     72.0     73.0     74.0  
   640x400        75.0  
   640x350        76.0  
   576x432        77.0     78.0     79.0     80.0     81.0     82.0     83.0  
   512x384        84.0     85.0     86.0     87.0     88.0  
   416x312        89.0  
   400x300        90.0     91.0     92.0     93.0     94.0  
   360x200        95.0  
   320x240        96.0     97.0     98.0     99.0  
   320x200       100.0  
   320x175       101.0  

```

---

### Post by davidmohammed on 2010-06-30
looks like your native resolution is the one with the * against it.  Looks like a widescreen display - correct?

---

### Post by Mi11z on 2010-06-30
> **davidmohammed said:**
> looks like your native resolution is the one with the * against it.  Looks like a widescreen display - correct?

yes

---


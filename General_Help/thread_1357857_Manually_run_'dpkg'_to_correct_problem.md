---
title: "Manually run 'dpkg' to correct problem"
date: 2009-12-17
forum: General Help
---

### Post by cdo on 2009-12-17
While trying to install a dpk package i had a power loss . After getting back on and going to Synaptic Package Manager i get this message :

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I assume this means run in terminal mode but when i type in 'dpkg--configure-a' i get the following :

bash: E:: command not found
alan@alan-desktop:~$ E: _cache->open() failed, please report.

Can someone please explain to me what i need to do here ? First off i don't know how to report the problem . I have also tried apt-get remove and apt-get update with the same message .  :confused:


Thanks

---

### Post by Leppie on 2009-12-17
the command to launch is:
```
$dpkg --configure -a
```
as opposed to what you seem to have typed:
```
$dpkg--configure-a
```
(you didn't type the spaces in between the command and the options).
You also need to use "sudo" with this command for admin access:
```
$sudo dpkg --configure -a
```

and you have to close synaptic and/or update-manager (if active) whilst running dpkg

---

### Post by cdo on 2009-12-17
> **Leppie said:**
> the command to launch is:
```
$dpkg --configure -a
```as opposed to what you seem to have typed:
```
$dpkg--configure-a
```(you didn't type the spaces in between the command and the options).
You also need to use "sudo" with this command for admin access:
```
$sudo dpkg --configure -a
```


Ok , that cleared the Package Manager and it does say i have a broken package so i went to Settings > Filters > Broken and checked off the broken box . Am i done or need to fix the broken package and if so how do i locate it ?

---


---
title: "Creating disc image-file problem"
date: 2009-08-27
forum: General Help
---

### Post by niiize on 2009-08-27
Hi
Im trying to create a image from a CD with cat command. At first I can hear the CD starts to spin, but after 30 secs or so it interrupts with the message "input/output fault"
Might add, the iso-file does get created in the folder before it interrupts.

thnx

---

### Post by XCan on 2009-08-27
Why are you trying to do it with cat, I'm not sure that cat can make an exact copy of a CD. Wouldn't you be better of using dd, i.e., 

```
 dd if=/dev/cdrom of=/home/user/cd.iso 
```

I think that the above will only work if your CD is unmounted first, but I'm a bit unsure, it will be obvious if you decide to try it.

---

### Post by niiize on 2009-08-27
Great thnx

---

### Post by SoftwareExplorer on 2009-08-27
> **XCan said:**
> Why are you trying to do it with cat, I'm not sure that cat can make an exact copy of a CD. Wouldn't you be better of using dd, i.e., 

```
 dd if=/dev/cdrom of=/home/user/cd.iso 
```

I think that the above will only work if your CD is unmounted first, but I'm a bit unsure, it will be obvious if you decide to try it.

You can also go to Places->Computer. Right click on the Cd and click copy. Go to properties and save the file where you want and make sure to set it to save as an iso. Click Copy once you have everything set up and it should work.

---

### Post by XCan on 2009-08-28
Ah, look at that, even easier. Thanks for the tip SE. :)

---


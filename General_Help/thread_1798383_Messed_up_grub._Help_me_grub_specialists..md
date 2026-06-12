---
title: "Messed up grub. Help me grub specialists."
date: 2011-07-06
forum: General Help
---

### Post by kanishkdudeja on 2011-07-06
i installed windows 7 after ubuntu 11.04..dual booting both..

and lost ubuntu from the boot menu..

followed the first method in this guide..

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

but unfortunately installed grub in the wrong disk..

i had to do it in /dev/sda1 and by mistake did it to /dev/sda6..

i did it again..and now installed it to the right drive..

but now when i boot my pc,

it says 

```
error:file not found
grub rescue > 

```

what should i do now?

i want to recover both ubuntu 11.04 and windows 7.

---

### Post by seawolf167 on 2011-07-06
Take a look at [this link]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2"), follow the instructions under "Copy Live CD Files", and substitute in your correct partition.

Once you get GRUB reinstalled and booted into Ubuntu, open a terminal and type in the following

```
sudo apt-get install os-prober
sudo update-grub
```

And it should find your Windows loader.

---

### Post by kanishkdudeja on 2011-07-07
okay. i will try it.

---

### Post by Mr Nemo on 2011-07-07
I used the same method you initially used. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I believe that you have to set it to /dev/sda without any numbers.

I'm pretty sure that's how I fixed mine.

---

### Post by kanishkdudeja on 2011-07-07
@Mr Nemo: i get what ure saying. i did the same. but i put the wrong tag. by tag i mean

```
/media/***********/
```

to find grub in..i put the wrong location of the drive in which ubuntu was installed by using the wrong tag..

by the way i fixed the problem using boot repair tool..

thanks..:) 

@seawolf167: thanks :)

---

### Post by hdiaz on 2011-07-07
> **kanishkdudeja said:**
> @Mr Nemo: i get what ure saying. i did the same. but i put the wrong tag. by tag i mean

```
/media/***********/
```to find grub in..i put the wrong location of the drive in which ubuntu was installed by using the wrong tag..

by the way i fixed the problem using boot repair tool..

thanks..:) 

@seawolf167: thanks :)

nice job! 
what boot repair tool did you use?

---

### Post by kanishkdudeja on 2011-07-07
@hdiaz: 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mr Nemo on 2011-07-07
Ah I see. Good job on the fix.

---

### Post by kanishkdudeja on 2011-07-07
Thanks :)

---

### Post by seawolf167 on 2011-07-07
> **kanishkdudeja said:**
> 

by the way i fixed the problem using boot repair tool..

thanks..:) 

@seawolf167: thanks :)

Awesome, glad it worked!

---

### Post by kanishkdudeja on 2011-07-07
:)

---


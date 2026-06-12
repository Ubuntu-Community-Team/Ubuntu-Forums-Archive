---
title: "inexperienced user needs help copying locked files"
date: 2012-05-07
forum: General Help
---

### Post by juliancam on 2012-05-07
Hi all.  I have 12.04 on my laptop and 11.10 on an external hard drive. I want to copy the background images from 11.10 to 12.04 but of course they are locked to root. Therefore I have been trying to use the "sudo cp" command to do it but I keep getting blocked. I can cd down to the usr/share folder on the external hd but when I try "sudo cp /backgrounds  /usr/share/backgrounds" to copy the folder over to the laptop, I get an error:- cp omitting backgrounds.

Obviously I am doing something wrong but what? All I want to do is copy the old 11.10 background images into the new 12.04 background folder. Do I need to specify the files in the background folder and if so is there a catchall suffix? Am I not specifying the destination folder well enough? I am booting from the laptop but have also tried booting the external hd.

(ps I may not be able to check in on this post for a day or two so please be patient if you need more information)

Julian

---

### Post by mmesantos1 on 2012-05-07
You can boot into 11.10 then copy backgrounds to USB thumb driver then boot into 12.04 and copy them from the thumb drive to the 12.04 install. Just a thought. ;)

---

### Post by steeldriver on 2012-05-07
> **juliancam said:**
> Do I need to specify the files in the background folder and if so is there a catchall suffix? 

Yes, use the file wildcard '*', also if you are trying to copy a directory below your current directory the path should not start with / (which means the root of the filesystem)

$ sudo cp backgrounds/*  /usr/share/backgrounds

You may want to add the -p switch to replicate the file permissions, i.e.

$ sudo cp -p backgrounds/*  /usr/share/backgrounds

---

### Post by juliancam on 2012-05-07
> **mmesantos1 said:**
> You can boot into 11.10 then copy backgrounds to USB thumb driver then boot into 12.04 and copy them from the thumb drive to the 12.04 install. Just a thought. ;)

:oops: I hadn't thought of that but if I had I would assume the same locked out restrictions would apply.

However

[QUOTE=Steeldriver]$ sudo cp -p backgrounds/* /usr/share/backgrounds [/QUOTE]

that worked just fine thank you. It even didn't replicate the Contest folder whatever that is. One more lesson learnt thank you just an infinite number to go :(.

Julian

---

### Post by steeldriver on 2012-05-07
ok that's good

for future reference, if you *did* want it to recursively copy any subdirectories, you can add the -r (or -R) option:

```
$ sudo cp -**R**p backgrounds/* /usr/share/backgrounds
```

---


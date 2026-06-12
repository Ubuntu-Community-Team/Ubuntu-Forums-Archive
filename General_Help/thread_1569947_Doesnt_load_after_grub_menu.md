---
title: "Doesnt load after grub menu"
date: 2010-09-07
forum: General Help
---

### Post by fusky on 2010-09-07
hello to all , Recently i have been getting this problem when i boot up i will get 3 different ubuntu options and my windows 7 option,when i try to boot into my latest version in the grub menu it will go to it go to a black screen and just hang there ,i will have to manually restart and do it 1 or 2 more times before it will actually begin to boot into ubutnu 10.04.I hope any one can enlighten me on this problem thanks.

---

### Post by garvinrick4 on 2010-09-07
> **fusky said:**
> hello to all , Recently i have been getting this problem when i boot up i will get 3 different ubuntu options and my windows 7 option,when i try to boot into my latest version in the grub menu it will go to it go to a black screen and just hang there ,i will have to manually restart and do it 1 or 2 more times before it will actually begin to boot into ubutnu 10.04.I hope any one can enlighten me on this problem thanks.
Use one of the different kernels in your grub screen, kernel that having boot problems will
be replaced be newer kernel shortly. If you want to get rid of it go to synaptics and type it in like 2.6.35-25 or whatever the troubled one is and get rid of it. The generic and image and 2 headers.

---

### Post by fusky on 2010-09-07
> **garvinrick4 said:**
> Use one of the different kernels in your grub screen, kernel that having boot problems will
be replaced be newer kernel shortly. If you want to get rid of it go to synaptic and type it in like 2.6.35-25 or whatever the troubled one is and get rid of it. The generic and image and 2 headers.

Thanks i might try that out to see if that helps any ,i just never booted into the older ones cause i didn't know if doing so would cause issues with the new one or not,and is there way for ubuntu to automatically get rid of old kernals or is it that i have to remove manually through the synaptic manager?

---

### Post by garvinrick4 on 2010-09-07
> **fusky said:**
> Thanks i might try that out to see if that helps any ,i just never booted into the older ones cause i didn't know if doing so would cause issues with the new one or not,and is there way for ubuntu to automatically get rid of old kernals or is it that i have to remove manually through the synaptic manager?
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---


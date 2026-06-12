---
title: "Compiling PV_on_HVM drivers for Ubuntu"
date: 2010-05-26
forum: General Help
---

### Post by devpriya on 2010-05-26
Hi

I want to compile PV_on_HVM drivers for Ubuntu, which according to my understanding should involve -

1. Enabling XEN drivers compilation flag
2. Compiling a normal kernel (non-Xenified one)

Now I am new to Ubuntu so I am finding it hard to locate the correct flags!

I used 'make menuconfig' but there I see that the XEN drivers are already marked as 'm' or '*' which means they are scheduled to be compiled with the kernel or as a module, but then I don't find them in the current kernel!

So I am suspecting that there is some flag which gets set only when we compile a XENified kernel which allows these drivers to get compiled. I may be wrong here, but this is all I could infer!

Any tips or advice here would be really helpful for me, as I am stuck at a dead-end here!

FYI: I am compiling a kernel for x86_64 architecture

Thanks

---

### Post by dino99 on 2010-05-26
[http://www.google.fr/search?as_q=PV%2Bon%2BHVM%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=PV%2Bon%2BHVM%2Bubuntu&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by devpriya on 2010-05-26
Nope! This is not what I am looking for.

If you look at his config, vif=[' ']

I am able to run Ubuntu on HVM but the ethernet driver is not working, so I will have to compile the XEN PV driver to work on HVM.

That is something which is not there in the link which you have provided. Correct me if I am wrong.

---

### Post by dino99 on 2010-05-26
sorry i'm not used with xen, might googled around

---


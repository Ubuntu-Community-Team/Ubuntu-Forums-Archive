---
title: "Blank Screen at Boot 11.10"
date: 2012-03-12
forum: General Help
---

### Post by P.ap G on 2012-03-12
After the "Bios options" screen all I get is a blank screen , the Xubuntu screen flashes on very briefly 
before the log in page , has anyone else had this ? What is the cause , what is the cure ?
any help will be very welcome .

---

### Post by 2F4U on 2012-03-12
Please provide info about your hardware. It could be a graphics card issue, but without knowing more about your hardware it is difficult to provide help. Did you try the nomodeset kernel parameter (accessible through F6 in the grub menu)?

---

### Post by Suparious on 2012-03-12
yes, you may have to specify framebuffer options to the kernel if it is just that splash screen.

After you get the login box, can you login and use the terminal/dektop?

---

### Post by P.ap G on 2012-03-13
Hello ,

xubuntu with xfce is brilliant distro but this is the only time I have had this problem !

With this very laptop since it was new in 2007 I have used :
ubuntu , mandriva, fedora, lps, austrumi, kubuntu, pc-bsd, debian, pinguy, gnewsesnse 
and a few others but no problems with splash screen so it cannot be a hardware issue 
can it ? 
No problems with log in screen and no problems with terminal once a full vim was installed.

---

### Post by P.ap G on 2012-03-13
I have just re-booted onto a USB stick with xubuntu 11.10 installed , no probs. whatsoever
with splash.

I should add that the version on my HD was installed after being downloaded onto another USB , the m5sum was checked , then burned onto  a disk , I then , prior to installing checked the veracity of the
burned disk , md5 again.

---


---
title: "Aladdin eToken"
date: 2006-06-20
forum: General Help
---

### Post by john_markh on 2006-06-20
Hi all,
Do any one know how to use Aladdin eToken with Firefox under Ubuntu 6.06 ?
](*,)

---

### Post by john_markh on 2006-10-17
OK, I managed to do it.
First of all, I had to install OpenCT and OpenSC. By default, I couldn't use it because permitions were set to root user.
I changed permitions to allow all users to read and execute the /var/run/openCT .
After that, I was able to access the USB eToken.
Next step was to add PKCS#11 to Firefox. Easy...
So, now I can see the token in Firefox but when website should pop up authorization popup (I know it should as I used it in Windows for more that 2 years - even in Firefox after you install Aladdin's PKCS#11 library) I doesn't work.

---


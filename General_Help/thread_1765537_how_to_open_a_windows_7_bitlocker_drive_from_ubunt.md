---
title: "how to open a windows 7 bitlocker drive from ubuntu?"
date: 2011-05-23
forum: General Help
---

### Post by sohlinux on 2011-05-23
How can I open a usb stick which was locked with windows 7 bitlocker from ubuntu 11.04? I have the password but I cant see anywhere to enter it.


thx

---

### Post by satanselbow on 2011-05-23
bitlocker is a "protected" M$ technology that cannot be read/decrypted by linux systems...

---

### Post by sohlinux on 2011-05-23
> **satanselbow said:**
> bitlocker is a "protected" M$ technology that cannot be read/decrypted by linux systems...

oh in that case is there some other encryption which I could use which can be read by both m$ and linux?

---

### Post by satanselbow on 2011-05-23
Is there no google in your area?

[http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html](http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html)

---

### Post by sohlinux on 2011-05-23
> **satanselbow said:**
> Is there no google in your area?

[http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html](http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html)


thats why we have this forum, to share info isnt it? I could have googled it done and dusted but now this thread will come up on google too. how mad is that.

found this one on google, why dont I just skip this forum all together. hm

[http://www.aescrypt.com/](http://www.aescrypt.com/)

---

### Post by kanux on 2011-07-16
> **sohlinux said:**
> thats why we have this forum, to share info isnt it? I could have googled it done and dusted but now this thread will come up on google too. how mad is that.

found this one on google, why dont I just skip this forum all together. hm

[http://www.aescrypt.com/](http://www.aescrypt.com/)


Then there's :arrow: **Truecrypt  **[http://www.truecrypt.org/](http://www.truecrypt.org/)



[URL="http://www.truecrypt.org/"]
[/URL]

---

### Post by nooblot on 2012-03-30
> **satanselbow said:**
> Is there no google in your area?

[http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html](http://www.ubuntusolutions.org/2009/03/how-to-create-encrypted-usb-drive.html)


Page not found (404)

---

### Post by Dragonbite on 2012-03-30
> **kanux said:**
> Then there's :arrow: **Truecrypt  **[http://www.truecrypt.org/](http://www.truecrypt.org/)



[URL="http://www.truecrypt.org/"]
[/URL]

+1.. probably the best solution for encrypting anything!

---

### Post by jerome1232 on 2012-03-30
> **kanux said:**
> Then there's :arrow: **Truecrypt  **[http://www.truecrypt.org/](http://www.truecrypt.org/)



[URL="http://www.truecrypt.org/"]
[/URL]

+2, truecrypt is nice

---

### Post by sohlinux on 2012-10-10
> **satanselbow said:**
> bitlocker is a "protected" M$ technology that cannot be read/decrypted by linux systems...


[http://www.hsc.fr/ressources/outils/dislocker/download/](http://www.hsc.fr/ressources/outils/dislocker/download/)

---

### Post by roin_09 on 2013-03-25
> **sohlinux said:**
> oh in that case is there some other encryption which I could use which can be read by both m$ and linux?

I personally use **LUKS + FreeOTFE**, haven't tried Truecrypt so I cannot tell which one is better. 

LUKS is the Linux standard for HDD encryption, and you can mount and read such a partition from Windows (and even Mac, I think) using the FreeOTFE program.

The downside to this solution is that in Windows, starting with Vista, drivers are required to be digitally signed and FreeOTFE's are not, so in order for it to work they suggest a workaround which consists on booting Windows with the TESTSIGNING option turned on, which results in a tiny "Test Mode" watermark showing on the bottom right corner of the desktop, and possibly a more vulnerable system. They explain the steps to make this change in their site. Don't know if Truecrypt has this problem as well, or it works differently.

Finally, you could use Ubuntu's **Disk Utility** to format your flash drive with LUKS encryption, just make sure you have installed the **cryptsetup** package from the repos.

---


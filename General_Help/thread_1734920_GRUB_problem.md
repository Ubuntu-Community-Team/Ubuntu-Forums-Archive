---
title: "GRUB problem"
date: 2011-04-20
forum: General Help
---

### Post by liamgillespie on 2011-04-20
Hi, basically my problem is that after installing Windows 7 on a separate partition, I no longer have access to Ubuntu through the grub loader or any other means. So I am stuck on Windows.
What would be the best solution?

---

### Post by wilee-nilee on 2011-04-20
Boot a live Ubuntu cd and in the terminal run this command and post the output.
fdisk -lu

---

### Post by liamgillespie on 2011-04-20
Thanks, I'll try that.

---

### Post by drs305 on 2011-04-20
liamgillespie, welcome to the Ubuntu forums !

From the LiveCD download and run the boot info script. This will provide us with the above requested information and a lot more that may be needed.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Post the contents of the RESULTS.txt between 'code' tags, which you generate by pressing the # icon in the post's menubar.

Most likely Windows overwrote the MBR and all you have to do is mount your Ubuntu partition and reinstall Grub2, but we will know for sure once we see the RESULTS.txt.

---

### Post by liamgillespie on 2011-04-20
Thanks drs! I'll try and get that for you. Will this work if I boot from a USB? It's what I used to install in the first place.

---

### Post by drs305 on 2011-04-20
> **liamgillespie said:**
> Thanks drs! I'll try and get that for you. Will this work if I boot from a USB? It's what I used to install in the first place.

Yes it will, as long as it boots to a Desktop or command line where you can get and run the script.

---


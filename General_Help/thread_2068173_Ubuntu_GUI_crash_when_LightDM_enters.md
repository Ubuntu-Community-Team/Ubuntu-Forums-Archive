---
title: "Ubuntu GUI crash when LightDM enters"
date: 2012-10-08
forum: General Help
---

### Post by CesarOscar on 2012-10-08
This issue happened spounteniously, i don´t know what could have cause it as i wasn´t using the PC when it happened. I ruled out any messing around with the setting as the user doesn´t know how to enter the BIOS, doesn´t have the sudo password and was only using firefox and libreoffice when it happened.

After the plymouth sequence i get this error. [https://www.dropbox.com/s/uf1xdkqkw9alvcu/IMAG0252.jpg](https://www.dropbox.com/s/uf1xdkqkw9alvcu/IMAG0252.jpg)

And this option: [https://www.dropbox.com/s/tpivkgjkx2spa3v/IMAG0253.jpg](https://www.dropbox.com/s/tpivkgjkx2spa3v/IMAG0253.jpg)

I choose the first option and this happens, [https://www.dropbox.com/s/j7vrmls3vrkn545/IMAG0254.jpg](https://www.dropbox.com/s/j7vrmls3vrkn545/IMAG0254.jpg)
[https://www.dropbox.com/s/ywxax1by2sdgbsy/IMAG0255.jpg](https://www.dropbox.com/s/ywxax1by2sdgbsy/IMAG0255.jpg)

Nothing happens after that. The issue persist after rebooting. I choose the other options to see if anything happens, i either get back to option 1 or doesn´t show anything anormal. (I have pictures i someone wants to know)

What i found weird is that event though the error is possitioned in the chip, however ubuntu 10.04 and 12.04 run fine in a live CD [https://www.dropbox.com/s/ll9feljag8cpl0z/IMAG0276.jpg](https://www.dropbox.com/s/ll9feljag8cpl0z/IMAG0276.jpg) .

I saw that some people are having issues when LightDM has a non default wallpaper, but i use a default one.

Thanks in advance.

---

### Post by CesarOscar on 2012-10-09
It turns out that a tmp folder in /home/cesar was filling up my Hard Drive, making it, somehow, unable to boot to LightDM. Everything worked flawlessly after deleting the folder.

---


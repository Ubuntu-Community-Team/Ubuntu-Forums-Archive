---
title: "Windows 7 won't boot after Ubuntu 10.10 installation"
date: 2010-10-21
forum: General Help
---

### Post by ngoing001 on 2010-10-21
Just today I downloaded and installed Ubuntu 10.10 on my HP G60 laptop that already has windows 7. Now, when I start, I'm given the option of Ubuntu Loader, Two Memory Tests, Windows 7 loader, and Windows Vista loader. When I click Windows 7 loader, I am taken to another screen where I choose just Windows 7 or Ubuntu. Once I click Windows 7 again, I see the beginning of the boot where the four colors meet but after they meet, a green screen flashes and the computer is rebooted. How can I get into Windows 7? I need to use some programs on it urgently!

---

### Post by forestG on 2010-10-24
In order to fix that you can google the query linux fix windows MBR (or boot). A link that might help is the following [http://lifehacker.com/345928/fix-windows-master-boot-record-with-an-ubuntu-live-cd](http://lifehacker.com/345928/fix-windows-master-boot-record-with-an-ubuntu-live-cd).

Another option if you have your windows 7 cd is to fix the mbr using the windows 7 cd. At this point you will be able to boot to windows but not ubuntu. Ofcourse afterwards you will not be able to boot to ubuntu and you will need the ubuntu cd. Hopefully when you use the ubuntu cd you will be able to boot to windows 7 normally.

---

### Post by oldfred on 2010-10-24
Welcome to the forums.

Did you have wubi and then also install to a partition? 

To see what you have installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---


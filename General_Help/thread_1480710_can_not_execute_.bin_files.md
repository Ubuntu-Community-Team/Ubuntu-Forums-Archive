---
title: "can not execute .bin files"
date: 2010-05-11
forum: General Help
---

### Post by mkarr on 2010-05-11
I have just installed 64bit Ubuntu 9.10 and I can't execute bin files.


      ~/Downloads$ chmod +x AdbeRdr9.3.2-1_i486linux_enu.bin

      ~/Downloads$ ./AdbeRdr9.3.2-1_i486linux_enu.bin

      bash: ./AdbeRdr9.3.2-1_i486linux_enu.bin: No such file or directory



no matter what bin file I download and try to install this is the output I get. If I try "sh" instead of "./" I get this



      ~/Downloads$ sh AdbeRdr9.3.2-1_i486linux_enu.bin

      AdbeRdr9.3.2-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected



hopefully there is a quick fix to this. If not I guess I'll just have to reinstall and hope for the best. Thanks for any help...........

---

### Post by fooman on 2010-05-11
have you tried using both sh and ./ ?   ....like this:

```
sh ./AdbeRdr9.3.2-1_i486linux_enu.bin
```

---

### Post by mkarr on 2010-05-11
Thanks for the reply. This is the output I got when I tried what you suggested: 


      ~/Downloads$ sudo sh ./AdbeRdr9.3.2-1_i486linux_enu.bin

      ./AdbeRdr9.3.2-1_i486linux_enu.bin: 1: Syntax error: "(" unexpected

---

### Post by fooman on 2010-05-11
are you sure that you have typed out the command correctly?  ....have you tried using the "tab" key to automagically complete the command??  that will make sure you have not made a typo....

type only the first few characters of the command,  like this:

```
./Adb
```then press "tab".  the rest of the command should fill in by itself,  when it does....press enter and see if it will install.

---

### Post by bredman on 2010-05-11
I don't know what type of file the bin file is, but it does not seem to be a valid executable on Ubuntu.

If possible, try to download a version which ends with .deb or with .tar.bz2 You can double-click on these file types in the File Manager to open them.

Have you checked if the version you want is available in Synaptic Package Manager? This is by far the safest way to install.

---

### Post by fooman on 2010-05-11
> **bredman said:**
> I don't know what type of file the bin file is, but it does not seem to be a valid executable on Ubuntu.

If possible, try to download a version which ends with .deb or with  .tar.bz2 You can double-click on these file types in the File Manager to  open them.

Have you checked if the version you want is available in Synaptic  Package Manager? This is by far the safest way to install.


yes, the package manager or a .deb are the preferred methods....but .bin files should install without problem.

---

### Post by sijusamuel on 2010-05-28
Make AdbeRdr9.3.2-1_i486linux_enu.bin executable by 

chmod +x AdbeRdr9.3.2-1_i486linux_enu.bin
then , 
sudo ./AdbeRdr9.3.2-1_i486linux_enu.bin     Extact to a directory, and then 
the executable will be in  bin directory (for Example : ~/Desktop/AdobeReader/Adobe/Reader9/bin/acroread  )

siju samuel

---

### Post by oldos2er on 2010-05-28
> **mkarr said:**
> I have just installed 64bit Ubuntu 9.10 and I can't execute bin files.


      ~/Downloads$ chmod +x AdbeRdr9.3.2-1_i486linux_enu.bin

      ~/Downloads$ ./AdbeRdr9.3.2-1_i486linux_enu.bin

      bash: ./AdbeRdr9.3.2-1_i486linux_enu.bin: No such file or directory


```
sudo apt-get install ia32libs
``` should allow you to install a 32-bit *.bin file, or enable the partner repository and install Adobe Reader from Synaptic or apt-get.

---

### Post by naked_pianist on 2010-06-18
The answer is [here]("http://helpforlinux.blogspot.com/2010/05/how-to-install-adobe-pdf-reader-on-any.html?showComment=1276912619406_AIe9_BEWHcJ9T7N7Jx9PC1_Nc6zMcDamvjy_spU6QPCDzZf3KNWdEgFI8YNAnQkMtr-az15yzZ0aVi9uZYFtTuaIA8EQcCGIAouXZ23lfHE1nSmWYOSysSFjvaLxCYODUyTPq1sPF6M-9lhAqWXJhs6d4A9v6TwN9qEli4Q7kSwCRsGqWWSfJbbE_ADbcC05ymtuQcRiAU2s9CPOwJQar6cxORs5AxHZAxh9Qd5WtSCM9c1hnxrO6f6CkVnWGewPftX8jYSU0P44#c4787930702576481027") (make executable and run with sudo)
[URL="http://helpforlinux.blogspot.com/2010/05/how-to-install-adobe-pdf-reader-on-any.html?showComment=1276912619406_AIe9_BEWHcJ9T7N7Jx9PC1_Nc6zMcDamvjy_spU6QPCDzZf3KNWdEgFI8YNAnQkMtr-az15yzZ0aVi9uZYFtTuaIA8EQcCGIAouXZ23lfHE1nSmWYOSysSFjvaLxCYODUyTPq1sPF6M-9lhAqWXJhs6d4A9v6TwN9qEli4Q7kSwCRsGqWWSfJbbE_ADbcC05ymtuQcRiAU2s9CPOwJQar6cxORs5AxHZAxh9Qd5WtSCM9c1hnxrO6f6CkVnWGewPftX8jYSU0P44#c4787930702576481027"]
[/URL]

---

### Post by jfd3220 on 2011-08-28
I had the same problem with postbooks bin files and the ia32libs solved that problem.

---


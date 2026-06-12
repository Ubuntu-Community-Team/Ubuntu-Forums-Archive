---
title: "Install a HP Printer"
date: 2009-10-11
forum: General Help
---

### Post by waltwin on 2009-10-11
How do I install my HP printer using my installation disk. When I try to install it directly from the cd it tells me that I am missing usb drivers.

waltwin

---

### Post by Tamlynmac on 2009-10-11
I'm using 9.04 "Jaunty"

I simply install it from [here]("http://hplipopensource.com/hplip-web/install.html") using the HP Automatic Installer? It worked great.

[Here's]("http://hplipopensource.com/hplip-web/supported_devices/index.html") the page for confirming that your printer is supported.

[Here's]("http://hplipopensource.com/hplip-web/install/install/index.html") the instruction page for the Automatic Installer.
[]("http://hplipopensource.com/hplip-web/install/install/index.html")
Good Luck and hope this helps.

---

### Post by jeremyswalker on 2009-10-11
I've never had to physically install an HP printer before, unless it was a network printer. Anytime I have an HP printer, I just turn it on and it is automatically installed. No CD or anything needed.

---

### Post by waltwin on 2009-10-11
I have installed the printer but one of the features of this printer is its ability to print on both sides of a sheet. I can't seem to activate this function. I have the download showing on my desktop but I am not sure how to tell if it is installed or not. I guess you can tell I am new at this ubuntu.

waltwin

---

### Post by sgosnell on 2009-10-11
If you want full functionality, install hplip.  It's in the repositories, or you can get the newest version from HP as a .deb file, and install it with gdebi.

---

### Post by hansdown on 2009-10-11
Hi waltwin.

Hope this helps.

[http://ubuntuforums.org/showthread.php?t=1267118](http://ubuntuforums.org/showthread.php?t=1267118)

---

### Post by waltwin on 2009-10-12
I have retrieved the file but I guess I just can't figure out how to install it. I have hplip-3.3.8.run sitting on my desktop but I am having no luck putting it anywhere. When I try to use the Open with "Wine Windows Program Loader" I get an error. Very confusing!

---

### Post by waltwin on 2009-10-12
> **waltwin said:**
> I have retrieved the file but I guess I just can't figure out how to install it. I have hplip-3.3.8.run sitting on my desktop but I am having no luck putting it anywhere. When I try to use the Open with "Wine Windows Program Loader" I get an error. Very confusing!
I have retrieved the file but I guess I just can't figure out how to install it. I have hplip-3.3.8.run sitting on my desktop but I am having no luck putting it anywhere. When I try to use the Open with "Wine Windows Program Loader" I get an error. Very confusing!

---

### Post by sgosnell on 2009-10-13
It's not a Windows program.  To run it, open a terminal and type ```
sudo ./hplip-3.3.8.run
``` or you can probably just type "sudo ./hp" and then press the Tab key, which will autocomplete it for you, unless you have more files name hp*.  

./ tells Linux to run the file with the name which follows, in the current directory.

---

### Post by Sef on 2009-10-13
> How do I install my HP printer using my installation disk. When I try to install it directly from the cd it tells me that I am missing usb drivers.


1) What model printer do you have?  

2) Are you connecting it directly or through a network?

3) Most HP printers that are connected directly you just plug in and turn on.  It will be automatically detected.

---

### Post by waltwin on 2009-10-13
> **sgosnell said:**
> It's not a Windows program.  To run it, open a terminal and type ```
sudo ./hplip-3.3.8.run
``` or you can probably just type "sudo ./hp" and then press the Tab key, which will autocomplete it for you, unless you have more files name hp*.  

./ tells Linux to run the file with the name which follows, in the current directory.
I get the response "command not found". I have downloaded hplip-3.9.8.run which is supposed to be a newer update but I can't figure out how to install it. I kind of figure that you now know that I am not real familiar with ubuntu!

---

### Post by StuartN on 2009-10-13
> **waltwin said:**
> I have hplip-3.3.8.run sitting on my desktop but I am having no luck putting it anywhere. When I try to use the Open with "Wine Windows Program Loader" I get an error.

The file hplip-3.3.8.run is a Linux script and needs to be made executable and run in Linux (right-click, properties, permissions and check the execution tickbox). This is the printer driver for Linux.

If you want Windows printer drivers for Wine then they could be .exe, possibly called something like setup.exe. Windows printer drivers in Wine do not give you printing capabilities within Linux.

---

### Post by jeremyswalker on 2009-10-13
> **waltwin said:**
> I get the response "command not found". I have downloaded hplip-3.9.8.run which is supposed to be a newer update but I can't figure out how to install it. I kind of figure that you now know that I am not real familiar with ubuntu!

The command should be:
```
sudo **sh** ./hplip-3.3.8.run
```
(The file is not executable by default.)

---

### Post by waltwin on 2009-10-13
> **jeremyswalker said:**
> The command should be:
```
sudo **sh** ./hplip-3.3.8.run
```
(The file is not executable by default.)
I nothing seems to be working. I think that perhaps the hplip is missing. I think that I know how to check it. I have downloaded the hplip-3.9.8.run and it is sitting on my desktop but I don't know how to install it!

---

### Post by jeremyswalker on 2009-10-13
> **waltwin said:**
> I nothing seems to be working. I think that perhaps the hplip is missing. I think that I know how to check it. I have downloaded the hplip-3.9.8.run and it is sitting on my desktop but I don't know how to install it!

If the file is sitting on your desktop, open a terminal and try this:
```
sudo sh /home/USERNAME/Desktop/hplip-3.9.8.run
```
Replace USERNAME with your username.

---

### Post by waltwin on 2009-10-13
> **jeremyswalker said:**
> If the file is sitting on your desktop, open a terminal and try this:
```
sudo sh /home/USERNAME/Desktop/hplip-3.9.8.run
```
Replace USERNAME with your username.
Well, that took care of that. Thank you very much. I really appreciate all the help. I am reading everything I can get my hands on to learn this program.

---


---
title: "HP 2050 printer with scanner (scanner is not recognized)"
date: 2011-03-27
forum: General Help
---

### Post by wolfways on 2011-03-27
Can someone please help me? I have just bought and installed an HP 2050 printer-scanner-copier. The printer works fine, but the scanner is not recognised by Simple Scan or XSane.

_Simple Scan_ states: No Scanners Detected

_XSane Image Scanning Program_ states: No Devices Available

I have Ubuntu 10.10  - the Maverick Meercat installed on my computer.
After reading some comments on this forum:
I have downloaded the hplip-3.11.3a.run file from the HP website but _it is still in my download folder_ and I don't know how to get it from the download folder to my computer and then once that is accomplished, I don't know what to type in the terminal to get this file installed.

Heck, I don't even know if this is what I should install to correct this problem or not. 

Will someone PLEASE help me?

Thank you....................

---

### Post by PCNetSpec on 2011-03-27
if hplip-3.11.3a.run is in you Downloads dirctory.., to run the installer, open a terminal and enter:

```

cd Downloads
sh hplip-3.11.3a.run
```
hitting enter after each line.

Then just answer any questions the installer asks.

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by wolfways on 2011-03-28
Hi PCNETSPEC,

I typed each line exactly as you stated and I hit the "enter" button after each line.
I still wasn't able to install the hplip file.
This is what it told me:

_I typed_: cd downloads (then I hit the enter button)
bash: cd: downloads: no such file or directory
_I then typed_: sh hplip-3.11.3a.run (then I hit the enter button)
sh: can't open hplip-3.11.3a.run

PCNETSPEC what have I done wrong?

---

### Post by smart_m-j on 2011-05-09
Had the same problem after downloading the hplip-software. But I solved it like this:

1. Open terminal and let it show your current file directory, type:
"xyz:~$ **pwd**"
Terminal answers something like this: "/home"

2. Now you must navigate into the folder with hplip-3.11.3a (if you don't know open your folder-navigator and take a look at your directories and follow the path). If your "Downloads"-Folder with hplip is in this path: "home/mypc/downloads" then type:
"xyz:~$ **cd mypc/Downloads**" (write it exactly: **d**ownloads wouldn't work!)

Now you are in the Download-Folder.

(If hplip-3.11.3a isn't in the Downloads-Folder you must navigate into the right folder (for File & Directory Commands looking [**here**]("https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html")))

3.Now type this:
"xyz:~/Downloads$ **sh hplip-3.11.3a.run**"

Thats all - installation will start.

---

### Post by ebasa on 2011-05-09
> **wolfways said:**
> Hi PCNETSPEC,

I typed each line exactly as you stated and I hit the "enter" button after each line.
I still wasn't able to install the hplip file.
This is what it told me:

_I typed_: cd downloads (then I hit the enter button)
bash: cd: downloads: no such file or directory
_I then typed_: sh hplip-3.11.3a.run (then I hit the enter button)
sh: can't open hplip-3.11.3a.run

PCNETSPEC what have I done wrong?

It is cd /home/username/Downloads

Note the capital D

---


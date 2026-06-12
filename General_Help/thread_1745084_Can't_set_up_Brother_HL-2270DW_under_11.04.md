---
title: "Can't set up Brother HL-2270DW under 11.04"
date: 2011-04-30
forum: General Help
---

### Post by entropy1 on 2011-04-30
I have a Brother HL-2270DW that I managed to get working in 10.10.  Today I installed 11.04, but when I try to set up the printer by following the instructions on the Brother website, I get the following error:```
sudo dpkg  -i  --force-all "hl2270dwlpr-2.1.0-1.i386.deb"
[sudo] password for xxxxxx:
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 165977 files and directories currently installed.)
Preparing to replace hl2270dwlpr:i386 2.1.0-1 (using hl2270dwlpr-2.1.0-1.i386.deb) ...
Unpacking replacement hl2270dwlpr:i386 ...
dpkg: dependency problems prevent configuration of hl2270dwlpr:i386:
 hl2270dwlpr:i386 depends on libc6 (>= 2.3.4-1).
dpkg: error processing hl2270dwlpr:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hl2270dwlpr:i386
```

What should I do?

---

### Post by mykrob on 2011-04-30
looks like you're trying to install a 32-bit driver in a 64-bit system. Plus, the dependency is not resolved.

Typically, to get apt to auto-resolve a dependency, i run

sudo apt-get -f install

and if the dependency is in the repositories, it will install then proceed with correcting the package you;re trying to install. although i'm not sure if you will get that driver to install unless they have a 64-bit version.

---

### Post by wgarcia on 2011-05-01
Have you followed the instructions in [www.brother.com?](www.brother.com?) They have specific instructions for Ubuntu, maybe not for 11.04 but they should also work for this version.

---

### Post by entropy1 on 2011-05-01
Thank you, mykrob.  After doing```
sudo apt-get -f install
``` I did
```

tablet$ dpkg  -l  |  grep  Brother
iU  cupswrapperhl2270dw:i386   2.0.4-2 Brother HL2270DW CUPS wrapper driver
iU  hl2270dwlpr:i386           2.1.0-1 Brother HL-2270DW LPR driver

```
However, I still don't see the printer in CUPS or using system --> administration --> printing.

wgarcia:  the commands and files used in my original post were from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW)  These are the instructions that worked for me under 10.10, but now I still get the errors of my original post, even when I run those commands again after "sudo apt-get -f install"

---

### Post by kevinh52 on 2011-05-01
I have this same prob. I did the upgrade from 10.10 to 11.04 yesterday. Now trying to install 32-bit drivers couple of Brother printers. Procedure that worked in 10.10 now produces the same err above in this thread. apt-get -f install doesn't list anything.
Thanks

---

### Post by entropy1 on 2011-05-01
I gave up and re-installed 10.10.  Now I can use my printer again.

---

### Post by volchara on 2011-05-07
Bump. 

Kubuntu 11.04 64-bit.

Same behavior as shown above. Lists dependency on libc6 >=2.3.4-1. 

Installed the same driver on an i386 Kubuntu 11.04 yesterday without a problem, although the same version of libc6 (2.13-ubuntu13) is installed on both machines. 

Somebody please help, need to keep my wife's illusion that Linux is as easy as anything else :)

---

### Post by kimnzl on 2011-05-08
There are instructions to remove the dependency on the following bug entry:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856/comments/20](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/701856/comments/20)

---

### Post by stevedude on 2011-05-08
You can try this website for assistance: [http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys](http://islandlinux.org/es/howto/upgrading-ubuntu-breaks-printer-cupsys)

I have a Brother HL-2140, that the printing ability was broken when upgrading from Maverick to Natty. My situation is different, I'm using the CUPS drivers and not a Brother proprietary driver, however, I can't see my printer from a Windows 7 desktop where the printer is shared.

---

### Post by sleon on 2011-05-12
Got mine working in 11.04 after Brother tech support emailed me the following link:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090)

FYI, two things:
1) After clicking the download link on that page you'll end up on the license acceptance.  After pressing accept, it may dump the contents of the script into the page instead of downloading it to a file.  If that's the case, highlight and copy all the text and save it to a file.  Then chmod 777 and run under sudo (e.g. sudo ./brinst).

2) While the script is running there are long pauses, almost like its hung.  Just let it sit during this time and it will eventually finish.

So far everything seems to be working well.  HTH.

---

### Post by entropy1 on 2011-05-30
Thank you kimnzl.  Your solution worked for me.  I am using 11.04 64-bit.

---

### Post by alawson on 2011-06-28
I used KIMNZLs process to get mine working too - albeit as a generic PCL6 printer. At least it works....

EDIT: 11.04 64bit......

---

### Post by alliance1975 on 2011-07-15
Brother has published a solution to:

> •I cannot install Monochrome Laser Printer driver on Ubuntu11.4(64bit). 

at their web site.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00098](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00098)

It involves a patch file. I intend to test tonight.

---

### Post by alliance1975 on 2011-07-16
Please to say the fix worked. My Brother HL-2040 network printer now works.

---

### Post by GSBoomer on 2011-08-28
So, I was able to get it to work wirelessly. Here's what I did.

I downloaded and ran the script from Brother mentioned by sleon ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090)). When it reached the point in the script when it asked to specify a URI, I didn't know which one to select, so I tried the ipp one. It did not work.

So, I proceeded to try to add the printer via the cups interface at [http://localhost:631](http://localhost:631). It found multiple network printer options. The correct one is dnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/. Then, I used the PPD file at /usr/share/cups/model/HL2270DW.ppd. I assume it was installed by the script above.

IT WORKED! I suspect that it may also have worked if, when I ran the above script, I selected the one with 'datastream' in it, but I am unwilling to try it now that it works.

---

### Post by txducker on 2011-09-09
> **GSBoomer said:**
> So, I was able to get it to work wirelessly. Here's what I did.
...

But are you running 11.04 (Your signature says 10.10). This thread is specific to 11.04. I was having problems with 11.04 64-bit and wifi printing. I am following brothers website install instructions without success [URL="http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html"]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html
[/URL]
After trying to install drivers
```
[CODE]sudo dpkg -i --force-all hl2270dwlpr-2.1.0-1.i386.deb
```[/CODE]
I get an error: "dpkg: dependency problems prevent configuration of hl2270dwlpr:i386:
 hl2270dwlpr:i386 depends on libc6 (>= 2.3.4-1)."

I was stuck at getting the driver installed. I could connect to printer via wifi, but my driver .ppd file is not present/installed when I look at /usr/share/cups/model/.

After several hours, I followed alliance1975 [post #13 of this thread]("http://ubuntuforums.org/showpost.php?p=11051299&postcount=13") (Thanks!), and was able to get wifi printing working.
I posted my steps at and the patched driver files at [chadchenault.blogspot.com]("http://chadchenault.blogspot.com/2011/09/brother-hl-2270dw-printer-driver.html")

---


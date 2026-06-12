---
title: "BROTHER PRINTER : 64 to 32-bit drivers"
date: 2011-09-11
forum: General Help
---

### Post by nick.archambault on 2011-09-11
I've just bought a 3-in-1 Scanner/printer from Brother (DCP-7060D)

The problem is that on their website they only have the driver for the 64-bit Linux version.

I've tried to install the driver multiple times without success. 

Maybe I'm wrong but I believe that it's because I'm running on a 32-bit and that the driver is made for 64-bit that it's not working.

-> I'm running on Ubuntu 10.04 LTS 32-bit.

Is there anyway that I can make my printer work ? Thank you;)

---

### Post by Joebewan on 2011-09-11
Brother only offering a 64 bit driver on their website would make me suspect that the driver for 32 bit is already in Ubuntu.

Have you tried installing and letting Ubuntu detect it and pick the driver ?

---

### Post by hermannelson on 2011-11-15
I am having the same problem with my Brother dcp 7060d.

It is not a listed driver.

However, on their site you can download the drivers: But in 32 bit.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

Now, I understand you can install a 32 bit driver on my 64 bit, but no joy.

I get the message:      Wrong architecture 'i386' 


Any help would be appreciated,

Carl

---

### Post by kurt18947 on 2011-11-15
It looks like standard Brother Linux drivers.  The drivers available on Brother's site are 32 bit.  To install on a 64 bit system you have to do it via a terminal AFAIK.  Here is the key line:

```
Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)
``` Do the same with the CUPS driver and don't include the parentheses in the driver name.  Before you run the above command, be sure to look through the "before the installation" section. 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004)

 It appears to me that with newer Ubuntu releases there are two sections that are relevant:

Pre-required Procedure (5)
**Related distributions**Debian 64 bit version, Ubuntu 64 bit version**Related products/drivers**printer/PC-FAX drivers** Requirement:****  ia32-libs** or **lib32stdc++** is required to be installed.

and

Pre-required Procedure (6)
**Related distributions**Distributions that do not have csh or tcsh by default**Related products/drivers**Printer drivers for DCP-110C, DCP-310CN, FAX-1815C, FAX-1820C,  FAX-1835C, FAX-1840C, FAX-1920CN, FAX-1940CN, FAX-2440C, MFC-210C,  MFC-3220C, MFC-3240C, MFC-3320CN, MFC-3340CN, MFC-3420C, MFC-3820CN,  MFC-410CN, MFC-420CN, MFC-5440CN, MFC-5840CN, MFC-620CN **Requirement:  ****csh** or **tcsh** is required to be installed.

I hope this is of some help to you.

---

### Post by hermannelson on 2011-11-15
Thanks Kurt 18947
I appreciated your response.

The     sudo dpkg -i --force-all package.deb   command work well for me. Printer works !!

On my Brother dcp 7060d all in one, I am unable to get the scanner to work.

On launching xsane, I get:    Failed to open device  ' brother4:bus;dev5':invalid argument.

Any ideas out there?

Carl

---

### Post by kurt18947 on 2011-11-18
> **hermannelson said:**
> Thanks Kurt 18947
I appreciated your response.

The     sudo dpkg -i --force-all package.deb   command work well for me. Printer works !!

On my Brother dcp 7060d all in one, I am unable to get the scanner to work.

On launching xsane, I get:    Failed to open device  ' brother4:bus;dev5':invalid argument.

Any ideas out there?

Carl

If you're using 11.10, there's an issue with Brother scanners but it's easily fixed.  The problem is that some files are installed in the wrong folders and the solution is to copy them to the correct place.  Here is the FAQ link:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

There is also this which I believe will create your 'Failed to open.....' error:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

I hope this will be of some help to you.

---

### Post by hermannelson on 2011-11-19
[U]AWESOME !

Thanks so much, Kurt8947 . Your post worked for the scanner too.

I had come across the the fist link but missed the second, you had the missing link I needed.

A apppreciate you time in answering my question and hope this will help others.

Carl
[/U]

---

### Post by kurt18947 on 2011-11-20
You're welcome.  Glad it worked for you.

---

### Post by wumingzhu on 2012-03-21
[SIZE=4]hi, all, 
I just bought a brother dcp7060d MFC printer fpr my new pc with Ubuntu 12.04 64 LTS  after installed printer driver (installed by double click), it work fine but scanner not work even after scanner driver installed.I[/SIZE][SIZE=4]found a error in installation page: this program need to dtard up from terminal: brsaneconfig4[/SIZE]. following install instruction to install scanner driver in erminal, but fail. check installation result, show result as following:   	 	 	 	 	 	   [FONT=DejaVu Serif, serif][SIZE=3]wumingzhu@wumingzhu-System-Product-Name:~$ sudo  dpkg  -l  |  grep  Brother [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  brscan-skey                            0.2.1-3                                        Brother Linux scanner S-KEY tool [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  brscan4                                0.3.0-3                                        Brother Scanner Driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  cupswrapperdcp7060d:i386               2.0.4-2                                        Brother DCP7060D CUPS wrapper driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  dcp7060dlpr:i386                       2.1.0-1                                        Brother DCP-7060D LPR driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  printer-driver-ptouch                  1.3-3                                          printer driver Brother P-touch label printers 
[/SIZE][/FONT]
[FONT=DejaVu Serif, serif][SIZE=3]this look like driver installed correctly. but why does not it work? 
[/SIZE][/FONT]
[FONT=DejaVu Serif, serif][SIZE=3]who can help me? thanks first!
[/SIZE][/FONT]

---

### Post by kurt18947 on 2012-03-21
Hi wumingzhu

You might try adding scanner users to user group "lp"(lower case L).  This is in addition to copying files as documented here.  This problem exists in 12.04 as well:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

I haven't tried installing via a package manager though it may work with the scanner packages since they're available in both 32 bit & 64 bit.  I did find after scanning on a MFC-6490CW it didn't want to print.  Turning it off then back off fixed the problem.  The joys of developmental software. :smile:

---

### Post by wumingzhu on 2012-04-06
[QUOTE=wumingzhu;11782188][SIZE=4]hi, all, 
I just bought a brother dcp7060d MFC printer fpr my new pc with Ubuntu 12.04 64 LTS  after installed printer driver (installed by double click), it work fine but scanner not work even after scanner driver installed.I[/SIZE][SIZE=4]found a error in installation page: this program need to dtard up from terminal: brsaneconfig4[/SIZE]. following install instruction to install scanner driver in erminal, but fail. check installation result, show result as following:                                   [FONT=DejaVu Serif, serif][SIZE=3]wumingzhu@wumingzhu-System-Product-Name:~$ sudo  dpkg  -l  |  grep  Brother [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  brscan-skey                            0.2.1-3                                        Brother Linux scanner S-KEY tool [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  brscan4                                0.3.0-3                                        Brother Scanner Driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  cupswrapperdcp7060d:i386               2.0.4-2                                        Brother DCP7060D CUPS wrapper driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  dcp7060dlpr:i386                       2.1.0-1                                        Brother DCP-7060D LPR driver [/SIZE][/FONT] 
 [FONT=DejaVu Serif, serif][SIZE=3]ii  printer-driver-ptouch                  1.3-3                                          printer driver Brother P-touch label printers 
[/SIZE][/FONT]
[FONT=DejaVu Serif, serif][SIZE=3]this look like driver installed correctly. but why does not it work? 
[/SIZE][/FONT]
[FONT=DejaVu Serif, serif][SIZE=3]who can help me? thanks first!


[/SIZE][/FONT] [COLOR=Red]kurt18947: do like you said but not work! anyway, thank you very much![/COLOR]

---

### Post by hermannelson on 2012-05-05
Try this,
It worked for me.

I found the problem. The brscan4 package had installed the drivers into /usr/lib64/sane (all by themselves) instead of /usr/lib/sane (where the other sane drivers live).


Carl

---


---
title: "cannot scan"
date: 2012-04-21
forum: General Help
---

### Post by klirka on 2012-04-21
Hello, 

printing with my new Brother MFC5890CN works fine, but I cannot scan on my 2011 Kubuntu. I downloaded and installed these 64bit brscan3 and scan-key-tool drivers from the Brother page:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html#brscan3)

Now, hitting the button directly on the machine does not make it scan, and when I try from Simple Scan or XSane instead, these programs cannot detect a device.

I added these 2 lines of text, as suggested by the website's troubleshooting FAQ:
# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u9.10)

I also copied these files: 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

cp /usr/lib64/libbrscandec3.so.1.0.0 /usr/lib
cp /usr/lib64/sane/libsane-brother3.so.1.0.7 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so.1 /usr/lib/sane
cp /usr/lib64/sane/libsane-brother3.so /usr/lib/sane
cp /usr/lib64/libbrscandec3.so /usr/lib
cp /usr/lib64/libbrscandec3.so.1 /usr/lib

I rebooted, and still nothing. I tried as normal user, but also did "sudo xsane". Do you have any idea?

---

### Post by klirka on 2012-04-21
It works now, and apparently the only problem was that the scanner went on stand-by and trying to wake it up from Simple Scan and XSane did not work. So you first have to wake it up manually and then start a scan from Simple Scan.

Cheers.

---


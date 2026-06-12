---
title: "Omnikey OK 5321 usb smartcard reader"
date: 2011-03-01
forum: General Help
---

### Post by aybayrak on 2011-03-01
Hi,

What will I do to run the OK 5321 usb smartcard reader on my Ubuntu 10.10 ?

I have installed the  device driver ***ifdokrfid_lnx_x64-2.8.1*** ,***  pcsc-lite-1.6.6***   and [I] [B]syncapi_lnx-amd64-1.5.0 .

[/B][/I]But now I can not get feedback when I plug in the reader on usb. How can I make tthe reader work.  Is there anyone who can achieve this ? Thanks for any help

---

### Post by aybayrak on 2011-03-03
any suggestion ?

---

### Post by aybayrak on 2011-03-08
No reply so I found a solution for other users :)

Firstly we have to install pcscd an libccid packages. We can do this with Synaptic Package Manager. Optionally we can install pcsc_tools with apt-get install pcsc_tools
Then, we have to download the device driver from [http://www.hidglobal.com/omnikey](http://www.hidglobal.com/omnikey)
and install the driver to system with the guide of the install procedure inside of tar file

After the installation we have to disable the standart USB CCID driver with
# rm -rf /usr/lib/pcsc/drivers/ifd-ccid.bundle

then, restart the pcsc with 
# /etc/init.d/pcscd restart

If you installed the pcsc_tools you can test with pcsc_scan command 

(I tried  to do my best :))

---

### Post by tredegar on 2011-03-08
Thanks for the follow-up, it'll help someone else.

---

### Post by aybayrak on 2011-03-08
I hope :)

---


---
title: "2530 Konica printing fails with OpenOffice and Maverick 10.10"
date: 2010-10-18
forum: General Help
---

### Post by kevindontenville on 2010-10-18
Hi all

I have a Konica 2530DL colour laser and have used it with versions from 6.06 onwards. 

However now, with 10.10 I find I cannot print at from most apps eg OpenOffice or PDFs. I get errors on video frame showing on the printer but nothing obvious on the PC. 

Test print and gedit text prints works fine and so does using a VM with Lucid running on the same host prints fine too from anything.

Can't see any other comments about this problem anywhere but I know the printer is fairly common and has worked well with Linux in the past.

Using it with IP printing on port 9100 and allow the installation to detect and select the driver. Not setup anything clever and I have the same issue with a Lucid upgrade to 10.10 or a clean install. However the VM running Lucid prints fine. Must be something changed on Maverick somewhere. 

Anyone any ideas?

---

### Post by kevindontenville on 2010-10-20
OK to answer my own problem, it seems it doesnt like using socket 9100 but will work when configured as an IPP using dnssd.

I had to select the driver as it didnt autodetect it but seems printing is now back on.

Odd one, will try cups on the file server and see if that works more smoothly these days. Permissions used to be a pain ;-)

---


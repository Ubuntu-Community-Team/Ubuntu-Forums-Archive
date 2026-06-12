---
title: "network hard drive"
date: 2009-10-09
forum: General Help
---

### Post by jtmedin on 2009-10-09
I have a network hard drive that i use with vista. How do i handle that in ubuntu? TIA

---

### Post by Mighty_Joe on 2009-10-09
how do you connect to it from Vista?  Shared drive?  If so, you should be able to see it in the Network browser.
Have a look [at this article]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") to mount it permanently.

---

### Post by jtmedin on 2009-10-10
A network hard drive is a separate hd connected to a router & looks mostly like a separate computer (sort of). As a mater of fact the os in my NHD (its a Buffalo linkstation) is a Linux variation. I dont think the windows shared drive is relevant. Please correct me if i am wrong. TIA

---

### Post by Mighty_Joe on 2009-10-12
According to the [product documentation]("http://www.buffalotech.com/files/products/LinkStation-mini_DS.pdf"), Buffalo linkstation supports SMB, DLNA or HTTPS.  [SMB ]("http://en.wikipedia.org/wiki/Server_Message_Block")(also called CIFS) is the protocol Windows uses to share drives on a network.  Again, you should be able to see the shared drive in the network browser.

---

### Post by jtmedin on 2009-10-12
Ok i tried network & got to ms networks where it stalled. I must be missing something. There is no ms os running just the NHD & ubuntu 9.04. What more do i need to do to NHD/9.04 so 9.04 can see the files? TIA

---

### Post by Mighty_Joe on 2009-10-14
I *swear *I didn't have to install anything to get to my NAS.  Try installing the Samba file utilities and see if it makes a difference:

```
sudo apt-get install smbfs
```

---

### Post by StuartN on 2009-10-14
I have a Buffalo Linkstation and it works well. If you go to Places->Network then you should see your Linkstation at the top level, or down in Windows Network or both. You should be able to see all the share names, even if you don't have permissions to open them.

If you put the Linkstation's name and .local into your web browser (for instance buffalo.local if it is called buffalo), or if you use the Linkstation's IP address if you know it, then you will see the Linkstation's administration page. The Linkstation manual explains how to reset the box to a default password if you can't get in.

I only needed smbfs to mount Linkstation shares.

---

### Post by jtmedin on 2009-10-14
Bingo that did it & thanks.

---

### Post by jtmedin on 2009-10-14
Worked on my 32 bit but not on the 64 bit ubuntu. Not a big problem & not the first problem with 32 vs 64. Thanks again.

---


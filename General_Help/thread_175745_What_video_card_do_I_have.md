---
title: "What video card do I have?"
date: 2006-05-13
forum: General Help
---

### Post by DSn0wMan on 2006-05-13
How do I find out what video card I have? I know its some sort of ATI Mobility with 128 MB of ram, but I want to get it working. 

I suspect that my install isn't using it by default? Hopefully I am asking the right question.

---

### Post by tonyr on 2006-05-13
Start with **lspci** in a terminal.  Post the results.

---

### Post by louis_nichols on 2006-05-13
the command

```
lspci | grep VGA 
```

might give you the answer directly.

---

### Post by tonyr on 2006-05-13
It seems to me, reading between the lines here, that you have a video card
that you think is not working.  Tell more.  Not working how?  Not working
at all?  Doesn't even start the xserver?  Resolution issues? Garbled screen?
Are you satisfied to try and chase this down yourself?  There are a lot
of posts about ATI cards/drivers problems in these forums, especially
Breezy and Dapper forums.  Search on.

---

### Post by DSn0wMan on 2006-05-13
Here are the results

josh@josh-mobile:~$ lspci|grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460


I really have not tried anything yet, but I figured from other posts I read that I might have to work a little to get my video card, being that its ATI. So I just wanted to take a look at it before I try running any video games.

So far my display works perfectly, I just want to validate that I am useing my ATI Mobility (dont remember what model), and not some onboard graphics.


btw-- I have seen some driver instruction, but I want to be sure that I actually need a driver, and then be positive that I am getting the right one.

---

### Post by Ptero-4 on 2006-05-13
Ohh man, you really need to update to breezy.

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=Ptero-4]Ohh man, you really need to update to breezy.[/QUOTE]

I am using breezy!

---

### Post by tonyr on 2006-05-13
[QUOTE=DSn0wMan]
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5460
[/QUOTE]

This represents the interpretation of a PCI Vendor-ID and Product-ID pair.  
The vendor is obviously ATI (vendorId=0x1002), and the unknown productId 
is 0x5460.

[URL="http://www.pcidatabase.com/vendor_details.php?id=240"]
http://www.pcidatabase.com/vendor_details.php?id=240[/URL] says for this ID
> 
Chip Number: 	unknown
Chip Description: 	PCI\VEN_1002&DEV_5460&SUBSYS_20061028&REV_00\4&27EA4097
Notes: 	ATI controller in some Dell D610 laptops


[URL="http://cvsweb.netbsd.org/bsdweb.cgi/src/sys/dev/pci/pcidevs.diff?r1=1.781&r2=1.782&f=h"]
http://cvsweb.netbsd.org/bsdweb.cgi/src/sys/dev/pci/pcidevs.diff?r1=1.781&r2=1.782&f=h[/URL]
says for this productID
> 
product ATI RADEON_RV370_5460   0x5460  Radeon Mobility M300 (M22)

whatever that means.

You should do a little more reading to find out whether the Ubuntu
driver gives you the full performance of this controller.

---

### Post by DSn0wMan on 2006-05-13
[QUOTE=tonyr]

[URL="http://cvsweb.netbsd.org/bsdweb.cgi/src/sys/dev/pci/pcidevs.diff?r1=1.781&r2=1.782&f=h"]
http://cvsweb.netbsd.org/bsdweb.cgi/src/sys/dev/pci/pcidevs.diff?r1=1.781&r2=1.782&f=h[/URL]
says for this productID

whatever that means.

You should do a little more reading to find out whether the Ubuntu
driver gives you the full performance of this controller.[/QUOTE]
 
Thanks for helping, thats the one ATI Radeon Mobility 300M. You'd think I can remember a simple thing like that.

I am pretty sure I can research the rest on my own.

Thanks again everyone!

---

### Post by Ptero-4 on 2006-05-14
[QUOTE=DSn0wMan]I am using breezy![/QUOTE]
Sorry. I saw that the thread was posted in the Warty section.

---

### Post by DSn0wMan on 2006-05-14
Ya, I thought that was weird too. I just clicked on video & audio support forum > new thread, and this is where it ended up.

---


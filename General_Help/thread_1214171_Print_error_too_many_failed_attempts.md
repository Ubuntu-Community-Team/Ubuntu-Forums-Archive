---
title: "Print error: too many failed attempts?"
date: 2009-07-15
forum: General Help
---

### Post by oxf on 2009-07-15
Hi,

I'm trying to print and am frequently (but not always) getting the error message:
"Failed to print document: Too many failed attempts"

This more often happens when I try to print several pages at once but its now happening with a single page. Any ideas?

9.04 and printer is HP1460

Thanks

---

### Post by oxf on 2009-07-15
Any ideas on this. Right now its doing it every time I try and print a page. Grrrrr!

---

### Post by oxf on 2009-07-16
bump

---

### Post by svaens on 2009-09-15
I got the same. It seemed to occur when i got an authentication issue on the printer side (I forgot to turn off the change password on my windows server) and  i tried it a few times not realising the problem. After that, even when i'd fixed up the authentication, I'd get this problem. 

To fix it, I had to re-install the printer on ubuntu. 
I hope there is a better easier way to refresh a printer device?

---

### Post by silverrope on 2009-09-26
> **svaens said:**
> 
To fix it, I had to re-install the printer on ubuntu. 
I hope there is a better easier way to refresh a printer device?

I have the same problem. I have a HP Deskjet 920c on a Windows machine connected via samba. The printer works for a while (maybe going as high as 30 successful print jobs) and then for some unknown reason, the printer no longer responds to further print requests. After a few attempts to print, I get the "too many failed attempts" error. The only way I have been able to fix this is to re-install the printer, but this is a pain to do for every 30 print jobs!

I would like to help in debugging this, but what logs should I look at?

Oh, and BUMP!

Addition:
It seems to be related to authorization because I sometimes get the "Can't prompt for authorization" error. I normally give the administrator password. In the Printing app, I selected the Properties of my printer and under Device URI, I selected "Change". I again set the administrator password and hit "Verify". It shows the print share is accessible. But it still fails to print.

---

### Post by trundlenut on 2009-09-26
I was having a problem like printing to our main printer at work.  There wasn't actually a specific driver the printer that I could find and I was using the closest I could find.  After a bit of googling I determined that a different driver may work better, tried that and the problems stopped.

This was with a ricoh printer/copier.

---

### Post by cmcanulty on 2009-10-29
I am having the same problem with a HP Laserjet 2100M It is at our library and if I can't fix it soon we will be back to windows, what a sad way to lose Ubuntu.

---

### Post by silverrope on 2009-10-29
I am still getting this error. It has now appeared on a Brother HL-2035. I tried a different driver as suggested by trundlenut, but the error keeps reappearing after several successful prints.

As I have several Windoze computers and only one Ubuntu laptop, this isn't a killer bug; I just avoid using the laptop! Sad really, if it weren't for this bug, I would migrate my other computers to Ubuntu.

---

### Post by cgb on 2009-10-29
I previously had the same issue and what actually worked for me, dont ask why, is creating a copy of the printer and then printing through the copy.  So basically open up System/Admin/Printing then right click on your printer and choose copy.  Now set this as your default and try again.  Also I've seen other posts that may help in your situation in the below link.

[URL="http://brainextender.blogspot.com/2009/01/ubuntu-intrepid-too-many-failed.html"]

---

### Post by oxf on 2009-11-01
For what its worth and I dont know why? I resolved this by using another appliction. Specifically the problem occured when I was trying to print multi page pdf docs in evince. I switched to acroread and the problem didnt exist. So who knows???

---

### Post by cmcanulty on 2009-11-02
I also switched default pdf readers from evince (comes with ubuntu) to foxit which is fast. Now don't get errors but sometimes prints slow.

---

### Post by oxf on 2009-11-02
> **cmcanulty said:**
> I also switched default pdf readers from evince (comes with ubuntu) to foxit which is fast. Now don't get errors but sometimes prints slow.

Hmm Would seem to be an issue with Evince interfacing with certain printer drivers then. Glad you sorted it too!

---


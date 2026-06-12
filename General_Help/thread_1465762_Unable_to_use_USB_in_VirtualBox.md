---
title: "Unable to use USB in VirtualBox"
date: 2010-04-29
forum: General Help
---

### Post by sgsawant on 2010-04-29
I have downloaded the virtual box from the VirtualBox website. My linux is Ubuntu 9.10 amd64. I also tried the following method:

System>Administration>Users and Groups>Click to Make Changes (entered password)>Manage Groups>vboxusers>properties>(tick username)>(click ok)>(close)>(close)

After this I booted my Windows XP 32 bit in VirtualBox. But I still can't access my USB drives. One more thing to note is that the Group ID gets reset to "0" in the properties of vboxusers. A few times I tried to change it to "125". But after going back the same path, I find that it has been reset to 0.

Can anyone tell what is wrong?

P.S.: I am not able to access my shared folder too (in VirtualBox)!

Regards,

-sgsawant

---

### Post by arrrghhh on 2010-04-29
Are you using the version that is non-free?  There are two versions, a completely open-source version that doesn't support USB, and another partially closed-source that's free for personal use that enables USB, RDP, etc...

So if you're using that version that supports USB, did you setup the filters in VirtualBox?  I'm hoping you already read their guide on enabling USB, it's quite good....

---

### Post by davec64 on 2010-04-29
Assuming you didn't install the OSE version you need to install Guest Additions:

[http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/]("http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/")

If you installed the OSE version, that hasn't got USB support.

All the best

---

### Post by sgsawant on 2010-04-29
How do I check if I have got the right version?


Regards,

-sgsawant

---

### Post by sgsawant on 2010-04-29
@davec64:
Thanks! That seems to have solved the problem.

---

### Post by slvr42 on 2010-04-29
Install the guest additions in whatever version you have. USB should work after that.

---

### Post by sgsawant on 2010-04-29
Oh.....ok!

---


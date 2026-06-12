---
title: "How does one secure oneself against root passwd reset?"
date: 2012-06-14
forum: General Help
---

### Post by pavelmaha on 2012-06-14
Like it is mentioned here: [http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/](http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/)

---

### Post by bab1 on 2012-06-14
> **pavelmaha said:**
> Like it is mentioned here: [http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/](http://www.slashgeek.net/2012/06/12/reset-linux-root-password-in-under-5-minutes/)

Lock the machine up to deny physical access.  My NOC does not allow anyone in the machine room who is not known.  The building is locked from the outside.

---

### Post by Kira_Belka on 2012-06-14
:lolflag: ) there are a lot ways how to reset(or change) root password in ubuntu/GNU debian

small offtopic: so it's possible on most.. or on all distro's :))
and I know at least 17 ways how to reset password in winxp/vista/win7 :))))))

some of them is "standart" like using Ubuntu Live CD or recovery.
other part based on some "backdoors" and "rootkit" utilities that can help reset or change root password.. so and?
Just be careful..you can change grub menu (and you can allow just one line ..your system))) and set password protect on BIOS and set boot only from HDD drive :) 
so also you have to switch off boot menu for BIOS)
and you can encrypt your home folder :) 
also you can set up firewall and install rootkit detection and intrusion tools and Clamav :)
but it seems to me it 'll be paranoic security actions :)
all depends on what kind of info you have on your target PC.

PS. hack from inside .. it's not a hack)))

---

### Post by HermanAB on 2012-06-14
The military do four things when they are paranoid about a computer:
[LIST]
[*]BIOS password
[*]Boot password
[*]'Full disk' AES256 encryption
[*]Lockable steel cabinet around the whole workstation
[/LIST]

In most cases the first 3 is enough.

---

### Post by Kira_Belka on 2012-06-14
> **HermanAB said:**
> The military do four things when they are paranoid about a computer:
[LIST]
[*]BIOS password
[*]Boot password
[*]'Full disk' AES256 encryption
[*]Lockable steel cabinet around the whole workstation
[/LIST]

In most cases the first 3 is enough.

Full disk encryption?  hmmm.it 'll be interesting to see it :)

---

### Post by Ms. Daisy on 2012-06-14
Yup, physical access is root access.  Don't allow anyone physically on the computer to avoid this.

---

### Post by CharlesA on 2012-06-14
> **Ms. Daisy said:**
> Yup, physical access is root access.  Don't allow anyone physically on the computer to avoid this.
Yep.

Besides, if you have physical access, it is easier to boot off a livecd and access files than reset a password.

Encryption prevents this of course.

---

### Post by Habitual on 2012-06-14
Security Rule #1:
**There is NO security without physical security.**
Disable USB/CD booting in BIOS. 
Set BIOS password.
set grub password.

---

### Post by choochoousmc on 2012-06-14
Along with what others said.
Divide your drive up.
Use Truecrypt to encrypt that new "drive".  Use a long password with mixed upper and lower case letters, numbers and special characters. 10 + digits is very hard to crack.
Second option use an external drive with encryption (full Disk). And HIDE the drive.
Or lock it in a safe.

---


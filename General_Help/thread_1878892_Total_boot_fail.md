---
title: "Total boot fail"
date: 2011-11-10
forum: General Help
---

### Post by solf on 2011-11-10
Hi guys,

I'm new to Ubuntu..

I have the following hardware:
Compaq dektop:
core 2 duo e4400
3GB ddr2
a 250GB HD contains windows XP and Ubuntu
a 1TB HD with only Win7 on it
Geeforce 8500 GT

About 2 weeks ago I installed Ubuntu, and since then I can't boot from the 250GB HD (it just shows a black screen with a blinking cursor)  - Ubuntu's boot loader loads when I boot from the 1TB HD although Ubuntu's partition is on the 250GB HD!
Windows 7 loads well from Ubuntu's boot loader, but when I choose XP it dosen't (black screen with blinking cursor). Until yesterday I have been using Ubuntu, and right after the last update it is not loading too (same black screen)!! 

How can I restore Win XP and Ubuntu?

Thank you in advance,
Mark.

---

### Post by Mark Phelps on 2011-11-10
> **solf said:**
> About 2 weeks ago I installed Ubuntu, and since then I can't boot from the 250GB HD (it just shows a black screen with a blinking cursor)  - Ubuntu's boot loader loads when I boot from the 1TB HD although Ubuntu's partition is on the 250GB HD!
That's probaby because, when you installed Ubuntu, you had BOTH drives connected, and since GRUB probably saw the 1TB as the "first" drive in the system, it installed itself to that drive's MBR by default.  You would have done better having the 1TB disconnected when you installed Ubuntu.

> Windows 7 loads well from Ubuntu's boot loader, but when I choose XP it dosen't (black screen with blinking cursor). 
There are various ways to fix this, but one I recommend is the following:
1) Boot into Win7
2) Download and install EasyBCD from NeoSmart Technologies
3) Reboot (Win7)
4) Run EasyBCD and use the option to Edit the Boot menu.  You should seen an entry there for XP.  Use the option to remove that.  Save the result.
4) Now, use the option to add a new entry. Enter the information and select the "drive" containing XP.  save that.
5) Since your BCD is now updated with the "new" location of XP, it should boot OK.
> Until yesterday I have been using Ubuntu, and right after the last update it is not loading too (same black screen)!!  I've found that the black screen can last several minutes.  Give it some time and see if it eventually comes up.

> How can I restore Win XP and Ubuntu?
Told you how to restore access to them, to restore them from scratch is an entirely different problem.

---

### Post by solf on 2011-11-11
Thank you very much, EasyBCD has restored XP.

How can I bypass GRUB? Beacuse it shows me first GRUB, then I should choose WIN7 and only then I have the real choice of the three systems.

Ubuntu is still down!! I gave it 9 hours to boot.. and nothing..

Thanks,
Mark.

---

### Post by solf on 2011-11-11
Anybody please?

---


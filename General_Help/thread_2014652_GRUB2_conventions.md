---
title: "GRUB2 conventions"
date: 2012-07-02
forum: General Help
---

### Post by cipherboy_loc on 2012-07-02
Mods, feel free to move this, been a while since I have posted here.


Currently I am in the process of cleaning up and then publishing my project, a script to add isos to the grub menu. The script gets placed in /etc/grub.d, such that it is run with update-grub2. However, I am wondering what the conventions are when numbering it. Users can change the number to put it wherever in the boot order that they want it of course. 

The README says:
> 
All executable files in this directory are processed in shell expansion order.

  00_*: Reserved for 00_header.
  10_*: Native boot entries.
  20_*: Third party apps (e.g. memtest86+).

The number namespace in-between is configurable by system installer and/or
administrator.  For example, you can add an entry to boot another OS as
01_otheros, 11_otheros, etc, depending on the position you want it to occupy in
the menu; and then adjust the default setting via /etc/default/grub.


Currently I have it at 50_grubiso, however it sounds like 20_grubiso would be better?




Thanks,
Cipherboy

---

### Post by dino99 on 2012-07-02
maybe you should add yourself on the mailing-list and propose your project

[http://www.gnu.org/software/grub/grub-development.html](http://www.gnu.org/software/grub/grub-development.html)

---

### Post by cipherboy_loc on 2012-07-03
Got a response on the mailing list, thanks.


Marking as solved,
Cipherboy

---


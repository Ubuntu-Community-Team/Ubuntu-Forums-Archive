---
title: "Cant Boot after Hibernate"
date: 2010-10-30
forum: General Help
---

### Post by spiky001 on 2010-10-30
Ok I have encoutered a problem I selected Hibernate which Laptop did, Then I could not get it to start again, I hard Shutdown then restart It then just sits at Grub page when I hit enter to enter system it then loads to a black screen with blinking cursor. I have tried all other options recovery + 2 other earlier kernals all Kernals give same response. I can boot into XP ok on same drive. Need some help here plz Guys

---

### Post by spiky001 on 2010-10-30
Ok I have update to problem ```
user@user:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="64804FF8804FCF6C" TYPE="ntfs" 
/dev/sda5: UUID="acbf55ec-75e1-462b-af01-c790e447b2fc" TYPE="ext4" 
/[COLOR=Red]dev/sda6: UUID="37f4ca2c-df49-4690-a7aa-6edc64c6fbf1" TYPE="swsupend" [/COLOR]
/dev/sda7: UUID="229e6284-c3e7-4ab2-8cfc-a1dc503586cf" TYPE="ext4" 
user@user:~$
```Swap seems to be in suspend **How to resolve?**

---

### Post by spiky001 on 2010-10-30
Ok solved problem. From live cd i ran gparted found swap partition unknown file system so i reformatted swap then rebooted

---

### Post by Quackers on 2010-10-30
It looks like hibernation sent stuff to swap and then swap was then set to suspend. Not a problem if it will wake from that state, I suppose. I wonder if there is a DSDT problem. I don't use hibernate any more due to problems. I just suspend.

---

### Post by spiky001 on 2010-10-30
Nor will I, I was only trying it "out never again" Hope this helps someone else tho

---


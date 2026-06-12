---
title: "Ecessive Disk usage"
date: 2012-08-19
forum: General Help
---

### Post by sonnet on 2012-08-19
Hi,
I have installed a command-line ubuntu system, on a ssd  of 240GB.
Var and TMP files are on another disk.
There's no swap, and I have 16gb of ram.
On top of that I installed gnome-shell and the applications I needed.
Problem is that now it results that 20GB are used by my system.
My estimation was that around 6gb should be actually used which roughly match with the sum of /usr /libs /opt and all the other main dir residing on the ssd. In any case the usage shouldn't be higher than 8 gb.

So the question, why "df -h" command and gparted gave me as result that 20 gb are used on my disk (it say disk size 223gb,20 GB used and 203Gb free)?
I can't see where 12-14gb are gone. Even using disk usage utilities is not solving the issue.
Technically I should have hibernation since I do not have a swap partition.
I don't know about suspend, but from what I read it should affect the ssd, but only the ram.

---

### Post by Rexilion on 2012-08-19
What filesystem are you using?

---

### Post by sonnet on 2012-08-19
> **rexilion said:**
> what filesystem are you using?
ext4
Just to give a better picture here's a screenshot:
[IMG]http://i1163.photobucket.com/albums/q550/byebytoad/Selection_001.jpg[/IMG]

As you can see on the left, "df -h" command report that sda1 (which is the SSD) has 20gb used.

On the right you can see the disk usage analyzer report:
410GB are the GB used **_in total_**.
Of those ,402GB are used in Media (and those GB reside on a different disk).
2GB are used by the VAR partition (which also reside on another disk).
So the SSD disk shouldn't have more than 6-7 gb used.

---

### Post by Rexilion on 2012-08-25
I have an idea, could you post the output of:

```
tune2fs -l /dev/sda1 | grep -i -e Block\ Count -e reserved\ blocks
```

---


---
title: "auto-remove mbr... say WHAT?!"
date: 2009-12-24
forum: General Help
---

### Post by Mahngiel on 2009-12-24
*doesn't mbr = master boot record ??*
should i be getting this code, and should i actually perform this??

```

king@king:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Navy]The following packages were automatically installed and are no longer required:
   mbr[/COLOR]
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  grub2

```perhaps my knowledge isn't where i think it is, or perhaps it is - prompting me to post this. i dunno, may YOU do?

:guitar:

---

### Post by mobilediesel on 2009-12-24
> **Mahngiel said:**
> should i be getting this code, and should i actually perform this??

```

king@king:~$ sudo apt-get install grub2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=Navy]The following packages were automatically installed and are no longer required:
   mbr[/COLOR]
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  grub2

```perhaps my knowledge isn't where i think it is, or perhaps it is - prompting me to post this. i dunno, may YOU do?

:guitar:

grub2 is replacing mbr in this case. The hard drive will still have a mbr (Master Boot Record) that will now point to grub2. The package mbr isn't needed.

Don't forget to back up anything important when messing with how the system actually boots. From personal experience: if you have anything on the drive that's not easily replaced or restored you will lose it just by **thinking** about the master boot record. :lol:

---

### Post by Mahngiel on 2009-12-24
> **mobilediesel said:**
>  From personal experience: if you have anything on the drive that's not easily replaced or restored you will lose it just by **thinking** about the master boot record. :lol:

:lolflag: ain't it the damned truth! thanks, that's what i kinda thought, but ya know... like you said... *take two of these and call me in the morning*

---


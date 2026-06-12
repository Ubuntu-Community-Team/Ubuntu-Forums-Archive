---
title: "Partition Problem"
date: 2010-01-14
forum: General Help
---

### Post by ashvindora on 2010-01-14
Hello Guys,

I have just installed ubuntu 9.10 (karmic)..I have made two partition to my hard disk as show below:

/dev/sda1   swap                  2mb      unknown
/dev/sda2   ext4      /            39mb    unknown
/dev/sda3   ext4      /home    40mb    unknown

But the prob is when i go to my computer i found only 1 file system i.e i think 1 partition..I wonder where is the other one..I have attached a screenshot of my computer windows just for u to get an overview..

please let me know..

thanks
ashvin

---

### Post by 4pack on 2010-01-14
The way this works is like a house.

You have a house, a single building. It has many rooms, many partitions.

But you always enter the house through the single front door, through the single "Filesystem"

When you add more disk drives, it is just like adding more rooms to the house. They don't stand alone, they attach on to a spot on the existing house.

Your sda2 is the main part of the house, and the sda3 home partition is the add-on room at the back of the house. It's all one building.

---

### Post by ashvindora on 2010-01-14
Thanks for your tutorial on partition..i know wht the meaning of partition..
PLease anyone who have understood my query, try to solve my problem...

thanks
ashvin

---

### Post by Jackzor on 2010-01-15
What does gparted show?

---

### Post by ranch hand on 2010-01-15
> **Jackzor said:**
> What does gparted show?
This would be a better use for a screen shot.  I certainly hope you meant "gb" instead of "mb".

---

### Post by ashvindora on 2010-01-15
root priviledge are required to run gparted!!!!!

---

### Post by Sef on 2010-01-15
Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```

copy and paste the results here.

---

### Post by egalvan on 2010-01-15
Does it show anything when you open the "filesystem"?

It should.

On mine:

---

### Post by egalvan on 2010-01-15
> **ashvindora said:**
> root priviledge are required to run gparted!!!!!

Run the graphical version...

click on

System -> Administration -> Partition Editor

when it asks you for the password, just type in the same one you use to log in with.

---

### Post by ashvindora on 2010-01-15
thanks

when i run gparted program, i got a screen indicating the 2 partition i have created..it seems to b good..see attachment plz..

but when i go to my computer and click on file system i got another window..see attachment plz

i mean i want to see my 2 partition and use it when i click on my computer..same as on microsoft system (Local Disk)

PLease help

thanks

---

### Post by ranch hand on 2010-01-15
Looks fine, this is how it should be.

If you put another OS on, with 2 partitions, they will show up separately in that menu, as does "HANDY" which I assume is another drive with one partition.

---

### Post by garvinrick4 on 2010-01-15
> **ashvindora said:**
> thanks

when i run gparted program, i got a screen indicating the 2 partition i have created..it seems to b good..see attachment plz..

but when i go to my computer and click on file system i got another window..see attachment plz

i mean i want to see my 2 partition and use it when i click on my computer..same as on microsoft system (Local Disk)

PLease help

thanks

[GParted partitioning software - Full tutorial]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by ashvindora on 2010-01-15
yes..but where is the other partition?

---

### Post by ranch hand on 2010-01-15
sda5 and sda6 are both in your "file system" menu.

Only your /home  partition files are in your "ashvin" menu.

Every thing from your "ashvin" menu is in "file system>home" the reat of the "file system" menu is your / partition files.

Really, this is the way it is supposed to be.  If you looked at a default pcmanfm menu (default Lxde file manager like nautilus is for gnome) all you would see is the files for /home.

Nautilus,by default settings, give you a lot more access to your system files.  This is why I like it.

It also gives you more chance to break things although you do need to do that as "root".

---


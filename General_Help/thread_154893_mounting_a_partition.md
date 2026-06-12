---
title: "mounting a partition"
date: 2006-04-04
forum: General Help
---

### Post by jeisma on 2006-04-04
hello!

when i was preparing my ubuntu system, i created a partition (hda15) and assigned mount point /public

i want this partition not mounted when system starts, only mount when needed. its listed in the fstab, i commented it but /public can still be accessed (by root of course).

also i want "user1" (normal user) to be able to mount /dev/hda15 and have him full access to this partition.

i read man pages for mount and fstab, but cant work out what i want to achieve.


thank you!

---

### Post by trent dillman on 2006-04-04
add 'noauto' to the fstab

---

### Post by jeisma on 2006-04-04
[QUOTE=trent dillman]add 'noauto' to the fstab[/QUOTE]

if it's not listed in fstab, it still gets mounted anyway?


thanks!

---

### Post by justleen on 2006-04-04
[QUOTE=jeisma]if it's not listed in fstab, it still gets mounted anyway?
thanks![/QUOTE]

err.. no.. if you commented it in fstab, it should not be mounted.. did you reboot after editting??

---

### Post by jeisma on 2006-04-04
[QUOTE=justleen]err.. no.. if you commented it in fstab, it should not be mounted.. did you reboot after editting??[/QUOTE]

hi!

yep! i did reboot after commenting it. i wonder why i can still cd /public when its already commented in fstab. i was expecting to get something like:

bash: cd: /tst: No such file or directory


thanks!

---

### Post by trent dillman on 2006-04-04
oh, i get ya....

/public is there still, but the partition isn't mounted to it. that's normal.

---

### Post by jeisma on 2006-04-04
[QUOTE=trent dillman]oh, i get ya....

/public is there still, but the partition isn't mounted to it. that's normal.[/QUOTE]

understand. how bout this?

"i want "user1" (normal user) to be able to mount /dev/hda15 and have him full access to this partition."

thanks!

---

### Post by Sutekh on 2006-04-04
[QUOTE=jeisma]
i want this partition not mounted when system starts, only mount when needed. its listed in the fstab, i commented it but /public can still be accessed (by root of course).[/QUOTE]
Hi **jeisma**,  you should uncomment the entry in the fstab and add **noauto** as per trent dillman's suggestion.

This will not mount the partition when Ubuntu starts, but allows you to mount it much easier.

If a partition has an /etc/fstab entry then it can be mounted using the mount folder name.  It will get all the relevant options from the file rather than you having to specify them

So your folder could be mounted simply by using
```
sudo mount /public
```
rather than
```
sudo mount /dev/hda15 /public -t blah -o foo,etc
```
Saves a lot of time.

[QUOTE=jeisma]
also i want "user1" (normal user) to be able to mount /dev/hda15 and have him full access to this partition.

i read man pages for mount and fstab, but cant work out what i want to achieve.


thank you![/QUOTE]
I'm sure this can be done too.

What type of partition is it?

---

### Post by jeisma on 2006-04-04
hi!

i will try your instruction.

> What type of partition is it?

at fstab it says ext3. 


thank you!

---

### Post by Sutekh on 2006-04-04
[QUOTE=jeisma]
at fstab it says ext3. 


thank you![/QUOTE]
Excellent, the easiest of them all.  

Okay you need to do these commands with the partition *mounted*.
```
sudo chown -R user.user /public
```
Will change the ownership of the partition to **user**
```
sudo chmod -R 700 /public
```
Will give **user** full access, but no access to anyone else.

If you want more information on why I used** 700**, check out the

[Linux CHMOD Calculator](http://www.onlineconversion.com/html_chmod_calculator.htm)

PS - I should point out that if another user on your system is allowed to use **sudo**, then they can still get access to the partition.  Otherwise only **user** can get to it.

---

### Post by jeisma on 2006-04-04
hello!

wonderful!


thank you!

---

### Post by Sutekh on 2006-04-04
Good stuff, glad to hear it!

---


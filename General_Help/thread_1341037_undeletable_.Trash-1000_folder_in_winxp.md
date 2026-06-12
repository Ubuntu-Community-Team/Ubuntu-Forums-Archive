---
title: "undeletable .Trash-1000 folder in winxp"
date: 2009-11-29
forum: General Help
---

### Post by redbullah on 2009-11-29
hello all. i'm a 14 year-experienced pc user and slowly getting aware of the might of the open source software projects. but when i installed ubuntu 9.10, i experienced some problems. still i have lots of things to learn, you people's help will be greatly appriciated. here i go...

i have had winxp32 installed on my pc when i installed ubuntu as the second o.s. so there was winxp installed in c:, ubuntu installed in d: and g: was my external harddisk. after usin my pc like that for a while, i formated my local hard disk (c: and d:) to install winxp back on. but after all, when i plugged in my external hd (g:) there was a folder named .Trash-1000 in the root directory of g: and it seems empty with a size of 3.5gb. do not know why but i cannot delete it, the error is:

[IMG]http://i45.tinypic.com/b7e2w9.jpg[/IMG]

so what can i do?

---

### Post by zaphod777 on 2009-11-29
take ownership of the file and give yourself full read and write permissions.

it should be under the advanced properties of the security tab.

---

### Post by Irony on 2009-11-29
In terminal type;

```
gksudo nautilus
```

This will open a root nautilus from which you can then delete the .Trash1000 (press Ctrl+H to reveal hidden folders). Use Shift+Delete to delete it.

Remember you are acting as root so make sure you delete the correct file. Note the file will be recreated later when you do normal binning.

---

### Post by sensay on 2009-11-29
You didnt clarify if you had reinstalled ubuntu as well, if you have not you should also be able to remove the file from safe mode in windows

---

### Post by zaphod777 on 2009-11-29
> **sensay said:**
> You didnt clarify if you had reinstalled ubuntu as well, if you have not you should also be able to remove the file from safe mode in windows

Safe mode won't change security permissions. It is on;y helpful if a process is using that file and you can't delete it. In this case the current owner of the file is probably root for the ubuntu system. He needs to set himself as owner and give admin access to the file and then he can delete it.

---

### Post by audiomick on 2009-11-29
Hallo.
Even if you manage to get rid of it, I think it will turn up again as soon as you access the directory from Linux again, or at the latest as soon as you delete something from there in Linux.
You can always tell if a USB stick has been in an Apple when you put it in your Windows PC, because it has a .trash folder on it. I have seen the same on my stick in Windows after having the stick in the Linux pc. I assume it is a general Linux (OS X is also a linux) characteristic.
I would ignore it.

---

### Post by sensay on 2009-11-29
> **zaphod777 said:**
> Safe mode won't change security permissions. It is on;y helpful if a process is using that file and you can't delete it. In this case the current owner of the file is probably root for the ubuntu system. He needs to set himself as owner and give admin access to the file and then he can delete it.

Ah. I didnt realize the permissions from ubuntu would have any effect in windows. Duly noted and thanks for correcting me.

---

### Post by redbullah on 2009-12-03
hello everyone, and thanks for your responses. i will try to answer your feedbacks as clearly as i can.

> **sensay said:**
> You didnt clarify if you had reinstalled ubuntu as well, if you have not you should also be able to remove the file from safe mode in windows

i did not installed ubuntu after the last format. there is only winxp installed on my machine right now.

> **zaphod777 said:**
> take ownership of the file and give yourself full read and write permissions.

it should be under the advanced properties of the security tab.

i could not really understand what you mean "taking ownership of the file" but i already tried unchecking the "read-only" box from it's properties windows but it didnt worked. and interestingly, after i apply its properties as read-only box unchecked, the folder becomes semi-read-only (grayed out box with a check on it) everytime, automaticly. bur MORE interesting thing, i can rename folder! #-o

> **Irony said:**
> In terminal type;

```
gksudo nautilus
```This will open a root nautilus from which you can then delete the .Trash1000 (press Ctrl+H to reveal hidden folders). Use Shift+Delete to delete it.

Remember you are acting as root so make sure you delete the correct file. Note the file will be recreated later when you do normal binning.

i think you are talkin about some operation that is doable on linux os, so i am not sure i understand that 

> **audiomick said:**
> Hallo.
Even if you manage to get rid of it, I think it will turn up again as soon as you access the directory from Linux again, or at the latest as soon as you delete something from there in Linux.
You can always tell if a USB stick has been in an Apple when you put it in your Windows PC, because it has a .trash folder on it. I have seen the same on my stick in Windows after having the stick in the Linux pc. I assume it is a general Linux (OS X is also a linux) characteristic.
I would ignore it.

yes it looks like a harmless folder but it has a size of 3,54 gb and honestly i do not want to see it on my external hd root :)

keep feeding this post back please, i think this is the only post that has been discussed such a problem. thanks again :)

---

### Post by jegerjensen on 2009-12-03
So, what you want to do is to delete a troublesome file on an external hard disk? From Windows XP?

---

### Post by redbullah on 2009-12-03
yes, the reason of this post being on the ubuntu forums is this folder is created by ubuntu.

---

### Post by zaphod777 on 2009-12-03
The tricky part is by default XP has simple file sharing enabled and the security tab is hidden by default.

in windows explorer you need to go to tools->folder options-> view tab -> scroll to the bottom -> uncheck "simple file sharing" -> click ok.

now if you goto the properties of the folder you should have a security tab click the advanced button on the tab then the owner tab.

Select your user and tick the box replace on sub objects and click ok on all of the other windows.

after it fixes the security permissions you should be able to delete the file.

I have attached a few screen shots for reference.

Good thing there are a few MS Guru's on this boards huh? ;-) 

I love Linux but knowing MS pays the bills.

---

### Post by jegerjensen on 2009-12-03
> **redbullah said:**
> yes, the reason of this post being on the ubuntu forums is this folder is created by ubuntu.

I see, hope you are are able to fix it :)

---

### Post by John Bean on 2009-12-03
The trash folder isn't the issue; its contents are the problem.

My guess: in Ubuntu you deleted (moved to trash) the hidden Windows folder "System Volume Information". Now in Windows you're trying to remove the trash folder, but it contains "System Volume Information" and Windows simply won't allow you to do that.

My advice is to boot from a Ubuntu live CD and delete it from there.

---

### Post by redbullah on 2009-12-04
well, i think i solve the problem. if someone is experiencing same difficulties like me, here is the link: [http://ccollomb.free.fr/unlocker/](http://ccollomb.free.fr/unlocker/) it is a %100 free program that managed to delete the folder in no time. all instructions are available on the web site. thanks for help everybody :)

---

### Post by StuartN on 2009-12-04
> **redbullah said:**
> yes, the reason of this post being on the ubuntu forums is this folder is created by ubuntu.

Boot up into Ubuntu to deal with Ubuntu's files, it is much easier and much safer. As already noted, Ubuntu will continue to create a trash folder on the external drive anyway, so you should check, empty and delete them before exiting Ubuntu.

---

### Post by cosypanther on 2011-08-30
The checkdisk command in Windows 7 worked for me. Thx! =D>

---

### Post by mayankgour13 on 2012-01-11
> **zaphod777 said:**
> The tricky part is by default XP has simple file sharing enabled and the security tab is hidden by default.

in windows explorer you need to go to tools->folder options-> view tab -> scroll to the bottom -> uncheck "simple file sharing" -> click ok.

now if you goto the properties of the folder you should have a security tab click the advanced button on the tab then the owner tab.

Select your user and tick the box replace on sub objects and click ok on all of the other windows.

after it fixes the security permissions you should be able to delete the file.

I have attached a few screen shots for reference.

Good thing there are a few MS Guru's on this boards huh? ;-) 

I love Linux but knowing MS pays the bills.
Thanks, It worked for me. I was looking for from a long time. Thanks again.

---

### Post by gsgleason on 2012-01-11
Empty your trash before unmounting windows filesystem in linux.

---


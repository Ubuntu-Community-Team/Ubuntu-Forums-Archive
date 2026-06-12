---
title: "How to use Pen drive in command mode"
date: 2010-07-20
forum: General Help
---

### Post by fizmhd on 2010-07-20
i  am having only command mode of linux in my lab .. iam not able to take the gui .mode so i want to know how to use my pendrive for copying files .. in ma lab ...

---

### Post by rubylaser on 2010-07-20
Not exactly sure what you're asking.  Are you trying to put together a bootable usb install so you can work from the cli, or have you done that and now you're asking how to transfer files?

---

### Post by fizmhd on 2010-07-20
> **rubylaser said:**
> Not exactly sure what you're asking.  Are you trying to put together a bootable usb install so you can work from the cli, or have you done that and now you're asking how to transfer files?


no frend ..its my college computer lab ... 
the . interface is just like dos ...so i can't acess any drives in those command mode ... 

using telnet we connect to our user name and password ...

so after loging in i want to copy some files from my pendrive to my account ...

hope u get me ...

---

### Post by nothingspecial on 2010-07-20
Plug it in

```
sudo fdisk -l
```

Figure out which /dev/sd?? it has been assigned

Make somewhere to mount it

```
sudo mkdir /media/drive
```

I`m assuming it is formatted fat

```
sudo mount -t vfat /dev/sd?? /media/drive
```

---

### Post by finito on 2010-07-20
cd /media/

Then type ls

You should find your drive listed here

then do cp /home/user/file1 /media/drive1

cp being the command to copy,
first parameter location of file to be copied
Second parameter Location of where to sopy file to.

Enjoy

---

### Post by fizmhd on 2010-07-20
> **finito said:**
> cd /media/

Then type ls

You should find your drive listed here

then do cp /home/user/file1 /media/drive1

cp being the command to copy,
first parameter location of file to be copied
Second parameter Location of where to sopy file to.

Enjoy

thnx ..i just can see my pen drive ... 
is there any way ... like in dos we type cd X: ... so we move on to x: ... 

i want to enter my pendrive ... so that ..i can see what all files ...is ..there ..in it ..

and ..copy .. .."a file ie a .c file from my pendrive to my login account "

i login like this in my lab.

telnet 10.0.0.1
username : cs0734
psss: same

then ...my account come s ....

---


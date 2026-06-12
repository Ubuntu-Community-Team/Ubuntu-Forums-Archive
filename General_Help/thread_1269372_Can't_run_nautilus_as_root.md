---
title: "Can't run nautilus as root?"
date: 2009-09-18
forum: General Help
---

### Post by mordecai83 on 2009-09-18
Hello,

I have a freshly installed jaunty and i cannot seem to run nautilus as root.
The command "gksu nautilus" gives me the following error: 

Nautilus could not create the required folder "/root/Desktop". Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.

any help would be aprreciated.

with kind regards,
mordecai

---

### Post by sunchiqua on 2009-09-18
Does the following command results in the same error ?

```
gksudo nautilus /

```

---

### Post by pi4r0n on 2009-09-18
Hello **mordecai83**

Note really sure what happened there :) but lets give a go

[LIST=1]
[*]What happen when you run **sudo nautilus** (Is it the same error ??)
[*]Have you checked if this folder is actually there (/root/Desktop) ??
[/LIST]
[INDENT][INDENT]If no create it with the followng privialages 
drwxr-xr-x 2 root root 4096 2009-08-10 09:54 Desktop
[/INDENT][/INDENT]Cheers

Arek

---

### Post by mordecai83 on 2009-09-18
@ sunchiqua : that command returns the same error

@ pi4r0n:  1. same error  2.folder exist, dont know how to change permissions to it

---

### Post by t0p on 2009-09-18
> **mordecai83 said:**
> @ sunchiqua : that command returns the same error

@ pi4r0n:  1. same error  2.folder exist, dont know how to change permissions to it

The *same* error?  I don't understand.  The first error message said that the directory /root/Desktop didn't exist.  To rectify that, you need to create that directory.  You can do this by opening the terminal (**Applications > Accessories > Terminal**) and typing in the command:

```
sudo mkdir /root/Desktop
```Then you can change the owner of this directory with the command **chown** also in the terminal.  I think the syntax of the command is:

```
sudo chown root:root /root/Desktop
```

---

### Post by pmlxuser on 2009-09-18
sudo chmod -R 777 folder_name

or you could just change the own

sudo chown -R username:username

---

### Post by mordecai83 on 2009-09-18
To all, 

Thanks for your quick reply and help but seems like there is something wrong because i keep getting the same error. To specify: the folder /root/Desktop existed from the start. mkdir tells me the folder already exists. I think the permissions were ok from the start also, however even changing them like the last two replies suggest doesn't help. There must be something else. 

I am reinstalling ubuntu as we speak because it was a fresh install anyway and i think trying to find the solution to this will take more time (wich i dont have today). I do wanna thank you all again though.

kind regards,
Mordecai

---

### Post by pi4r0n on 2009-09-18
> **mordecai83 said:**
> To all, 
mkdir tells me the folder already exists.
Mordecai

Can you do below and show what you got there ?? (in root folder of course)

 > ls -ltr

---


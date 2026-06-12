---
title: "files permissions"
date: 2011-02-24
forum: General Help
---

### Post by legend_gibby on 2011-02-24
ok ive changed my files permissions so i can change them so on and so forth

now none of my programmes work!!! AAAAAAAAHHHHHHHHHH
i cant get back to root, oprn terminal, nothing!!

think im gonna have to restart my OS again!!!!

Can anyone help so i dont have to do this!!!!!

PLZ HELP!!!!

---

### Post by zenwalker on 2011-02-24
This is just vague question. You have to give us more details as what is happening and what you did and want to do. Once you changed the permissions for the system files then your done. Use the live cd and chroot into the installed file system and change all the file permissions back.

Still i am not clear whats going on. So my answer may not be as you would expect.

---

### Post by legend_gibby on 2011-02-24
ok what happened was..........

right i tried to put a theme into my urs/share/themes but it would let me coz it was in root access only.......so in my previous post i asked if i could change the permission

so i use the "gksudo nautilus" change the permission then added the folder.....then tried to change it back by using "gksudo nautilus" but to my surprise......it wouldnt let me

so i now have no access to my program's what so ever untill i turn it back to root!!!!!

---

### Post by zenwalker on 2011-02-24
You want to change the permission for the folder or for the file?

---

### Post by legend_gibby on 2011-02-24
i went into the "gksudo nautilus" change the owner and group to my name on file "usr" then saved it and exited the program...

i need to change the owner of the folder again back to "root" so all my programs will work again...

sorry my terminology is rubbish....

---

### Post by zenwalker on 2011-02-24
Since you have changed to your account, just log into the terminal and again change or just go to the file manager (if your logged in account the owner or the /usr and sub directories) and change it. You dont need root access.

---

### Post by legend_gibby on 2011-02-24
thanks but could you plz explain it a bit better step by step plz

im just tring to get to grips with UBUNTU!!!

i think your saying is to log out then log back in with a new account!?

---

### Post by AbsolutIggy on 2011-02-24
What he meant was:

Log in as normal, open a terminal.

Type:
```

chown -R root:root /usr

```

Or open nautilus normally and change the owner to the root user

---

### Post by Spyderkid on 2011-02-24
next time if your moving files into/out of  /usr  just use

[I]sudo su
mv FILENAME[/I]

---

### Post by legend_gibby on 2011-02-24
> **AbsolutIggy said:**
> What he meant was:
 
Log in as normal, open a terminal.
 
Type:
```

chown -R root:root /usr

```
 
Or open nautilus normally and change the owner to the root user
 
i restarted my comp and now just have a list of stuff then
 
[EMAIL="root@james-A0751h"]root@james-A0751h[/EMAIL]:~#
 
thing i have totaly messed it up!!!   aaaaaaahhhhhh

---

### Post by legend_gibby on 2011-02-24
think i have done it......
 
i restarted the comp.......then it asked me a few to pick so i choise the safe mode then asked to start.......
had to then login.......add password
 
this was all from a black screen!!!!
 
then i added the "chown -R root:root /usr" command and it apears to be doing something anyway!!!!!
 
its changing ownership of folders....so ill let yas know if this works!!

---

### Post by legend_gibby on 2011-02-24
its still going but at the end of everyline its says "operation not permitted"

---

### Post by legend_gibby on 2011-02-24
> **AbsolutIggy said:**
> What he meant was:
 
Log in as normal, open a terminal.
 
Type:
```

chown -R root:root /usr

```
 
Or open nautilus normally and change the owner to the root user
 
 
the other thing is i couldnt open a terminal or nautilus either.....so i switched off the comp and started it....then was asked for 4 options....i picked the second one safe mode...
 
then as my other post says.......loging enter password so on and so forth!!

---

### Post by legend_gibby on 2011-02-24
o well that didnt work.......so back to square one!!!!
 
thanks for all your help dudes!!!
 
just downloading the software again......to install ubuntu 10.10 again!!!

---

### Post by oldos2er on 2011-02-24
> **legend_gibby said:**
> so i use the "gksudo nautilus" change the permission then added the folder.....then tried to change it back by using "gksudo nautilus" but to my surprise......it wouldnt let me


Just so you know, using "gksu nautilus" itself gives you admin access to system folders; it's redundant and dangerous (as you found out) to then change permissions on those folders.

---


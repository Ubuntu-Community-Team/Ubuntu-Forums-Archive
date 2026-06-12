---
title: "User settings and root password??"
date: 2010-03-28
forum: General Help
---

### Post by stratus75 on 2010-03-28
Is this a Fault on my part or a bug?? (not sure if this is the right place for this let me no if not i'll move it thanks)

I want to add a user to Group "freevo" but if i open User settings via the GUI menus and click on the keys button to enter the root password it keeps coming back to me saying that the password is wrong even though it is'nt (and cap's is off).

So i try the terminal "user-admin" and had the same problem wrong password ...

So i try'd "sudo user-admin" and entered the password at the command line and up pops the User settings GUI with root privileges

---

### Post by zvacet on 2010-03-28
```
sudo adduser <username> freevo
```

---

### Post by stratus75 on 2010-03-28
Thanks for the reply. But why does the password not work in the graphical version of User settings after clicking on the keys button and entering the right password  it keeps saying that its the wrong admin password ??

---

### Post by zvacet on 2010-03-28
I understand what are you asking,but I don´t know the answer.I have similar problem with users&groups when I tried to add new user.I resolve it adding user from terminal and never thinking of it again.

---

### Post by sisco311 on 2010-03-28
By default, the root account password is locked. 

By default, sudo/gksu prompts you for your user password & policykit prompts for an admin user password.

[uhelp]community/RootSudo[/uhelp]

---

### Post by zvacet on 2010-03-29
@ **sisco311**

All you said is truth,but that is now point in this case.Thing is that adding new user GUI way fail from time to time,but CLI way work all the time.Whay is that I don´t know but I do know that is truth.

---

### Post by stratus75 on 2010-03-31
Thanks Guys

well it seems to be spreading now, i cant do anything via the command line now - install programmes, update manager etc 

One thing well really the only thing i remember doing ( with users and goups) was i made root a member of the freevo group (hdpc & pvr). and need to undo that to see if that changes anything ?? 

So my  next Question is whats the best command for that

just discovered that i cant mount disks now :-( so it would seem to be getting progressively worse for some reason??
also where would be a good place to start in tracking down the cause of this ? or would it be beyond my limited knowledge (well i suppose that fact that i have to ask that Q at all is an anwser in itself lol)
thanks again for yer patients !!:p

---

### Post by sisco311 on 2010-03-31
What's th output of:
```
groups
```?

---

### Post by stratus75 on 2010-03-31
> **sisco311 said:**
> What's th output of:
```
groups
```?

That would be ```
John Freevo
```

---

### Post by sisco311 on 2010-03-31
Boot into recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by stratus75 on 2010-03-31
If i type```
ls -l
```  i get the list of files and directorys all file i own and most directories with the exception of the recordings dir that is part of the freevo group.

---

### Post by stratus75 on 2010-03-31
> **sisco311 said:**
> Boot into recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

Thanks this link is going to come in very handy me thinks now and in the future !!

---

### Post by stratus75 on 2010-03-31
> **sisco311 said:**
> Boot into recovery mode and add your user to the admin group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

On the ball with that one sisco311 

used that link and cmd ```
 adduser username admin
```
and all is back to normal so far so good

thanks 
to everybody for your help. slowly but surely getting my head around linux/Ubuntu :D

---


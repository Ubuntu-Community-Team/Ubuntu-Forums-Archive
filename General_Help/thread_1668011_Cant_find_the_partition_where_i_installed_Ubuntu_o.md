---
title: "Cant find the partition where i installed Ubuntu on Ubuntu ! + other questions"
date: 2011-01-15
forum: General Help
---

### Post by amhjzm on 2011-01-15
Hi 
I am the ultimate noob i only installed Ubuntu few days ago but today i found out that the partition where i installed Ubuntu (using wubi) no longer exists on Ubuntu but it is there on widows7 and by the way i found that Ubuntu pocket book guide and reference 
is it helpful for someone who basically knows nothing 
and last i am thinking about turning to Mint they say it is much easier did any one try it , the main reason i want to get out of Ubuntu is that it very web dependent and my internet connection sucks or should i go with fedora 
sorry for putting three questions in one topic ;)

---

### Post by kn0w-b1nary on 2011-01-15
i would just install ubuntu straight cuz u can resize the windows partition in the installer. Most distros r web dependant that i've used. You can try Puppy Linux though. It's small, fast, doesn't require partitioning.

Hope this helps!

---

### Post by Dutch70 on 2011-01-15
> **amhjzm said:**
> Hi 
I am the ultimate noob i only installed Ubuntu few days ago but today i found out that the partition where i installed Ubuntu (using wubi) no longer exists on Ubuntu but it is there on widows7 and by the way i found that Ubuntu pocket book guide and reference 
is it helpful for someone who basically knows nothing 
and last i am thinking about turning to Mint they say it is much easier did any one try it , the main reason i want to get out of Ubuntu is that it very web dependent and my Internet connection sucks or should i go with fedora 
sorry for putting three questions in one topic ;)

Welcome to the boards & Linux.
You have installed Ubuntu into windows programs. It is in windows, not a separate partition.  

Mint is not easier, not to say that it is more difficult either. Ubuntu is one of, if not the easiest to learn imho. Once you learn one Linux OS, it's not difficult to use most of them. Kind of like changing from xp to vista to 7. Also, it is probably easier to get help with Ubuntu, as there are many more users. Which= more people to help you.

Your OS can't speed up your Internet connection. What makes you think Ubuntu is any more web dependent than any other OS? What does that even mean?

Good luck with whatever you choose
Dave

---

### Post by bcbc on 2011-01-15
> **amhjzm said:**
> Hi 
I am the ultimate noob i only installed Ubuntu few days ago but today i found out that the partition where i installed Ubuntu (using wubi) no longer exists on Ubuntu but it is there on widows7 and by the way i found that Ubuntu pocket book guide and reference 
is it helpful for someone who basically knows nothing 
and last i am thinking about turning to Mint they say it is much easier did any one try it , the main reason i want to get out of Ubuntu is that it very web dependent and my internet connection sucks or should i go with fedora 
sorry for putting three questions in one topic ;)

When you install with wubi it installs on a virtual disk - a file called root.disk that is loop mounted when Ubuntu boots. So it's not a physical partition. When you say it "no longer exists" on Ubuntu what do you mean?

When you boot Ubuntu it mounts the host partition (the one containing the root.disk) under /host. So maybe that is why you cannot see it under the Places menu. If that's not the answer you're looking for please explain more about the problem.

In terms of other distros, I can't help with that.

---

### Post by amhjzm on 2011-01-16
> **bcbc said:**
> When you install with wubi it installs on a virtual disk - a file called root.disk that is loop mounted when Ubuntu boots. So it's not a physical partition. When you say it "no longer exists" on Ubuntu what do you mean?

When you boot Ubuntu it mounts the host partition (the one containing the root.disk) under /host. So maybe that is why you cannot see it under the Places menu. If that's not the answer you're looking for please explain more about the problem.

In terms of other distros, I can't help with that.

I found a root folder in the file system but i couldnt open it 
it said that i didn't have a permission or something and one more thing Ubuntu keeps getting slower by time and if i install it without wubi will i get the same problem

---

### Post by amhjzm on 2011-01-16
> **Dutch70 said:**
> Welcome to the boards & Linux.
You have installed Ubuntu into windows programs. It is in windows, not a separate partition.  

Mint is not easier, not to say that it is more difficult either. Ubuntu is one of, if not the easiest to learn imho. Once you learn one Linux OS, it's not difficult to use most of them. Kind of like changing from xp to vista to 7. Also, it is probably easier to get help with Ubuntu, as there are many more users. Which= more people to help you.

Your OS can't speed up your Internet connection. What makes you think Ubuntu is any more web dependent than any other OS? What does that even mean?

Good luck with whatever you choose
Dave

what i meant by internet dependent is that it relies on downloading software and heavy upgrades after install without using a strong download manger and with bad internet connections that have high ping and packet loss this will simply not work

---

### Post by AmanSin on 2011-01-16
I'd Say stick to ubuntu, i've used Fedora, mint and puppy(i found puppy to be sumwhat....irritating o.o, the gui suck lol)...
and as for being web depended, well you know open source means that people share it over the network, so you arent goona find any distro which isnt!!!!
ubuntu is the B.E.S.T. as far as online support(and other support go)

and as for your problem....i've got no idea , because if i am right, wubi installs ubuntu within windows partition...i would recommend that you un-install it from there and reinstall using live cd, way better that way!! and defrag the windows partition before you do it(but i think ubuntu installer does that on it's on...correct me sumone if i am wrong :-? ) and once you install it over that way.. you'll know where u install it :D(generally the last sda partition)

---

### Post by bcbc on 2011-01-16
> **amhjzm said:**
> I found a root folder in the file system but i couldnt open it 
it said that i didn't have a permission or something and one more thing Ubuntu keeps getting slower by time and if i install it without wubi will i get the same problem

the folder is \ubuntu\disks and the file is root.disk

Hard to say if you'll have the same problem on a normal install - no idea what your problem is - but a normal install is always recommended if you're able to do this.

---


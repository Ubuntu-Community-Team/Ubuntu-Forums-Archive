---
title: "About Myself"
date: 2010-03-26
forum: General Help
---

### Post by cogier on 2010-03-26
Can you tell me how to use the "About Myself" software. The blurb says it can change change passwords, mount users etc. I can only get it to show very basic user details.

Thanks in advance.

---

### Post by bvkmohan on 2010-03-26
Hi Ubuntu this is mohan....

I have installed ubuntu as dual boot on my existing windows 7 machine 

it completed in less than 10 minutes ....

UBUNTU ROCKS!!!!  :popcorn:

---

### Post by lisati on 2010-03-26
> **cogier said:**
> Can you tell me how to use the "About Myself" software. The blurb says it can change change passwords, mount users etc. I can only get it to show very basic user details.

Thanks in advance.
What version of Ubuntu are you using? 
Have a look at the System->Preferences and System->Administration menus.

> **bvkmohan said:**
> Hi Ubuntu this is mohan....

I have installed ubuntu as dual boot on my existing windows 7 machine 

it completed in less than 10 minutes ....

UBUNTU ROCKS!!!!  :popcorn:

[QUOTE=lisati]Huh?[/quote]

---

### Post by cogier on 2010-03-26
I am using 9:10. I can access the program from Application>System Tools But all I get is a user details screen. I can use this to remind me of my name!

---

### Post by cong06 on 2010-03-26
When I open there's a button labeled "change password" in the top right... It's not there for you?
Is your user an admin (ie: can you run sudo)?


I'm in 9.04.

---

### Post by cogier on 2010-03-26
This is what I see (See attached). I can run Sudo. I have tried this on 2 computers and I get the same result.

---

### Post by cong06 on 2010-03-26
That looks bizzare. Mine is just wreathing with information (in both my desktop 9.04 and UNR 9.10)

Do you have:
```

sudo apt-get install gnome-control-center

```
installed?

---

### Post by cogier on 2010-03-26
Yes it seems I have.

charlie@wave-ubuntu:~$ sudo apt-get install gnome-control-center
[sudo] password for charlie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-control-center is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
charlie@wave-ubuntu:~$

---

### Post by cogier on 2010-03-26
I see now that the components are separate but they don't do what I am looking for.

I was really looking for a GUI that would change the User Name and Password in one simple step. This is so that if I set up a computer then give it to a user I can simply change the Home folder name etc.

---

### Post by cong06 on 2010-03-26
How did you fix it?



I don't think there's any easy way to change a username other then deleting it and re-creating it...

Do you set up settings for these users? or just install applications?
If it's the later, then a simple delete and adduser should work:
```

deluser <user>
adduser <user2> <group>

```

If it's the former, then I'd back up the home dir... maybe something like this:
```

mkdir /home/backup/
rsync -av --delete /home/<user>/ /home/backup/
deluser <user>
adduser <user2> <group>
rsync -av --delete /home/backup/ /home/<user2>

```

It might be time to learn bash scripts (if you don't have that stuff already).
You could do a gui if you wanted (mess around with Zenity) or just have something like:
```

echo "enter the user to delete"
read user1
echo "enter the user to add"
read user2

```
and then user $user1 and $user2 in the rsync code above.

If you have any questions please, don't hesitate to ask. We're here to help. I could explain this a bit more if you wanted to go down this alley.

---

### Post by cogier on 2010-03-26
cong06

Thanks very much for this. I have added the details to my "useful" file and it is being uploaded to Ubuntu One as I type.

I have been able to get hold of old PCs which have no operating system and I have install Ubuntu on them and given them to whoever was in need or interested. I am trying to spread the Linux word (and it's working).

So I have my machine running Ubuntu with the Home directory called "mine" and a simple password. With your help I can now change them to something more relevant.

I have learnt so much from this forum and am glad to say I have been able to put some things back as well. 

You are correct. I need to learn more about BASH scripting and possible Gambas programming.

If you have anything more I'd be pleased to receive it.

Thanks again.

---


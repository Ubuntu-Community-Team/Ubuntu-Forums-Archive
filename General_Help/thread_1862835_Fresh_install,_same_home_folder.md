---
title: "Fresh install, same home folder"
date: 2011-10-17
forum: General Help
---

### Post by Spitted on 2011-10-17
Hi

I'm using Ubuntu 11.04 and want to do a fresh install of 11.10 (formatting the partition currently mounted to / and install).
Before I'll do that, I want to make sure I'll be able to access my home folder. Is it possible to create the same user I use now in the new installation? Will I encounter any problems?

Thanks,
Eyal

---

### Post by BlinkinCat on 2011-10-17
Hi,

As long as you don't format /home you can create the user(s) in your new installation using the same user name(s) 

Cheers - :)

---

### Post by nothingspecial on 2011-10-17
If your current user is the original user on your system then you will have a uid and gid of 1000

If you have multiple users you need to create them in the same order.

For example if I type

```
less /etc/passwd
```

and scroll to the end, I see

```
me:x:1000:1000:me,,,:/home/me:/bin/bash
mrs:x:1001:1001:mrs,,,:/home/mrs:/bin/bash
son1:x:1002:1002:son1,,,:/home/son1:/bin/bash
son2:x:1003:1003:son2,,,:/home/son2:/bin/bash

```

So I need to create the user me when installing the system

Then

mrs
son1
son2

in that order so the uid and gid are the same.

---

### Post by Spitted on 2011-10-17
Great, thanks. :)

I found this line:
```
eyal:x:1000:1000:Eyal,,,:/home/eyal:/bin/bash
```
So I guess it should be fine

---

### Post by Meelad on 2011-10-17
Be careful, back your files up! Ubuntu could very well try to make a home folder for you and overwrite the the old folder if you assign the home partition to the one already containing your home folder..

Just back your files up and copy them again into your home folder when you are finished.. This is much safer..

---

### Post by nothingspecial on 2011-10-17
I'm assuming you have a /home partition here.

If you don't, you will wipe your home folder if you format /

---

### Post by tubunu on 2011-10-17
Don't forget to mount your /home (/sda7 or whatever it is) to /home in the manual partitioning section of the installation process.

---

### Post by Spitted on 2011-10-17
I appreciate your concerns, thanks a lot!
I do have a separate /home partition and I plan to mount it to /home again in the new installation.
I will backup my files just to be on the safe side. Nevertheless I hope Ubuntu won't overwrite my home since this would be less comfortable.

---

### Post by nothingspecial on 2011-10-17
When you get to the stage "How do you want to install Ubuntu?" (or something like that) choose "something else"

Select your / partition, choose to use it as an ext4 journaling file system. Give it a mount point of / and choose to format it.

Select your /home partition, **_[COLOR="Red"](this is important)[/COLOR]_** choose to use it as whatever file system it already is.

Give it a mountpoint of /home
[COLOR="Red"][B][SIZE="2"]
But do not choose to format it.[/SIZE][/B][/COLOR]

And you should be fine.

But yes a backup is prudent because you never know.

---

### Post by Spitted on 2011-10-17
Yup, I was going to do exactly as you described. Thanks :)

---

### Post by kwildman on 2011-10-17
This is how i typically do all of my upgrades.  Dedicated \home partition.   However, i ran into some issues with Unity being completely jacked up - no shutdown button, missing icons on the launcher (there was empty space where they should be and the programs would start by clicking on it but no icons), etc.   I think some of the gnome2 stuff in the \home was causing conflicts.   I had to copy my user directories and then format my \home and copy the user stuff back.  This took care of all the weird stuff i was encountering.   

Overall, the installing with a decicate \home is the way to go and has saved me countless hours during previous upgrades.  This time it bit me in the backside.

---

### Post by Spitted on 2011-10-17
I did the installation and it went very well. I didn't even had to use the backup I made, and everything is working flawlessly.
Oneiric is surprisingly impressive. It is very slick and feels like a "proper" version of Natty. Fixed most of the stuff I complained about.
I can't wait to dive into Gnome-Shell, although I know I'll miss this great and improved Unity. :)

---


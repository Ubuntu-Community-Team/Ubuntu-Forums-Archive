---
title: "how to delete a folder owned by root"
date: 2011-07-04
forum: General Help
---

### Post by bombicri on 2011-07-04
I copied a folder from /media/memory_stick into a folder /opt/openerp/server/bin/addons.
Trying to open the copied folder I discovered that it is impossible because it is owned by root.
I should like to delete the copied folder.
To avoid this ownership I copied the folder in /home/cristian/Downloads and I will copy it with:

sudo cp -R folder_name /opt/openerp/server/bin/addons

Maybe in this way the folder will be not more owned by root.
I tried already but because in the destination folder already exist one owned by root nothing is happening.
Is this a good way?

Or maybe is easier to change the ownership?
If yes, then how to do it?

---

### Post by srisharan on 2011-07-04
If you just need to delete it you can open nautilus as root
```
sudo nautilus
```

---

### Post by apollothethird on 2011-07-04
> **bombicri said:**
> I copied a folder from /media/memory_stick into a folder /opt/openerp/server/bin/addons.
Trying to open the copied folder I discovered that it is impossible because it is owned by root.
I should like to delete the copied folder.
To avoid this ownership I copied the folder in /home/cristian/Downloads and I will copy it with:

sudo cp -R folder_name /opt/openerp/server/bin/addons

Maybe in this way the folder will be not more owned by root.
I tried already but because in the destination folder already exist one owned by root nothing is happening.
Is this a good way?

Or maybe is easier to change the ownership?
If yes, then how to do it?

You can change the ownership by:

```
chown user:group filename
```user: the name or number
group: the group name or number
filename: the name of the file (or directory)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by RikoW on 2011-07-04
Hi,

you can change ownership of the folder by:

```
sudo chown -R username:username /opt/openerp/server/bin/addons
```

where "username" is your username, I suppose "cristian".

If you want to remove it, you use sudo as well:

```
sudo rm -r /opt/openerp/server/bin/addons
```

Depending on what you want to do with the folder, it may be just enough to give read and execution rights to the users on you system:

```
sudo chmod -R gu+rx /opt/openerp/server/bin/addons

```

This will give members of the current group [g] and all users [u] read [+r] and execution [+x] rights to the folder and it's content [-R].

Cheers,
     Riko

---

### Post by srisharan on 2011-07-04
Ok,here is the full method.If you just need to delete it you can open nautilus as root
```
sudo nautilus
```

Then a nautilus windows will open as root and you can delete the file you want.But be careful as you can manipulate any file since you are root.And close the root nautilus immediately after your work is done so that you may not accidently  do something which might harm the system

---

### Post by CatKiller on 2011-07-04
> **srisharan said:**
> If you just need to delete it you can open nautilus as root
```
sudo nautilus
```

Don't use (or suggest using) graphical applications with *sudo*. It messes things up. Graphical applications should be used with *gksudo*.

---

### Post by srisharan on 2011-07-04
> **CatKiller said:**
> Don't use (or suggest using) graphical applications with *sudo*. It messes things up. Graphical applications should be used with *gksudo*.

Ya,I keep forgetting that.Thank you for reminding me

---

### Post by bombicri on 2011-07-04
Thanks to all, with your help I know now more about working with Ubuntu.
My problem was solved due to your help.
Thanks again.

---


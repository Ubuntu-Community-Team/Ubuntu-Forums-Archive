---
title: "Going mad trying to add a repository"
date: 2009-09-06
forum: General Help
---

### Post by 1ronlung on 2009-09-06
First .. I have read the help page on this.

I'm trying to add the following repo :

[http://arco.esi.uclm.es/~francisco.moya/debian/](http://arco.esi.uclm.es/~francisco.moya/debian/)

Am using the gui under system admin.

Now, I'm forced to specify distro and type .. e.g Jaunty and universe

My problem is that once I've entered the repo, ubuntu adds on /i386 ... etc to the URL.
This directory doesn't exist on the repo I'm trying to add.

Any workaround ?

---

### Post by Bodsda on 2009-09-06
> **1ronlung said:**
> First .. I have read the help page on this.

I'm trying to add the following repo :

[http://arco.esi.uclm.es/~francisco.moya/debian/](http://arco.esi.uclm.es/~francisco.moya/debian/)

Am using the gui under system admin.

Now, I'm forced to specify distro and type .. e.g Jaunty and universe

My problem is that once I've entered the repo, ubuntu adds on /i386 ... etc to the URL.
This directory doesn't exist on the repo I'm trying to add.

Any workaround ?

Add the line to the /etc/apt/sources.list file and then run
```
sudo apt-get update
```

Hope this helps,
Bodsda

---

### Post by defacto on 2009-09-06
```
sudo -i
echo "deb http://arco.esi.uclm.es/~francisco.moya/debian/" >> /etc/apt/sources.list
exit
sudo apt-get update

```

---

### Post by Bodsda on 2009-09-06
> **defacto said:**
> ```
sudo -i
echo "deb http://arco.esi.uclm.es/~francisco.moya/debian/" > /etc/apt/sources.list
sudo apt-get update

```

your still root when executing the update, should be
```

sudo -i
echo "deb http://arco.esi.uclm.es/~francisco.moya/debian/" > /etc/apt/sources.list
exit
sudo apt-get update

```

Kind regards,
Bodsda

---

### Post by 1ronlung on 2009-09-06
No good.  From what I can tell, if I leave out the distro and repo type, I get an error re a malformed line in souces.lst when I run the get update.

If I include the distro and type details, I have the same problem as via the gui - it looks for directories that aren't there.

Thanks for the answer, tho'

---

### Post by defacto on 2009-09-06
> **Bodsda said:**
> your still root when executing the update, should be
```

sudo -i
echo "deb http://arco.esi.uclm.es/~francisco.moya/debian/" >> /etc/apt/sources.list
exit
sudo apt-get update

```Kind regards,
Bodsda

Fixed a few seconds before your post :)

---

### Post by imhotep59 on 2009-09-06
Hello,

Did your enter the line as this ?
```
deb http://arco.esi.uclm.es/~francisco.moya/debian/
```
With deb before [http://.](http://.)...

Edit: oops, I'm too slow !

---

### Post by falconindy on 2009-09-06
Danger! Do NOT use a single '>' when trying to **append** information to a file. You will wipe the contents of a file unless you use the double '>>'.

---

### Post by 1ronlung on 2009-09-06
> **imhotep59 said:**
> Hello,

Did your enter the line as this ?
```
deb http://arco.esi.uclm.es/~francisco.moya/debian/
```
With deb before [http://.](http://.)...

Edit: oops, I'm too slow !

Yup.. I did.

I'm sure this is something really simple, but I'm a bit n00b.

Would someone mind trying to addo it to their list if they're using Jaunty.. Just to make sure I'm not being really stupid.

Getting frustrated.. Been at this hours now ...

---

### Post by defacto on 2009-09-06
> **falconindy said:**
> Danger! Do NOT use a single '>' when trying to **append** information to a file. You will wipe the contents of a file unless you use the double '>>'.

Weird that, when I use '>' to add new folders to .hidden file, it appends them :-k Anyway, you are right ( syntax ), so .. let's leave it as it is ( posts edited ).

---

### Post by CatKiller on 2009-09-07
```
deb http://arco.esi.uclm.es/~francisco.moya/debian/ ./
```

---


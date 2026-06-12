---
title: "Ubuntu 10.04: I Lost A File In Terminal"
date: 2011-02-23
forum: General Help
---

### Post by SexySara on 2011-02-23
I moved a file named "Human1" in to "/usr/share/themes". I then tried to moved the file in to desktop by issuing this command...

```
sudo mv Human1 /Desktop
```Now when I go to Desktop, the "Human1" file is not there. Any clues where it could of gone and how to find it lol? I also tried the "locate" command in terminal but no good.

In case anyone is wondering, I am trying to familiarize myself with terminal commands and moving files back and fourth and such :)

I think the correct command would of been this right?
```
sudo mv Human1 Desktop
```

---

### Post by TeoBigusGeekus on 2011-02-23
There's no folder called /Desktop. The command should have been

```
sudo mv Human1 /home/username/Desktop
```


EDIT: 

```
sudo mv Human1 Desktop
```

This wouldn't have worked either.
I assume that you were in the /usr/share/themes folder.

It would have worked if you were in your home folder, but then you would have to change the path of the "from" directory, ie.

```
sudo mv /usr/share/themes/Human1 Desktop
```

---

### Post by hvbakel on 2011-02-23
You actually moved 'Human1' to the root of the filesystem and renamed it to 'Desktop'. The following command should do what you're looking for:

```
sudo mv /Desktop /home/USERNAME/Desktop/Human1
```

where you replace USERNAME with your username.

---

### Post by whatthefunk on 2011-02-23
If you go to a terminal and type:
```
cd /
```
```
ls
```
You should find your folder.

---

### Post by SexySara on 2011-02-23
> **TeoBigusGeekus said:**
> There's no folder called /Desktop. The command should have been

```
sudo mv Human1 /home/username/Desktop
```
EDIT: 

```
sudo mv Human1 Desktop
```This wouldn't have worked either.
I assume that you were in the /usr/share/themes folder.

It would have worked if you were in your home folder, but then you would have to change the path of the "from" directory, ie.

```
sudo mv /usr/share/themes/Human1 Desktop
``` Thank you very much, I guess practice makes improvement haha.

> **hvbakel said:**
> You actually moved 'Human1' to the root of the filesystem and renamed it to 'Desktop'. The following command should do what you're looking for:

```
sudo mv /Desktop /home/USERNAME/Desktop/Human1
```where you replace USERNAME with your username. I was wondering why I couldn't find but 2 files in the Desktop while in terminal when I know I had at least 10 of them. I did what you said and all is better now. Thank you soooo much!

> **whatthefunk said:**
> If you go to a terminal and type:
```
cd /
``````
ls
```You should find your folder. Yah I have that part down haha, thanks.

---


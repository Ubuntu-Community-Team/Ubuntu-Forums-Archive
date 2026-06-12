---
title: "Command"
date: 2010-01-10
forum: General Help
---

### Post by CEW11 on 2010-01-10
Does anyone know what the command would be in terminal to move a folder to a usb flash stick.
I cant do  it mnaually as it says I dont have permissions.

---

### Post by NoaHall on 2010-01-10
To bring up a file browser with permission -
```
gksudo nautlius
```
To copy the folder command wise
```
sudo cp -R /home/user/folder/ /media/drivename
```

---

### Post by blueridgedog on 2010-01-10
To move:

```
mv /path/to/directory /path/to/newlocation
```

This would move the directory and all contents into the directory specified.

If you do not have permissions for the move, you can precede the command with "sudo".   Note that moving system files in this fashion may break your system, so investigate why you don't have permission.

---

### Post by blueridgedog on 2010-01-10
> **NoaHall said:**
> 
```
sudo mv -R /home/user/folder/ /media/drivename
```

I don't think "-R" is supported by mv.

---

### Post by davec64 on 2010-01-10
> **blueridgedog said:**
> To move:

```
mv /path/to/directory /path/to/newlocation
```

This would move the directory and all contents into the directory specified.

If you do not have permissions for the move, you can precede the command with "sudo".   Note that moving system files in this fashion may break your system, so investigate why you don't have permission.

Jut adding to the above, I would "copy" rather than move just to be on the safe side first! Call me over cautious if you like :)

```
cp /path/to/directory /path/to/newlocation
```

---

### Post by NoaHall on 2010-01-10
> **davec64 said:**
> Jut adding to the above, I would "copy" rather than move just to be on the safe side first! Call me over cautious if you like :)

```
cp /path/to/directory /path/to/newlocation
```

cp needs the -R flag  :) Which is what I meant to wrote first :)

---

### Post by CEW11 on 2010-01-11
thanks for the help

---


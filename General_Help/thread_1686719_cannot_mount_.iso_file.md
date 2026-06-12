---
title: "cannot mount .iso file"
date: 2011-02-12
forum: General Help
---

### Post by Horomancer on 2011-02-12
I'm trying to mount an .iso containing archived text books
I made a mount point at /mnt/math with no trouble, but when I attempted to mount the .iso i get this error


```
horomancer@keeper:/mnt/math$ sudo mount /home/horomancer/documents/Research/130+\ Math\ Learning\ Books/mathbooks.iso  /mnt/math
mount: /home/horomancer/documents/Research/130+ Math Learning Books/mathbooks.iso is not a block device (maybe try `-o loop'?)

horomancer@keeper:/mnt/math$ sudo mount -o loop /home/horomancer/documents/Research/130+\ Math\ Learning\ Books/mathbooks.iso  /mnt/math
mount: /dev/loop0: can't read superblock

```

I got no clue on what this means.

---

### Post by wojox on 2011-02-12
You already created the directory?

```
sudo mkdir -p /mnt/math
```

Then:

```
sudo mount -o loop mathbooks.iso /mnt/math
```

```
cd /mnt/disk
```

```
ls -l
```

What is the location of the .iso?

---

### Post by asmoore82 on 2011-02-12
You may need to specify the filesystem type with `-t`
```
sudo mount -o loop -t iso9660 mathbooks.iso /mnt/math
```

---

### Post by Horomancer on 2011-02-13
I've made the dir already, though i do not think I used the -p argument

```
horomancer@keeper:~$ cd /mnt
horomancer@keeper:/mnt$ ls
lfs  math
horomancer@keeper:/mnt$ file math
math: directory
horomancer@keeper:/mnt$ 
```

I tried specifying the file system type, but get the same error

```

horomancer@keeper:~$ sudo mount -o loop -t iso9660 ./documents/Research/130+\ Math\ Learning\ Books/mathbooks.iso  /mnt/math
[sudo] password for horomancer: 
mount: /dev/loop0: can't read superblock

```

---

### Post by wojox on 2011-02-14
What is the name of the .iso and where is it located?

Can you burn it to a CD? Maybe it's a bad .iso.

---


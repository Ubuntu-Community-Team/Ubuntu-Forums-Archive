---
title: "Impossible to delete some files"
date: 2010-06-11
forum: General Help
---

### Post by Axio on 2010-06-11
Hi, I am using Ubuntu 10.04. I have a small HDD and I noticed that the weight of the folder .Trash-0/lost+found on my computer was of 2.6 gb.

I tried to delete the files in this folder, but it seems impossible. Even with using sudo I can't delete them because I am not authorized to do so.

The files in the folder are quite weird, there are folder and files named like this: #7614692, #7613635 etc. Their groups and their users are also quite weird: -1933023744, 1624453254... Even from a live cd it is not possible to delete them. Also the date of the files is ****ed up, example: 
- last access: "mar. 13 juil. 1943 15:26:11 CEST"
- last modification: "mer. 12 oct. 2022 15:59:51 CEST"

I recently upgraded this partition from ext3 to ext4, so I would guess that it comes from here. But I don't know if these files where there before or not.

---

### Post by bobcollard on 2010-06-11
> **Axio said:**
> Hi, I am using Ubuntu 10.04. I have a small HDD and I noticed that the weight of the folder .Trash-0/lost+found on my computer was of 2.6 gb.

I tried to delete the files in this folder, but it seems impossible. Even with using sudo I can't delete them because I am not authorized to do so.

The files in the folder are quite weird, there are folder and files named like this: #7614692, #7613635 etc. Their groups and their users are also quite weird: -1933023744, 1624453254... Even from a live cd it is not possible to delete them. Also the date of the files is ****ed up, example: 
- last access: "mar. 13 juil. 1943 15:26:11 CEST"
- last modification: "mer. 12 oct. 2022 15:59:51 CEST"

I recently upgraded this partition from ext3 to ext4, so I would guess that it comes from here. But I don't know if these files where there before or not.
You might try gksu "file manager" in Terminal: where "file Manager" is the name of yours, while mine is thunar, without the quotes.  There is a caution, delete only the contents of the folder, not the folder itself. Empty the trash while still at root.

---

### Post by Axio on 2010-06-11
It is not working.

---

### Post by bobcollard on 2010-06-11
> **Axio said:**
> It is not working.
I think you are correct about changing the formatting.  You may have to backup your home folder and reinstall the system to clean it up.  Unless someone else has a suggestion.

---

### Post by benson444 on 2010-06-11
This is a long shot, but perhaps the immutable attribute has somehow been set on the files. Try

```
lsattr filename
```

If there is a lower case i in the output then it has been set. I believe not even root can delete it then. Remove it with

```
sudo chattr -i filename
```

You will then be able to remove it. Not very likely, but worth a try.

---

### Post by Raizen44 on 2010-09-04
> **benson444 said:**
> This is a long shot, but perhaps the immutable attribute has somehow been set on the files. Try

```
lsattr filename
```If there is a lower case i in the output then it has been set. I believe not even root can delete it then. Remove it with

```
sudo chattr -i filename
```You will then be able to remove it. Not very likely, but worth a try.


Need some hel with this as well. I'm using the Ubuntu 10.04 netbook edition on my laptop. It was great at first. Then, I tried ripping a DVD using the Brasero application. I ripped two files that were failures (did not rip the entire DVD) so I deleted them. I've tried to delete them/empty my trash folder several times now, but they still can't be deleted. I keep getting an error saying that it was unable to delete the file. 

BTW, Ialso need help on something else. I was able to make a successful rip on one of them, but I can't transfer the file to my external HDD. when its almost over, I keep getting an error that says unable to trasfer file, file too large. I hope you guys can help as I'd like to fix this without reprogramming my laptop if its at all possible...

---


---
title: "move all of one type of files"
date: 2009-10-17
forum: General Help
---

### Post by kmrs75 on 2009-10-17
i have a graphics shop and all my fonts are scattered in my external HD 

i would like to do a search and move them to one folder 

but i dont want to search my local drives just the external. 

if the file that i would like to move is a *.ttf file and move it to desktop folder called TTFFONT how do i go about doing this 

there is sub folders

---

### Post by coldReactive on 2009-10-17
There is no recursive option for **mv**, so you'll have to move it all manually as you find them.

that said, you can (I'm sure) move all of one type of file using a wildcard: ***.ttf**

---

### Post by kmrs75 on 2009-10-17
well i found this thread but its a copy not a move. is there was something similar that was a move 

[http://ubuntuforums.org/showthread.php?t=671220]("http://ubuntuforums.org/showthread.php?t=671220")

---

### Post by diesch on 2009-10-17
```

find /media/my_external_hd -name \*.ttf -exec mv  {}  ~/Desktop/TTFFONT \;

```

---

### Post by Neezer on 2009-10-17
I don't know about the recursive ability of mv, or what it even means, but you might try

mv *.tff TIFFONT

Remember that it is good practice to do something this: 
```

$ls -a *.tff

```
before you actually run any commands on it. The above should show you every file with a .tff ending...

if the **mv** command doesn't work, you might try the **cp** command. Then you will copy all of the files into the folder....but you are stuck with all of the originals still in their original place....if you try the **rm** command after copying them, you will end up removing every .tff file, and I'm sure that isn't what you want to happen.

I'm sure there is a way to exclude your TIFFONT file in the **rm** command, but I don't know what it is.


EDIT: turns out I don't have any idea what I'm talking about and that command won't work. It only searches your home directory.....if your files aren't there, you might go to the /etc directory and run the command. Not too sure, I hope I got you going on the right track though. As long as you don't use the **rm** command you won't ruin anything though.

---

### Post by StuartN on 2009-10-17
> **diesch said:**
> ```
find /media/my_external_hd -name \*.ttf -exec mv  {}  ~/Desktop/TTFFONT \;
```

This is definitely the simplest way to do it.

If it is the kind of thing that you do rarey, and you want to hide the command-line, then install a file manager like Krusader alongside Nautilus. It has a wealth of options to find a group of files, copy or move them and check whether two different directories have the same contents (synchronise).

---

### Post by kmrs75 on 2009-10-17
this is what i get 


ken@ken-desktop:~$ find /media/disk -name \*.ttf -exec mv  {}  ~/Desktop/TTFFONT \;
find: `/media/disk/lost+found': Permission denied
find: `/media/disk/root': Permission denied
find: `/media/disk/etc/ssl/private': Permission denied
find: `/media/disk/etc/chatscripts': Permission denied
mv: cannot remove `/media/disk/etc/alternatives/ttf-japanese-gothic.ttf': Permission denied
find: `/media/disk/etc/ppp/peers': Permission denied
ken@ken-desktop:~$

---

### Post by coldReactive on 2009-10-17
put sudo before the command:

```
sudo find /media/my_external_hd -name \*.ttf -exec mv  {}  ~/Desktop/TTFFONT \;
```

You will be asked for a password, typing the password will not move the cursor (this is normal, just type the password and hit enter. Backspace is not allowed when typing the password, so make sure it's right the first time)

---


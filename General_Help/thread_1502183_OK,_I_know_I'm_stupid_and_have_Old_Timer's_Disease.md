---
title: "OK, I know I'm stupid and have Old Timer's Disease, but"
date: 2010-06-05
forum: General Help
---

### Post by GuiGuy on 2010-06-05
... why do I get a "cannot stat" error on this

cp -Rv /mnt/music/Blues/*.mp3 /media/mymp3s

/mnt/music/Blues/ is valid and contains valid *.mp3 files with read/write permissions for the user

/media/mymp3s is a valid and working mounted device.

TIA

---

### Post by wojox on 2010-06-05
A cannot stat error literally means the files do not exist.

---

### Post by XubuRoxMySox on 2010-06-05
Install ubuntu restricted-extras (or xubuntu restricted-extras, or kubuntu restricted-extras, depending on which version you're using) and your MP3s will play!

Find it in Synaptic Package Manager.

have fun,
Robin

---

### Post by GuiGuy on 2010-06-05
> **dixiedancer said:**
> Install ubuntu restricted-extras (or xubuntu restricted-extras, or kubuntu restricted-extras, depending on which version you're using) and your MP3s will play!

Find it in Synaptic Package Manager.

have fun,
Robin

Please read my post; I am trying to copy mp3 files to a device:

> cp -Rv /mnt/music/Blues/*.mp3 /media/mymp3s

---

### Post by GuiGuy on 2010-06-05
> **wojox said:**
> A cannot stat error literally means the files do not exist.

That's what a I thought. But the directory I want to copy from has literally hundreds of .mp3 files in it. 

Or isn't *.mp3 a valid wild card combination?

---

### Post by amauk on 2010-06-05
do you have write access for /media/mymp3s

Check the owner & group
```
ls -ld /media/mymp3s
```

and if applicable
```
sudo chown user:user /media/mymp3s
```
obviously change **user** to suit

---

### Post by GuiGuy on 2010-06-05
> **amauk said:**
> do you have write access for /media/mymp3s

Check the owner & group
```
ls -ld /media/mymp3s
```

and if applicable
```
sudo chown user:user /media/mymp3s
```
obviously change **user** to suit

Yea, thanks. I'd done all the obvious stuff before posting here. 

I'm copying using a file manager now (nautilus). I'm just annoyed that I can't do this from a shell. 

Oddly 

cp -Rv /mnt/music/Blues/* /media/mymp3s

works fine, but I get all files that way. I only wanted the mp3's. :(

---

### Post by sanderd17 on 2010-06-05
you don't need a -R option if you dont copy directories (and you aren't sindce all your files end on .mp3)

maybe that helps.

---

### Post by GuiGuy on 2010-06-05
> **amauk said:**
> do you have write access for /media/mymp3s


Yes. My user account is the owner and permissions are 777 in any case.

---

### Post by sisco311 on 2010-06-05
*.mp3 only matches the mp3 files from /mnt/music/Blues/. it doesn't match the mp3s from the subdirectories.

If you want to copy the files recursively, then try something like:
```

shopt -s globstar
cp -v /mnt/music/Blues/**/*.mp3 /media/mymp3s
```
See:
```
man bash | less +/globstar
```

or:
```
find /mnt/music/Blues -type f -iname *.mp3 -exec cp -v '{}' /media/mymp3s \;

```

See: ```
man find
```

---

### Post by GuiGuy on 2010-06-05
> **sanderd17 said:**
> you don't need a -R option if you dont copy directories (and you aren't sindce all your files end on .mp3)

maybe that helps.

... but there's no recursion without the -R option is there? 

Or isn't it possible to use recursion when using semi explicit filenames?

---

### Post by GuiGuy on 2010-06-05
> **sisco311 said:**
> *.mp3 only matches the mp3 files from /mnt/music/Blues/. it doesn't match the mp3s from the subdirectories.

If you want to copy the files recursively, then try something like:


Thank you. That it did it!

Cheers

---

### Post by wojox on 2010-06-05
> Or isn't *.mp3 a valid wild card combination?

Yeah it is.

Your using sudo right?

---

### Post by sanderd17 on 2010-06-05
> **GuiGuy said:**
> Thanks you. That it did it!

Cheers
I thought all your mp3's were in the same folder, no subdirectories.

---

### Post by wojox on 2010-06-05
Cool mark it solved for future reference. :)

---

### Post by GuiGuy on 2010-06-05
> **wojox said:**
> Cool mark it solved for future reference. :)

I did, I did mark it as solved :biggrin:

NB: Didn't solve my "stupid" problem or Old Timer's Disease, but .... <sigh>

---

### Post by GuiGuy on 2010-06-05
Thanks everyone.

---

### Post by wojox on 2010-06-05
> **GuiGuy said:**
> I did, I did mark it as solved :biggrin:

NB: Didn't solve my "stupid" problem or Old Timer's Disease, but .... <sigh>

You must have been maring it while I was typing. :)

---

### Post by sisco311 on 2010-06-05
If memory serves, in DOS and Windows (cmd.exe) you can use the xcopy command to copy specific file types recursively:
```
xcopy /s *.htm foo
```

It's because,  in DOS, wildcards are handled by the commands themselves, while in unix/linux are handled by the shell.

EDIT:
You can read a more detailed explanation here:
[http://www.mcwalter.net/technology/shell/recursive.html](http://www.mcwalter.net/technology/shell/recursive.html)

EDIT2:
> **GuiGuy said:**
> Thanks everyone.
You are welcome!

---


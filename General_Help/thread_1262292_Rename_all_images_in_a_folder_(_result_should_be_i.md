---
title: "Rename all images in a folder ( result should be img_1.png, img_2.jpg, etc. ) ?"
date: 2009-09-09
forum: General Help
---

### Post by credobyte on 2009-09-09
Ok, all I need is a simple ( I assume it's not that hard ) bash or Python script that will rename all images in my Pictures folder ( no need for recursive stuff ).

As an example:
```
Cool wallpaper 25(2).png
abstract_by_zed.jpg
#niceone.png
```

Result:
```
image_1.png
image_2.jpg
image_3.png
```

So .. are there any bored bash masters browsing through this forum at the moment ? :p

---

### Post by Vaphell on 2009-09-09
i googled a bit and found something like that

```
i=0; for file in *.jpg; do mv "$file" $(printf "image_%0.3d.jpg" $i); i=$((i+1)); done
```
at [http://stackoverflow.com/questions/880467/renaming-a-set-of-files-to-001-002-on-linux](http://stackoverflow.com/questions/880467/renaming-a-set-of-files-to-001-002-on-linux)

you'd have to run it for all extensions because it's not foolproof and wouldn't keep extensions if you'd run it for all files. Also if you don't want to have 001.jpg and 001.png you'd have to adjust counter (i variable) accordingly. Probably there is some way to upgrade that command chain to work correctly in 1 go but i don't know how to reliably extract extension from the $file variable.

---

### Post by credobyte on 2009-09-09
> **Vaphell said:**
> i googled a bit and found something like that

```
i=0; for file in *.jpg; do mv "$file" $(printf "image_%0.3d.jpg" $i); i=$((i+1)); done
```at [http://stackoverflow.com/questions/880467/renaming-a-set-of-files-to-001-002-on-linux](http://stackoverflow.com/questions/880467/renaming-a-set-of-files-to-001-002-on-linux)

you'd have to run it for all extensions because it's not foolproof and wouldn't keep extensions if you'd run it for *all files. Also if you don't want to have 001.jpg and 001.png you'd have to adjust counter (i variable) accordingly

I found a few similar commands before even thinking about posting this thread, however, I need a way to keep the extension ( so I should not run it multiple times and verify if everything went right ). I've +/- 5000 files sitting here and waiting for this to be done, so .. it's pretty insane to check, if everything is as it should be, manually.

---

### Post by Vaphell on 2009-09-09
```
i=0; for file in *; do extn=${file##*.}; i=$((i + 1)); newname=$(printf 'image_%0.4d.%s' "$i" "$extn"); mv $file $newname; done
```
run from a directory in question should do the trick, test it first on some small sample to see if it works. You can replace mv with echo to see input - output filenames first.

---

### Post by credobyte on 2009-09-09
By the first, I got a couple of errors ( just an example ):
```
mv: target `image_0105.jpg' is not a directory

```Secondly, some of the files were not renamed ( file names contain spaces, indeed, no special characters ).
Anyway, looks like it did the trick in general, however, would be nice if someone could tweak it so it would rename all files :)

---

### Post by kaibob on 2009-09-09
I have an alternate suggestion. In your example, you did not pad the file number with zero's. This makes things a bit easier. Also, I personally would not be comfortable trusting 5,000 photos to a simple bash command. So, instead of overwriting the source files with the move command, I would use a copy command and place the renamed photos in a different directory. Then, if all goes well, you can then delete the source directory.

You have to run the following command while in the directory that contains the source files. Also, you have to change /output/directory/ to whatever you choose. 

```
count=1 ; for file in * ; do ext="${file##*.}" ; cp "$file" "/output/directory/image_${count}.${ext}" ; count=$((count+1)) ; done
```

BTW, I tried this command on the filenames in your post, and the command worked with one exception. The file abstract_by_zed.jpg was renamed to image_1.jpg rather than image_2.jpg and Cool wallpaper 25(2).png was renamed to image_1.png rather than image2.png. This is a result of the way bash order files.

---

### Post by Vaphell on 2009-09-09
I reworked that uber command line combo to 1. skip directories 2. support spaces
behold :D

```
i=0; for f in *; do if [ -f "$f" ]; then extn=${f##*.}; i=$((i+1)); newname=$(printf 'image_%0.4d.%s' "$i" "$extn" ); echo $f $newname; mv "$f" "$newname"; fi; done

```

test it somewhere first though

---


---
title: "Make folder names out of file names, move files"
date: 2011-06-26
forum: General Help
---

### Post by kainalu on 2011-06-26
Hello all,

I'm trying to make a script that will convert my large library of movies to folders. As it is, every video has an info file, a fanart pic, a cover image, and the video. 

I want to make a script that: 

1. will look at the video's name, and make a folder with that name, but without the extension

2. will move the videos, and their support files, into that folder.

The videos are named [video name] ([year]).[ext] like "Avatar (2009).avi". The support files are jpg's, tbn's and nfo's

Thanks!

---

### Post by Ozymandias_117 on 2011-06-26
You may have to mess with it some, but here's a basic idea.

```
for FILE in $(ls | grep avi)
do
[INDENT]FILENAME=$(echo $FILE | gawk '{ split($0,tmp,"."); print tmp[1] }')[/INDENT]
[INDENT]mkdir tmp[/INDENT]
[INDENT]mv $FILE $FILENAME.jpg $FILENAME.tbn $FILENAME.nfo tmp[/INDENT]
[INDENT]mv tmp $FILENAME[/INDENT]
done

```

---

### Post by kainalu on 2011-06-27
It works great, but is there any way to make it work with files that have spaces in them? 

Thanks!

---

### Post by nothingspecial on 2011-06-27
```
for FILE in *.avi; do mkdir "${FILE%.*}"; mv "${FILE%.*}".* "${FILE%.*}"; done
```

I'd test it first.

---

### Post by Ozymandias_117 on 2011-06-27
> **kainalu said:**
> It works great, but is there any way to make it work with files that have spaces in them? 

Thanks!

Put quotes around all the places that I've used $FILE and $FILENAME (Make sure the closing quote is at the end after the extension)

---

### Post by Ozymandias_117 on 2011-06-27
Just read the previous poster's code and made me realize one line was overcomplicated.

```
for FILE in ./*.avi
do
[INDENT]FILENAME=$(echo $FILE | gawk '{ split($0,tmp,"."); print tmp[1] }')[/INDENT]
[INDENT]mkdir tmp[/INDENT]
[INDENT]mv "$FILENAME.*" tmp[/INDENT]
[INDENT]mv tmp "$FILENAME"[/INDENT]
done

```

---

### Post by sisco311 on 2011-06-27
> **Ozymandias_117 said:**
> Just read the previous poster's code and made me realize one line was overcomplicated.

```
for FILE in $(ls | grep avi)
do
[INDENT]FILENAME=$(echo $FILE | gawk '{ split($0,tmp,"."); print tmp[1] }')[/INDENT]
[INDENT]mkdir tmp[/INDENT]
[INDENT]mv "$FILENAME.*" tmp[/INDENT]
[INDENT]mv tmp "$FILENAME"[/INDENT]
done

```

Please check out:  [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by kainalu on 2011-06-28
Very helpful, and worked like a charm. Thanks for all the help. Marking solved.


EDIT : 

As an educational experience for me, What would I have do to to make a script that would go through the folder tree this made, and copy all the tbn files to folder.jpg in the same folder?

---

### Post by Ozymandias_117 on 2011-06-28
> **kainalu said:**
> Very helpful, and worked like a charm. Thanks for all the help. Marking solved.


EDIT : 

As an educational experience for me, What would I have do to to make a script that would go through the folder tree this made, and copy all the tbn files to folder.jpg in the same folder?

You want to make a folder named "folder.jpg" and move the *.tbn files into it?

---

### Post by kainalu on 2011-06-29
No, I'd like to go to all the folders and copy *.tbn to folder.jpg, but they can stay in the folder.

like what this does, but in all the movie folders that were created :
```
cp ./127\ hours/127\ hours.tbn ./127\ hours/folder.jpg
```


I tried this

```
find ./ -not \( -type d -name ".?*" -prune \) \
	 -iname "*.tbn" -exec \
	 cp {} `basename {}`/folder.jpg \;
```



but I get errors cp: target `./folder.jpg' is not a directory

---

### Post by nothingspecial on 2011-06-29
If I understood you correctly the first time, you should now have a load of folders like this

```
Avatar(2009)
```

each containing 3 files

```
Avatar(2009).avi    Avatar(2009).nfo  Avatar(2009).tbn
```

If you want another file in each of those directories, that is a copy of the tbn file, but all named folder.jpg, then this will do it

```
for d in *; do cp "$d"/*.tbn "$d"/folder.jpg; done
```

---

### Post by kainalu on 2011-06-29
That worked great. I have XBMC & cover thumbnailer installed, and now all my movies have the information and movie all in one folder & the folder icon in Nautilus replaced with the DVD cover art. :popcorn:

It worked awesome. Thanks for the major help!

---

### Post by nothingspecial on 2011-06-29
No problem \\:D/

---


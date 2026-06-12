---
title: "Pseudo Complex File Renaming"
date: 2010-03-29
forum: General Help
---

### Post by colli419 on 2010-03-29
Hello All:

I would like to know if there is a way to take a bunch of files in a directory and put them all individually in their own directories. I have a bunch of movie files that I would like to move to directories with the same name as the file sans file extension (e.g. Batman.avi --> Batman/Batman.avi). Hope someone can help.

Thanks,
Michael

---

### Post by cjhabs on 2010-03-29
> **colli419 said:**
> Hello All:

I would like to know if there is a way to take a bunch of files in a directory and put them all individually in their own directories. I have a bunch of movie files that I would like to move to directories with the same name as the file sans file extension (e.g. Batman.avi --> Batman/Batman.avi). Hope someone can help.

Thanks,
Michael

If all the files have the same extension, avi for example, you can do:

for file in *.avi; do mkdir `basename $file .avi`; mv $file `basename $file .avi`; done

Repeat for other extensions, replacing all occurrances of .avi with whatever the other extensions are.

---

### Post by kaibob on 2010-03-30
The suggestion by cjhabs works great. Just for the sake of completeness, I thought I would suggest an alternative that utilizes bash parameter expansion. 

```
for file in *.avi ; do mkdir "${file%.avi}" ; mv "$file" "${file%.avi}" ; done
```

---

### Post by colli419 on 2010-03-30
Thanks for your help the final script ended up looking like this:
(Suffice it to say, I added a bit of other automagicness...)
```
#!/bin/bash
for file in *.avi;
do target=`echo "$file"|tr -s ' '|tr ' ' '-'`;
mv "$file" "$target";
interim=`basename $target .avi`;
newdir=`echo "$interim"|tr -s '-'|tr '-' ' '`;
mkdir "$interim";
mv "$target" --target-directory=$interim;
cd "$interim";
	for file in *.avi;
	do target=`echo "$file"|tr -s '-'|tr '-' ' '`;
	mv "$file" "$target";
	cd ..;
	done;
mv "$interim" "$newdir";
done
```

---


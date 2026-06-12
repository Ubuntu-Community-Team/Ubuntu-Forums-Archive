---
title: "How do I....in terminal"
date: 2012-05-14
forum: General Help
---

### Post by Keybored67 on 2012-05-14
Ive got a list of files in a txt file, the actual files are spread over multiple folders.  Is there a way in terminal to have the txt file read and copy those files into a folder?

---

### Post by roelforg on 2012-05-14
Look into how find, grep and xargs work.
You're not very clear on what you're trying to do, so thats all i can do to help you.
(ex. do you want every txt file copied? or only the ones with certain strings in names/contents? etc)

---

### Post by Keybored67 on 2012-05-14
I want to cherry pick some pictures that in different folders, so I made a list of pictures (in filename format) in a txt file.  I want to find (gather) and copy the files named in the list into another folder.

---

### Post by diesch on 2012-05-14
```
xargs cp -t your_destination_folder < files.txt
``` should work

---

### Post by roelforg on 2012-05-14
> **Keybored67 said:**
> I want to cherry pick some pictures that in different folders, so I made a list of pictures (in filename format) in a txt file.  I want to find (gather) and copy the files named in the list into another folder.

Assuming there's a picture a line with valid path:
ex:
```

~/Pictures/a.png
/media/usb/b.png

```
and your target is ~/result
```

mkdir -p ~/result
cp `cat ~/mylist.txt` ~/result/

```

---

### Post by diesch on 2012-05-14
> **roelforg said:**
> 
```

mkdir -p ~/result
cp `cat ~/mylist.txt` ~/result/

```

This doesn't work for filenames containing spaces

---

### Post by Vaphell on 2012-05-14
```
while read f; do cp "$f" destination_dir; done < list.txt
```

---

### Post by roelforg on 2012-05-15
> **diesch said:**
> This doesn't work for filenames containing spaces
 
Correct,
i assumed the list contains entries like this:
```

/path/with\ escaped\ spaces/file.ext

```

---

### Post by Keybored67 on 2012-05-15
Tried those with limited success.  diesch suggestion was able to read the filenames from the txt file, but it wouldn't drill into the sub folders to the files, so I cant comment on the copy portion lol.
One of the others with a bit of "lets see what this will do..." I managed to get it to copy something,,,everything, what I needed and what I didnt...so I dont know if it was able to takes its cues from the txt
My eyes started to get blurry so I attacked another front for a while with even less success.  I am still working on it though.
Thanks for your replies.

---

### Post by roelforg on 2012-05-15
> **Keybored67 said:**
> Tried those with limited success.  diesch suggestion was able to read the filenames from the txt file, but it wouldn't drill into the sub folders to the files, so I cant comment on the copy portion lol.
One of the others with a bit of "lets see what this will do..." I managed to get it to copy something,,,everything, what I needed and what I didnt...so I dont know if it was able to takes its cues from the txt
My eyes started to get blurry so I attacked another front for a while with even less success.  I am still working on it though.
Thanks for your replies.

If you want to copy all the png files from a directory that contains several subdirs and other formats, use something like this:
```

find /path/to/root/image/dir -name *.png

```
It'll output a list of all the png files, with full path.

---

### Post by Keybored67 on 2012-05-15
Everything is in the same format but each file name is unique with no spaces, is why Im trying to read the list from txt...some 600 or so files out of 3000 separated into 5 different folders...I was just contimplating copying everything over into one folder and re running those and see what happens

---

### Post by Vaphell on 2012-05-15
have you tried *while read f; echo "$f"; cp -v -- "$f" destination_dir; done < file.txt*
?
care to give few examples of entries in the file?

---

### Post by Keybored67 on 2012-05-15
That one gave me 

bash: syntax error near unexpected token `done'

Pices have been renamed to dates... ones I take today would be 2012-05-15-001.jpg  
2012-05-15-002.jpg...ect

---

### Post by Vaphell on 2012-05-15
crap i missed **do**
```
while read f; **do** echo "$f"; cp -v -- "$f" destination_dir; done < file.txt
```

---

### Post by Keybored67 on 2012-05-15
that gave me

cp - v -- filename /destination_dir

for every file in the text list, but no copies

---

### Post by Vaphell on 2012-05-16
like literally? i guess you made a typo and missed **;**

while read f;   = read data line by line into f )
do    = start block of commands for each line
  echo "$f";  print the file/line f
  cp -v -- "$f" <dest>;   = copy file f do existing dest directory in verbose mode
done < file.txt   = end block, use the data from file to fuel the loop


you should ctrl+c / shift+ctrl+v in terminal so you avoid typos
or highlight it here and middle click in terminal (linuxy copy-paste). Sloppiness with typing won't get you far.

you could paste here some terminal output what exactly you run and what you get
(again highlight-select/middleclick or ctrl+shift+c/ctrl+v)

---

### Post by Keybored67 on 2012-05-18
That kinda worked, had to run it from each folder, but it did copy the files I wanted into a diff folder.

---


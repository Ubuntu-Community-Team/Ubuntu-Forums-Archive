---
title: "Quick way to rename files?"
date: 2010-02-08
forum: General Help
---

### Post by mellowd on 2010-02-08
I know it can be done, I just forgot how.

I don't want to change the extension, that's easy.

Let's say I have a bunch of files like so:

file1.jpg
file2.jpg
file3.jpg

I now want to rename all of them as follows:

eg.1.jpg
eg.2.jpg
eg.3.jpg

and so on.

Anyone got a command using a regular expression that could help?

---

### Post by t4thfavor on 2010-02-08
You could probably get by with this script run from within the target directory.

```

i=1;
for file in ${ls *.jpg};do

     mv $file eg.${i}.jpg;
     i=$i+1;
done

```

---

### Post by mellowd on 2010-02-08
Thanks. I actually went more complicated and did it like so:

```
for file_name in `ls E*`; do echo "The file:" $file_name ; new_file_name=$(echo $file_name | sed 's/E/S01.E/g') ; echo "New name:" $new_file_name ; mv -v $file_name $new_file_name; done
```

I've recently got my xbmc running and so wanted to quickly rename single series episodes from E01 to S01.E01 and so on so it would correctly pick them up.

Works quite nicely:

```
mellowd@XBMCLive:/media/1TB/tv.shows/FLCL$ ls -lha
total 2.1G
drwxrwxrwx 1 root root 4.0K 2010-02-08 14:41 .
drwxrwxrwx 1 root root  28K 2010-02-08 13:57 ..
-rwxrwxrwx 1 root root 352M 2007-02-24 14:27 E01.ogm
-rwxrwxrwx 1 root root 348M 2007-02-24 13:47 E02.ogm
-rwxrwxrwx 1 root root 349M 2007-02-24 14:17 E03.ogm
-rwxrwxrwx 1 root root 351M 2007-02-24 14:27 E04.ogm
-rwxrwxrwx 1 root root 310M 2007-02-24 14:27 E05.ogm
-rwxrwxrwx 1 root root 392M 2007-02-24 14:24 E06.ogm
mellowd@XBMCLive:/media/1TB/tv.shows/FLCL$ for file_name in `ls E*`; do echo "The file:" $file_name ; new_file_name=$(echo $file_name | sed 's/E/S01.E/g') ; echo "New name:" $new_file_name ; mv -v $file_name $new_file_name; done
The file: E01.ogm
New name: S01.E01.ogm
`E01.ogm' -> `S01.E01.ogm'
The file: E02.ogm
New name: S01.E02.ogm
`E02.ogm' -> `S01.E02.ogm'
The file: E03.ogm
New name: S01.E03.ogm
`E03.ogm' -> `S01.E03.ogm'
The file: E04.ogm
New name: S01.E04.ogm
`E04.ogm' -> `S01.E04.ogm'
The file: E05.ogm
New name: S01.E05.ogm
`E05.ogm' -> `S01.E05.ogm'
The file: E06.ogm
New name: S01.E06.ogm
`E06.ogm' -> `S01.E06.ogm'
mellowd@XBMCLive:/media/1TB/tv.shows/FLCL$ ls -lha
total 2.1G
drwxrwxrwx 1 root root 4.0K 2010-02-08 14:41 .
drwxrwxrwx 1 root root  28K 2010-02-08 13:57 ..
-rwxrwxrwx 1 root root 352M 2007-02-24 14:27 S01.E01.ogm
-rwxrwxrwx 1 root root 348M 2007-02-24 13:47 S01.E02.ogm
-rwxrwxrwx 1 root root 349M 2007-02-24 14:17 S01.E03.ogm
-rwxrwxrwx 1 root root 351M 2007-02-24 14:27 S01.E04.ogm
-rwxrwxrwx 1 root root 310M 2007-02-24 14:27 S01.E05.ogm
-rwxrwxrwx 1 root root 392M 2007-02-24 14:24 S01.E06.ogm
```

---

### Post by kaibob on 2010-02-09
Glad you got things working as you want. I thought I would mention that a simpler alternative--which is perhaps what you originally had in mind--is the rename command. The following is an example that utilizes the files in your second post:

> $ rename -v 's//S01./' *.ogm
E01.ogm renamed as S01.E01.ogm
E02.ogm renamed as S01.E02.ogm
E03.ogm renamed as S01.E03.ogm
E04.ogm renamed as S01.E04.ogm
E05.ogm renamed as S01.E05.ogm

---

### Post by mellowd on 2010-02-09
Thanks kaibob. Always handy to know more of 1 way to do things.

---

### Post by t4thfavor on 2010-02-11
Everybody knows that programming something in a script is intended to make it more complicated :) Glad you got it working, It looks like your method makes more sense if you are renaming episodes, and not jpg's.

---

### Post by jflaker on 2010-02-11
Also, there is a gui called PyRenamer which will rename files based on patterns....It is in the repositories.

---

### Post by mellowd on 2010-02-11
Thanks jflaker, but I have no gui on my machine. Handy to know though

---


---
title: "terminal: how can i cp *.txt files folder &amp; sub folders"
date: 2011-09-08
forum: General Help
---

### Post by bigdee973 on 2011-09-08
how can i copy all txt files from a folder including the ones inside sub directories using terminal?  how could i also remove txt files from a folder including its sub directories using terminal?

cp *.txt .....
rm *.txt ....

---

### Post by haqking on 2011-09-08
> **bigdee973 said:**
> how can i copy all txt files from a folder including the ones inside sub directories using terminal?  how could i also remove txt files from a folder including its sub directories using terminal?

cp *.txt .....
rm *.txt ....

cp /path/*.txt /path

 same with rm

you probably want to do it recursively though ?

see man cp
man rm

---

### Post by bigdee973 on 2011-09-10
> **haqking said:**
> cp /path/*.txt /path

 same with rm

you probably want to do it recursively though ?

see man cp
man rm

i dont want to delete the folders..just the files in the folder.. and i wanna copy and paste just the files not the folders...is the way u explained it the right way to do it or will it include the folders?

---

### Post by sisco311 on 2011-09-10
In bash 4, you can use the globstar option:
```
shopt -s globstar
cp **/*.txt /path/to/dest
```

when the globstar shell option is enabled, the glob ** expands to all files and directories found recursively under the current directory, and **/ to all directories. As of 4.0.28, combinations like foo/**/*.txt work, but **.txt and foo** do not.

See also:  [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by haqking on 2011-09-10
> **sisco311 said:**
> In bash4, you can use the glo**b**star option:
```
shopt -s globstar
cp **/*.txt /path/to/dest
```when the globstar shell option is enabled, the glob ** expands to all files and directories found recursively under the current directory, and **/ to all directories. As of 4.0.28, combinations like foo/**/*.txt work, but **.txt and foo** do not.

See also:  [http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)


nice, interesting, wasnt familiar with that.

Your initial globstar has a typo ;-)

---

### Post by holiday on 2011-09-10
You want to flatten the contents of the sub-directories? So you have

dirA
--a.txt
--dirB
----b.txt

and you want to get to 

dirTxt
--a.txt
--b.txt

If that's what you want then do this:

$ find dirA -name '*.txt' | xargs -i mv '{}' dirTxt

find will list recursively all the .txt files under dirA, the pipe will pass each of those to xargs which will execute the mv.  Make sure that dirTxt exists or you'll end up with one text file named dirTxt.

---

### Post by sisco311 on 2011-09-10
> **holiday said:**
> You want to flatten the contents of the sub-directories? So you have

dirA
  a.txt
  dirB
    b.txt

Where dirB is a subdirectory of dirA (the formatting doesn't show this)


and you want to get to 

dirTxt
  a.txt
  b.txt

If that's what you want then do this

$ find dirA -name '*.txt' | xargs -i mv '{}' dirTxt

find will list recursively all the .txt files under dirA, the pipe will pass each of those to xargs which will execute the mv.

This one will fail with files with newlines in their name. I know they aren't  common but for any chance it's much safer to use something like:

```
find ./ OPTIONS -print0 | xargs -0 COMMAND
```

find also has a -exec option and cp can copy multiple files, so I would go with something like:
```
find ./ -name \*.txt -type f -exec cp -b -t /path/to/dest '{}' +
```

---

### Post by bigdee973 on 2011-09-24
i tried removing files in the methods you used i wasnt able to do it...i need to remove text files within a folder and its sub directories please help....just the text files...not the folders...

---

### Post by holiday on 2011-09-24
> **bigdee973 said:**
> i tried removing files in the methods you used i wasnt able to do it...i need to remove text files within a folder and its sub directories please help....just the text files...not the folders...

The command I gave you will not remove folders. It touches only files that end with '.txt' If you have newlines in your filenames then you are an extraordinary bird and so are probably accustomed to intractable problems.

Try the find

$ find . -name '*.txt' and watch the listing. You won't see any folders. 


$ find dirA -name '*.txt' | xargs -i mv '{}' dirTxt

You can use -exec if you want, but I prefer xargs. It's a good command to get used to. Once you know it, you will find yourself using it often.

---

### Post by bigdee973 on 2011-10-16
the find option worked for me thanks. i made an error thats why it didnt work but find -type f -name "*.txt" -exec rm -rf '{}' \; worked good for me thanks so much guys

---

### Post by bigdee973 on 2011-10-16
the find option worked for me thanks. i made an error thats why it didnt work but find -type f -name "*.txt" -exec cp /home '{}' \; worked good for me thanks so much guys

---

### Post by sisco311 on 2011-10-16
> **bigdee973 said:**
> the find option worked for me thanks. i made an error thats why it didnt work but find -type f -name "*.txt" -exec cp /home '{}' \; worked good for me thanks so much guys

You are welcome!

The -type test should go after the  -name test in order to avoid having to call stat(2) on every file. Also cp can copy multiple files. You can use the **-exec command {} +** syntax to copy a set of file instead of invoking cp on each matched file.

---

### Post by bigdee973 on 2011-10-17
thank you i will 'find -name "*.txt" -type f' instead hmm what is stat(2)? what does that mean and what do u mean i can use the -exec command {} + syntax to copy a set of file instead of invoking cp on each matched file... give me an example please if you may.

---

### Post by sisco311 on 2011-10-18
stat (2 refers to the man section: **man 2 stat**) is a function provided by the kernel used by find to check if a file is a regular file, directory, symbolic link, character device, etc.

If you put the -type test first, then find will check each file in the directory and its subdirectories. If it comes after the -name test, then only the .txt files will be checked. 


If you use **-exec command {} \;** the command is invoked for each matched file:

command file1.txt
command file2.txt
command file3.txt

with **-exec command {} +** the command is invoked for a set of files:
command file1.txt file2.txt file3.txt

---

### Post by bigdee973 on 2011-10-19
> **sisco311 said:**
> stat (2 refers to the man section: **man 2 stat**) is a function provided by the kernel used by find to check if a file is a regular file, directory, symbolic link, character device, etc.

If you put the -type test first, then find will check each file in the directory and its subdirectories. If it comes after the -name test, then only the .txt files will be checked. 


If you use **-exec command {} \;** the command is invoked for each matched file:

command file1.txt
command file2.txt
command file3.txt

with **-exec command {} +** the command is invoked for a set of files:
command file1.txt file2.txt file3.txt

1.so 'find -type f -name "*.txt"' will look in current directory and sub directories while 'find -name "*.txt" -type f' will just look in current directory? 

2. and are you basically saying '-exec command {} \;' processes more slower? while '-exec command {} +; is faster?  thats the idea here?  it makes common sense that it does but in this case of cp are their any problems doing it one way from another u know...

---


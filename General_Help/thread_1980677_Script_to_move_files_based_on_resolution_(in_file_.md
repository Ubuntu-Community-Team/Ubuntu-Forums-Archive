---
title: "Script to move files based on resolution (in file name)"
date: 2012-05-15
forum: General Help
---

### Post by angryhomer17 on 2012-05-15
I have a lot of jpg images in one directory that have resolutions of 500px or 1000px. Most of the images are both 500px and 1000px. They have the same file name except for a _500 or _1000 at the end. E.g. xyz_500.jpg, xyz_1000.jpg and abc_500.jpg, abc_1000.jpg. The problem is some of the images are only 500px and don't have their higher resolution 1000px complement.

I'd like a script that moves all the 500px images that have a 1000px complement into another directory. If a 500px image doesn't have a 1000px complement leave it alone. 

So...

if xyz_500.jpg has xyz_1000.jpg
then  mv xyz_500.jpg ~/folder2
else do nothing and go to next file

Thanks.

---

### Post by imachavel on 2012-05-15
..................

---

### Post by imachavel on 2012-05-15
sorry for my first ******** reply. This is getting a lot closer to what you want. So you want either tags or an entire script that will copy files from one directory to another based on a pre specified label parameter? I'm googling as hard as I can, when I have an answer, I'll let you know

[http://www.basicconfig.com/linux/how_to_copy_files_directory_linux](http://www.basicconfig.com/linux/how_to_copy_files_directory_linux)

ok if you implemented the correct directory would this work for you?:

for files in *; do echo $files | grep "_500; done
>

my mistake, corrected:

for files in xyz/*; do echo $files | grep "_500"; done

try it and post the syntax
Ok forget that another ****** response, one second now and I'll have the right syntax:

and here we are, the command works, so you need to substitute the correct directories:

for files in *; do file=$(echo $files | grep "_500"); echo $file | seds/"_500"/"_1000"/g; done;
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory
bash: seds/_500/_1000/g: No such file or directory

---

### Post by Vaphell on 2012-05-15
```
for f in *_1000.jpg; do echo "$f"; cp -v -- "${f/_1000./_500.}" ~/folder2; done
```

for each file matching _1000.jpg copy "file but with _1000. replaced by _500." to destination folder

---

### Post by MG&amp;TL on 2012-05-15
Okay, not the best at this, so I might advise using cp rather than mv at first, but here it is:

```
for files in *; do file=$(echo $files | grep "_500"); filetwo=$(echo $file | sed s/"_500"/"_1000"/g);  if [[ -a $filetwo &&  $filetwo != "" ]]; then echo $filetwo; mv $file xyz/; fi; done;
```

I'm sure someone will correct me for mistakes.

How it works:

for files in * - iterate over all files in $(pwd).
file = $(echo $files | grep "_500")  - $file is a file if it contains _500 or a blank if it doesn't.

filetwo=$(echo $files | sed s/"_500"/"_1000"/g); - filetwo is a potential _1000.png file.

if[[-a $filetwo && $filetwo != ""]] - if it exists and doesn't equal a blank...

mv $file xyz/; -move the original filename.

Probably not perfect-please do a testcase before losing data. :(

Hope this helps a bit.

EDIT: Gah, Vaphell, you are amazing. @OP: Ignore mine and go with Vaphell's, but do laugh at it first.

---

### Post by angryhomer17 on 2012-05-15
@imachavel  I had problems with 
bash: seds/_500/_1000/g: No such file or directory

I tried putting in my own dir names but I guess I don't understand the syntax after the last pipe.

@Vaphell No problems with running your script. I changed cp to mv because  I want to get rid of the 500px images that have 1000px complements. A cp would work if I were copying the 500px images without a 1000px complement.

The only issue with the script is that the destination folder must exist. If it doesn't there is no error. And if I mv the files to a non-existent folder those files just disappear.

@MG&TL No problems with your script either. Yours doesn't allow moving files to a non-existent dir. Thanks for the comments too.

---


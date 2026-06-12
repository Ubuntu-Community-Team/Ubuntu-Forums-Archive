---
title: "Move all sub-files to one place"
date: 2009-12-04
forum: General Help
---

### Post by Teacher Lion on 2009-12-04
Hi,

I know the answer is out there somewhere but I just can't find it!! Over the years I've accrued loads of photos and they've all been split up in their own folders and... well... now it's a mess!

So what I want to do is run a terminal command in my photo directory to scan through all the levels of subdirectories and move/copy *.jpg to a folder on my Desktop.

Any ideas? Thanks in advance!

---

### Post by dvlchd3 on 2009-12-04
To copy:
```

cp -r photos/*.jpg ~/Desktop/folder_on_desktop

```

To move:
```

mv -r photos/*.jpg ~/Desktop/folder_on_desktop

```

And of course, change the directories to match your environment.

---

### Post by KeLa on 2009-12-04
You can't use the cp -r command if you don't wan't to copy those directories also
Here is simple way to do it without any directories in destination
First go to terminal and directory where you have those images spread around subdirectories and run following (assuming you have directory Test created in your desktop.
```
find . -name \*.jpg -printf 'cp %p ~/Desktop/Test\n' > do.sh
chmod 777 do.sh
./do.sh
```
First command will create list file and adding copy command to every file it finds.
Then only change file permissions and run that shell script.

Tested my self and working fine.

---

### Post by Teacher Lion on 2009-12-04
Kella and dvlchd3, you are *both* absolutely brilliant.

I sincerely hope that you wake up tonight to find that beautiful naked women have broken into your house in order to molest you repeatedly.

Thank you.

---

### Post by Teacher Lion on 2009-12-04
Hi!

I was trying to mark this thread as solved but I have no idea how. I've given up now. Too difficult to find!

Upon initial investigation everything was perfect. I looked in my desktop 'Test' folder and there were loads of pictures in it. However, this morning I was looking through and I found that only a small number of the pictures have actually been copied in. About 500 or so out of closer to 4000 (I haven't actually taken 4000 pictures in my life, there's company stuff too)!!

I ran the command again and paid attention to what was happening. There's a lot of this:

cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/52.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/53.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/54.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/55.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/56.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/57.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/58.jpg': No such file or directory
cp: cannot stat `./Zoli/Shady': No such file or directory
cp: cannot stat `Lane/59.jpg': No such file or directory

Any clues?

(Note: You still deserve naked ladies. I won't take that from you!)

---

### Post by Sam on 2009-12-04
Looks like you should escape your parameters....

What exactly did you run ?

---

### Post by Teacher Lion on 2009-12-04
First I created a folder on my Desktop called Test. Then (from my home folder):

sudo chmod 777 -R /photos/
cd photos
find . -name \*.jpg -printf 'cp %p ~/Desktop/Test\n' > do.sh
chmod 777 do.sh
./do.sh

I think that's everything. Please note that I understand roughly two thirds of what I'm doing.

---

### Post by Sam on 2009-12-04
You had to add quotes between the parameter.```
<snip>
find . -name \*.jpg -printf 'cp [COLOR="Red"]"[/COLOR]%p[COLOR="Red"]"[/COLOR] ~/Desktop/Test\n' > do.sh
<snip>
```

But this is a better solution in just one command:
```
find /photos/ -type f -iname *.jpg -exec cp {} ~/Desktop/Test \;
```
(or mv instead of cp if you want to move the files)

---

### Post by Teacher Lion on 2009-12-04
Trying it... wait for it... wait for it...

(This is all very exciting)

---

### Post by Teacher Lion on 2009-12-04
I've been looking into this and trying to sort it out myself, but here's what I got...

I typed:

find /photos/ -type -f -iname *.jpg -exec cp {} ~/Desktop/Test \;

...and I got:

find: Arguments to -type should contain only one letter

I shall try the other one as well in the meanwhile though I rather like yours because it's easier for me to understand!

---

### Post by Teacher Lion on 2009-12-04
The other command plus your ammends is working wonders, Sam. Thank you.

May you too be condemned to an eternity of thoroughly indecent sexual assaults perpetrated by the gender and build of your choosing.

---

### Post by kaibob on 2009-12-05
> **Teacher Lion said:**
> I've been looking into this and trying to sort it out myself, but here's what I got...

I typed:

find /photos/ -type -f -iname *.jpg -exec cp {} ~/Desktop/Test \;

...and I got:

find: Arguments to -type should contain only one letter

I shall try the other one as well in the meanwhile though I rather like yours because it's easier for me to understand!

There shouldn't be a - before f. Thus, it should be -type f

---

### Post by jegerjensen on 2009-12-05
Before you delete the original files, maybe you should make sure there are no name conflicts.  If you had pictures with identical filename but in different folders, you now have only one of those files.

To avoid the conflicts, you can create a new empty folder and copy everything again, but this time with a --backup option to cp:
```
find /photos/ -type f -iname *.jpg -exec cp --backup=numbered {} ~/Desktop/NewTestDir \;
```

---

### Post by Sam on 2009-12-05
> **Teacher Lion said:**
> ...and I got:

find: Arguments to -type should contain only one letter

Ooos my mistake, as kaibob pointed out, there is no dash before the 'f'.

---

### Post by Teacher Lion on 2009-12-05
Thank you!

Two working methods. It's really very solved!

Please mark as [Solved]. It's the way forward.

---

### Post by kilee on 2009-12-08
Hi friends.

Is there a way to move different types of files with this commands? Lets say all the jpgs, mpgs or any combination of files??

What needs to be added to perform this search. I want to move all the xls xlsx mp3 ogg etc into a single folder.

Thanks!!

And what happens if duplicated files are found?

---

### Post by KeLa on 2009-12-09
Without any other modification than extension change in command you can move one type of files at the time.
What comes to duplicates it depends on file attributes are previous files overwritten or not.

---

### Post by kaibob on 2009-12-09
> **kilee said:**
> Is there a way to move different types of files with this commands? Lets say all the jpgs, mpgs or any combination of files??

You can use multiple -name options. For example,

```
find /target/directory -name '*.pdf' -o -name '*.jpg' -o -name '*.png' -type f
```

Instead of -name, you may want to use -iname, which is not case sensitive.

---

### Post by kilee on 2009-12-15
thanks a lot! 

It worked perfect.

---


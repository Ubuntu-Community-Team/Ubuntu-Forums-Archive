---
title: "copying a lot of files"
date: 2012-06-28
forum: General Help
---

### Post by tazthecat on 2012-06-28
Hello,

I was storing all my video files in a single folder, but now it has reached over 600 files it is slow in loading the folder especialy over a local network.

what is the best way of moving every file in it's own folder?

ex. 
/home/tazthecat/Video's/*.avi (and *.srt)
to
/home/tazthecat/Movies/<movie name folder>/*.avi

Can someone please help me? I don't want to manually create all folders.

---

### Post by deathadder on 2012-06-28
You could use something like this:
```
#!/bin/bash
for f in $(find ./ -type f -iname '*.avi')
do
    base_name=$(basename $f .iso)
    base_dir="${base_name}"

    if ! [ -d $base_dir ]; then
        mkdir $base_dir
    fi
    mv $f $base_dir
    if [ -e "${base_name}.srt" ]; then
        mv "${base_name}.srt" $base_dir
    fi
done

```
I haven't tested it by the way, so be careful. To test it you can replace the mv commands with cp :)

---

### Post by MG&amp;TL on 2012-06-28
```
for files in *.avi; do name="${files%.avi}" ; mkdir "$name"; cp "$files" $HOME/Movies/"$name"; done

```for files in *.avi   -iterate over all avi files
name = "${files%.avi}"    -name is the file, minus the .avi.
mkdir $HOME/Movies/$name   -make a folder called that.
cp $files...       -copy the files there

Hope that helps, and obviously you can modify that for the .srt files. Have tested, but not extensively, so be careful. Make a copy of the folder or something.

---

### Post by Vaphell on 2012-06-28
obviously $name and $file should be in "", you never know if there is some space char waiting to ruin your day.
${files%.avi} deletes only at the end, thus it's better than ${files/.avi/} which does that everywhere

---

### Post by MG&amp;TL on 2012-06-28
> **Vaphell said:**
> obviously $name and $file should be in "", you never know if there is some space char waiting to ruin your day.
${files%.avi} deletes only at the end, thus it's better than ${files/.avi/} which does that everywhere

Thanks Vaphell, edited.

Still learning, try and do my own solutions for each of these threads.

---

### Post by tazthecat on 2012-06-28
I am going to try this out an report the results here.

Thanks deathadder, MG&TL and Vaphell!!

---

### Post by tazthecat on 2012-06-28
Worked like a charm and instant (would have take me days to do it manually).

used 

> for files in *.avi; do name="${files%.avi}" ; mkdir "$name"; mv "$files" $HOME/Movies/"$name"; done

Used the mv instead of the cp becouse of insufficient hd space.

> for files in *.srt; do name="${files%.srt}" ; mv "$files" $HOME/Movies/"$name"; done

now I have some mkv and subs ending with .nl or .en left in the folder.

how do you set multiple file formats in one code? or do I want too much now?

I will edit the script to copy the mkv and the subs, but I am just curious how to do this.

Thanks again.

---

### Post by Vaphell on 2012-06-28
do they share common name and would be put in the proper dir?

you can go with *.{nl,en} if you want to make sure only these extensions will be caught.
or *.* to match everything in name.extension format
You'd have to modify ${file%....} stuff to ${file%.*} to be more flexible. %pattern trims shortest possible match at the end, .* would consume shortest dot+any sequence

---

### Post by tazthecat on 2012-06-28
The *.{nl,en} option will do nicely. Just want to make sure no folders are created for just a subtitle, so the more specified the better.

```
for files in *.{avi,mkv,mp4}; do name="${files%.*}" ; mkdir "$name"; mv "$files" $HOME/Movies/"$name"; done 
```

and for the subs

```
for files in *.{srt,nl,en}; do name="${files%.*}" ; mv "$files" $HOME/Movies/"$name"; done 
```

---


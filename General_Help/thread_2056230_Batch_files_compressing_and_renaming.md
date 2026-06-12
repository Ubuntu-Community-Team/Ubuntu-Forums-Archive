---
title: "Batch files compressing and renaming"
date: 2012-09-11
forum: General Help
---

### Post by fernansha on 2012-09-11
Hi everyone, 

I am learning and using Linux for more than 10 months, learning new things every day. i have a task here today, just want all of ur help to direct me in the right way .

I have a folder with the set of files eg: 1000 jpgs each jpg with the size of 2MB. The task is i want to write a command and compress a all these jpgs to with the size of l gigs, ie i want all these 1000 jpgs in the folder as set of compressed files(.tar or .zip)with the size of 1 gb. 

I hope my question make sense. it would take ages if i am selecting manually and doing it. I am sure linux has a simple and fastest way to do it.

initial level of approaches i have tried. 

create a for loop and assigned a variable frame :

" for frame in ` seq 1 1 100 `; do tar -cf xxx ${frame}.jpg dest/ ; done "

I know i mmaking something wrong, not sure what it is. 

and i also want to name the zip or tar files incrementally like xx1 xx2 xxx3 etc. 

thanks in advance, sorry for the long post.

---

### Post by Vaphell on 2012-09-11
[http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/](http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/)

```
tar -M -L 1000000 -cf pics.tar *.jpg
```
though it's annoying because it doesn't automate the names of parts.

another option is to tar everything and use
```
split --verbose --bytes=1G -d pics.tar pics
```

besides at least in case of jpeg files compression doesn't make much sense. They are compressed already and the gain is miniscule.

---

### Post by fernansha on 2012-09-11
> **Vaphell said:**
> [http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/](http://trulymanaged.com/blog/how-to-split-a-large-files-to-multiple-parts-using-tar/)

```
tar -M -L 1000000 -cf pics.tar *.jpg
```
though it's annoying because it doesn't automate the names of parts.

another option is to tar everything and use
```
split --verbose --bytes=1G -d pics.tar pics
```

besides at least in case of jpeg files compression doesn't make much sense. They are compressed already and the gain is miniscule.
Thanks for the reply vaphell.
i will give it a try now. and I mentioned jpg's as an example. 
The actual task is to compress 5000+ tifs each is a size of 10Mb.

---

### Post by Vaphell on 2012-09-11
in case you want compress N files at once and have multiple archives you can try something like this:

```
n=50 # number of files in a single archive
w=3  # width of the archive number, 3 => 001

c=0; vol=1; files=();
for f in *.tiff
do
  ((c++))   # file counter
  files+=( "$f" )   # add file to the current batch  
  if ((c%n==0))     # test if c is a multiple of n
  then
    # run tar on the current batch of files
    tar -cf archive$( printf "%0${w}d" $vol ).tar "${files[@]}"
    ((vol++))
    files=()    # clear the array
  fi
done

if (( ${#files[@]} > 0 )) # compress leftovers if batch is not empty
then
  tar -cf archive$( printf "%0${w}d" $vol ).tar "${files[@]}"
fi


```

---

### Post by fernansha on 2012-09-11
sorry, i am not that good in codes,
i dont understand this line "( printf "%0${w}d" $vol ).tar " ? 
and were do we specify that, i want the xxx.tar to be only a size of 1gb ?? 

because i want all these 5000+ tifs to split them into different tar  with the size of 1 gb. 
i apologize if i am questioning wrong. vaphell

---

### Post by Vaphell on 2012-09-11
*printf "%03d" number* is used to pad the number with 0s to desired width.
```
$ w=3; vol=1; printf "%0${w}d" $vol
001
```

if you want exact size of 1G you have to either tar with multiple volumes and fixed size of 1000000 or tar everything and split to pieces with split which can be reversed (my first post)
My second post described how one would go about creating separate tars for files 1-100, 101-200, 201-300, but there is no way to tell the size of archive in advance so most likely that goes out the window.

---

### Post by fernansha on 2012-09-11
thanks alot vaphell, It works :)

---


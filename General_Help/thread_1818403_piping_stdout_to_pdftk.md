---
title: "piping stdout to pdftk"
date: 2011-08-04
forum: General Help
---

### Post by nloewen on 2011-08-04
I have a large amount of pdfs in a folder. pdfs that need to be merged have a v2 suffex making it 'name v2.pdf'. I am trying to make a script that will search for these and merge them. so far I have this

```
ls -a | grep v2 >> mergelist.txt
ls -a | grep V2 >> mergelist.txt
sed -e s/' V2.pdf'//g -e s/' v2.pdf'//g < mergelist.txt > mergelist2.txt
ls -a | grep --file=mergelist2.txt | pdftk - cat output -
```

pdftk doesn't seem to pick up stdout, and it doesn't seem to be able to grap multiple pdfs from stdout. is there a better way to be doing this?

---

### Post by -jrosco- on 2011-08-04
This could work. I'm not to sure how the pdftk works, but try the code below.

```


ls -a | grep -i v2 >> mergelist.txt #Use -i option to ignore case
sed -e s/' V2.pdf'//g -e s/' v2.pdf'//g < mergelist.txt > mergelist2.txt

for x in $(ls -a | grep --file=mergelist2.txt); do
      pdftk $x cat output output.pdf
done

```Cheers

---

### Post by nloewen on 2011-08-05
Thank you. Your code doesn't do what I want, but using the variable works far better than I could have hoped with pdftk. I hadn't thought of trying that.

---

### Post by blind2314 on 2011-08-05
> **nloewen said:**
> Thank you. Your code doesn't do what I want, but using the variable works far better than I could have hoped with pdftk. I hadn't thought of trying that.

Parsing 'ls' is never a good idea. Do any of your filenames have spaces in them by chance?

---

### Post by nloewen on 2011-08-05
they did. My working script converts all spaces to underscores because when I give pdftk the variable, it interprets all spaces as separators, even if I include quotations or \. removing spaces solved a lot of errors.

---

### Post by blind2314 on 2011-08-05
> **nloewen said:**
> they did. My working script converts all spaces to underscores because when I give pdftk the variable, it interprets all spaces as separators, even if I include quotations or \. removing spaces solved a lot of errors.

I'm assuming this modified script hasn't been shown here? I ask that because the SED lines above don't convert anything..they simply remove " v2.pdf" wherever it's found (unless that leaves a trailing underscore due to the file naming convention, in which case ignore what I'm saying, just trying to be thorough :)

---

### Post by nloewen on 2011-08-05
here is the new and improved version.

```
mergepdf.sh
for folder in $(ls -ARd */)
do
   cd $folder
   rename s/\ /_/g *
   find -iname '*v2*' -exec ../act.sh '{}' \;
   cd ..
done

act.sh
base=$(echo $1 | sed -e s/^..// -e s/'_V2.pdf'//g -e s/'_v2.pdf'//g)
echo $base
pdflist=$(ls -AR | grep $base)
pdftk $pdflist cat output $base
rm $pdflist
mv $base $base.pdf
```

---

### Post by blind2314 on 2011-08-05
> **nloewen said:**
> here is the new and improved version.

```
mergepdf.sh
for folder in $(ls -ARd */)
do
   cd $folder
   rename s/\ /_/g *
   find -iname '*v2*' -exec ../act.sh '{}' \;
   cd ..
done

act.sh
base=$(echo $1 | sed -e s/^..// -e s/'_V2.pdf'//g -e s/'_v2.pdf'//g)
echo $base
pdflist=$(ls -AR | grep $base)
pdftk $pdflist cat output $base
rm $pdflist
mv $base $base.pdf
```

So just so I (and anyone else reading) is clear, what exactly is the problem at this point? What output are you getting vs. what you're expecting?

---

### Post by nloewen on 2011-08-05
there is no problem at this point. It does what it is supposed to. The code from -jrosco- didn't do what I wanted, but I used his idea of giving pdftk a variable as input, and spent 12 hours with google hacking together what you see now, which works quite well.

---

### Post by blind2314 on 2011-08-05
Ah, in that case, please mark the thread as solved :) What you shared from your code might help someone else that has/will have the same problem.

---


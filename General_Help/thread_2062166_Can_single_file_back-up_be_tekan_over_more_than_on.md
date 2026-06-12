---
title: "Can single file back-up be tekan over more than one DVDs?"
date: 2012-09-24
forum: General Help
---

### Post by arroy_0209 on 2012-09-24
In case the back-up file size is so much that it can not be saved in one DVD, can one use more than one DVD? I mean back-up of operating system along with installed programs. I know many people prefer  not to back up installed programs, but suppose, someone try this. Will this method work at the time of restoration?

I wonder how the method of installing Red Hat Linux worked in past when people used as many as three/four CDs to install. Perhaps this shows that what I am asking is possible but I am not sure. Can anybody please help?

---

### Post by jerrrys on 2012-09-24
I don't do that, but check this out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+to+multiple+dvd&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=backup+to+multiple+dvd&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by arroy_0209 on 2012-09-25
I tried, but this only opens a new search page. I guess that is not what you intended. Please check.

---

### Post by Bobhuber on 2012-09-25
> **arroy_0209 said:**
> In case the back-up file size is so much that it can not be saved in one DVD, can one use more than one DVD? I mean back-up of operating system along with installed programs. I know many people prefer  not to back up installed programs, but suppose, someone try this. Will this method work at the time of restoration?

I wonder how the method of installing Red Hat Linux worked in past when people used as many as three/four CDs to install. Perhaps this shows that what I am asking is possible but I am not sure. Can anybody please help?
Take a look at this. About the middle of the page. I use it daily for backups.
[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by Primefalcon on 2012-09-25
there is a built in command to the linux terminal called split... read ho to use it by typing in man split

by thelooks of it.. its as simple and typing in

```
split --bytes=<size you want each piece to be> <filename>
```

for example

m stands for megabytes, g for gigabytes and k for kilobytes

so the following command
```
split --bytes=5m bigfile.mp4
```
would split the file called bigfile.mp4 into 5 meg chunks

btw you can rejoin the files by by running

```
cat x[a-z][a-z] > bigfile.mp4
```

you can even rejoin in windows by running 
```
copy /b xa* bigfile.mp4
```

[s]note: I am not sure if the windows accept the [a-z] regex expression but it does accept the * wildcard[/s] **Tested in dosbox and no it doesn't accept [a-z] so just use the * wildcard**

hope this helps

edit: in windows/dos you can use this program to split files: [http://www.fourmilab.ch/splits/](http://www.fourmilab.ch/splits/)

---

### Post by Mark Phelps on 2012-09-26
I've used an app know as hj-split.  It comes in various forms, including a java executable that you can run in Linux.

It will allow you to split a single file into parts.

Problem you will have, though, is that you will most likely have to recombine all the parts before you can use that file for restoration.

Better solution may be using a backup app that allows you to save the backup in files small enough to fit on DVDs.  The restore option of such apps then allows you to restore from the DVDs.

---


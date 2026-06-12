---
title: "Best Desktop Search Tool?"
date: 2012-05-14
forum: General Help
---

### Post by bacalha on 2012-05-14
Hello,

Since Google Desktop Search and Beagle, two great projects are dead, I would like to know if anyone knows a very good alternative to these projects

I have 1TB of data with more than 600.000 files and i'm going crazy, i'm using Lubuntu 12.04

Thanks in advance

---

### Post by scouser73 on 2012-05-14
I recommend using Synapse which can be found in the Ubuntu Software Centre.

---

### Post by LewisTM on 2012-05-14
**Recoll**. It's accurate, fast and customizable.
There is now a Recoll Unity [lens]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html") too!
See my [previous]("http://ubuntuforums.org/showpost.php?p=11518074&postcount=9") post about it.

Cheers!

---

### Post by Enigmapond on 2012-05-14
> **scouser73 said:**
> I recommend using Synapse which can be found in the Ubuntu Software Centre.

+1! This app is truly the best and not just for searches. Terminal commands & app launching also work from here. I couldn't do without it.

---

### Post by LewisTM on 2012-05-14
> **Enigmapond said:**
> +1! This app is truly the best and not just for searches. Terminal commands & app launching also work from here. I couldn't do without it.
I love Synapse and use it every day, but it doesn't answer the OP's question.
Beagle and GDS are (were) full text search tools. Synapse doesn't do that, it just searches for files, programs and actions.
I wish there was a Recoll plugin for Synapse, that would be wondrous.

---

### Post by Enigmapond on 2012-05-14
You can do this easily in the terminal as well if you use grep  with the -l option to have it return file names that match. So to do this you would open terminal change directory till your in the one you wanna search then use a command like this one.

```
grep -l searchterm *.txt
```

where *.txt is wildcard which tells it to check all files of type .txt. Where searchterm is the term or word(s) your looking for.(in quote marks if theres a space ie. "search term")

Hope this helps.

---

### Post by bacalha on 2012-05-14
First I would like to thank everyone who replied my topic.

I'm trying to use Recoll, but AFAIK it only searches docs, images and pdfs. It's really good to look for sentences inside documents.

But I have tons of videos, songs and images. I just want to separate all the images, videos and other files in order to classify in folders(like TV series folder, Hip-Hop Songs,etc)

If Recoll could do this search(by other file types than documents), it would be perfect

---

### Post by traditionalist on 2012-05-14
> **bacalha said:**
> Hello,

Since Google Desktop Search and Beagle, two great projects are dead, I would like to know if anyone knows a very good alternative to these projects

I have 1TB of data with more than 600.000 files and i'm going crazy, i'm using Lubuntu 12.04

Thanks in advance

use Recoll. Works well for me on 12.04;

[http://www.recoll.org/](http://www.recoll.org/)

It is in the Ubuntu Center as well.

---

### Post by Enigmapond on 2012-05-14
> **LewisTM said:**
> **Recoll**. It's accurate, fast and customizable.
There is now a Recoll Unity [lens]("http://www.webupd8.org/2012/03/recoll-lens-full-text-search-unity-lens.html") too!
See my [previous]("http://ubuntuforums.org/showpost.php?p=11518074&postcount=9") post about it.

Cheers!

Just install recoll...MAD indexing to start...seems pretty good though.

---

### Post by ckop64 on 2012-05-14
Try catfish. It's a lightweight frontend to find and locate. It is in the software centre.

---

### Post by bacalha on 2012-05-14
> **Enigmapond said:**
> Just install recoll...MAD indexing to start...seems pretty good though.

But does Recoll indexes other files than documents and images(like videos, songs, zip, rar, etc)?

---

### Post by Enigmapond on 2012-05-14
You can tell it what to skip..file types or paths from what I can see. Just install it and play with it. It's a tiny file but in the beginning, don't let it just run...configure the indexing first.

---

### Post by LewisTM on 2012-05-14
> **bacalha said:**
> But does Recoll indexes other files than documents and images(like videos, songs, zip, rar, etc)?
Ahh I see. So you want to find by file name and type and do stuff with the results.
The most comprehensive tool would be **kfind**
It requires KDE libraries but that's just hard drive space of which most have plenty. It runs fine in all environments. 
It can filter by file name AND file type AND location AND a bunch of other parameters. The files in the list of results can be copied or moved or opened or whatever.

---

### Post by HiImTye on 2012-05-14
the best search tools are find, grep, sed, and the like especially if you are searching a large number of files or large files

---

### Post by traditionalist on 2012-05-15
> **bacalha said:**
> But does Recoll indexes other files than documents and images(like videos, songs, zip, rar, etc)?

It can index everything. Don't put the index in your /root  !

---

### Post by bacalha on 2012-05-15
Hello everyone,

@Enigmapond:
I tried kfind, worked great, but it lacks in indexing, otherwise it would be perfect. Is there any way to enable some sort of indexing so i can find those files faster?

@traditionalist:
I indexed almost 30% of my backup hard drive and it only lists mp3 files, documents, compressed files and images. I have several mkv and avi files and it didn´t listed any. Am I missing something?

---

### Post by LewisTM on 2012-05-15
Well there is a checkbox in kfind to use files index, which calls [FONT="Courier New"]locate[/FONT]. 
Unfortunately it lags and doesn't seem to speed up much. Maybe it runs better on your side...

---

### Post by goodbye-windows(tm) on 2012-07-17
> **LewisTM said:**
> Ahh I see. So you want to find by file name and type and do stuff with the results.
The most comprehensive tool would be **kfind**
It requires KDE libraries but that's just hard drive space of which most have plenty. It runs fine in all environments. 
It can filter by file name AND file type AND location AND a bunch of other parameters. The files in the list of results can be copied or moved or opened or whatever.

I know this is an old post, so perhaps no one will read this message....

I tried to use kfind in xubuntu, it does not work. Yes, I installed it with all it's dependencies using the synaptic program. 

I find all the programs that do searches do very little with the results of the search.

For instance, I search for a keyword in my music folder. I get 300 hits, all the files I am interested in are there. But, I want to select 3 of those files to move them to the trash (or to the desktop, or to a subfolder in my music folder) etc. 

Terminal based searches find the files fast! But, if you want to move number 3, number 73 and number 300 to another folder, you have to type each filename to do the job in terminal.

I believe kfind provides the ability to manipulate files found in the list of files that satisfy the search criteria. 

_**But, does anyone know why kfind can't find files in Xubuntu?? **_All the searches end up with 'no files found'.

Art

---

### Post by goodbye-windows(tm) on 2012-07-18
Use gnome utilities, has great search program.

---

### Post by ThorX89 on 2012-12-16
> **HiImTye said:**
> the best search tools are find, grep, sed, and the like especially if you are searching a large number of files or large files

He was obviously asking for an indexing solution. Grep and find are great, but they always have to scan the content they're searching. This makes them not so good for a large number of large files, as each search will take necessarily too long. Having an index circumvents the need to scan the files again and that makes it a lot faster.

---


---
title: "I can not unzip this file"
date: 2012-07-10
forum: General Help
---

### Post by Tetrohedron on 2012-07-10
I downloaded a per-configured virtual machine that came in a zipped file.  I double clicked it and tried to unzip it via the default program and I got this error.

zipinfo:  cannot find zipfile directory in one of /home/rootless/.cache/.fr-xKB5uz/dojo_v1.2-virtualbox.zip or
          /home/rootless/.cache/.fr-xKB5uz/dojo_v1.2-virtualbox.zip.zip, and cannot find /home/rootless/.cache/.fr-xKB5uz/virtualbox.zip.ZIP, period.


Then I tried (and I don't think I used this command correctly) gzip ~/Downloads/virtualbox.

The virtual box icon changed from saying zip to gzip but nothing appeared to happen.  When I double clicked it again I was able to extract the files without an error but rather than extracting the files it extracted an identical zipped file.  The box got good reviews on the sites I checked so I would be shocked if its host site had up a broken zip file.

---

### Post by SlugSlug on 2012-07-10
can you post output of 

```
ls -lh  ~/Downloads
```

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> can you post output of 

```
ls -lh  ~/Downloads
```



The output is:

```

-rw-rw-r-- 1 rootless rootless 877M Jul  9 21:57 virtualbox.zip.gz
```

---

### Post by SlugSlug on 2012-07-10
> **Tetrohedron said:**
> The output is:

```

-rw-rw-r-- 1 rootless rootless 877M Jul  9 21:57 virtualbox.zip.gz
```


What does this output?
```
tar zxvf ~/Downloads/virtualbox.zip.gz
```

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> What does this output?
```
tar zxvf ~/Downloads/virtualbox.zip.gz
```


SlugSlug, the output from that command was 

```
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

```

---

### Post by codemaniac on 2012-07-10
> **Tetrohedron said:**
> The output is:

```

-rw-rw-r-- 1 rootless rootless 877M Jul  9 21:57 virtualbox.zip.gz
```

Seems like you have first used zip to compress the file then again used gzip for compression .

check the file type , then use uncompression utility accordingly .

```
 which virtualbox.zip.gz
```if the below command returns something like below use gunzip to uncompress then use unzip .

> gzip compressed data - deflate method , original file name


EDIT : Please note that i have mistyped the command , it would be file command instead of which .Regret for the typo .

---

### Post by SlugSlug on 2012-07-10
```
sudo apt-get install gunzip
``` ```
gunzip ~/Downloads/virtualbox.zip.gz
``` ```
unzip ~/Downloads/virtualbox.zip
```

---

### Post by Tetrohedron on 2012-07-10
> **codemaniac said:**
> Seems like you have first used zip to compress the file then again used gzip for compression .

check the file type , then use uncompression utility accordingly .

```
 which virtualbox.zip.gz
```if the below command returns something like below use gunzip to uncompress then use unzip .


Am I misunderstanding your command?  I am typing in " 			 				gzip compressed data - deflate method ./virtualbox.zip.gz" while in the downloads directory and it is saying no such file or directory.  I typed in ls to check my spelling.  It also wouldn't let me tab to the file.

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> ```
sudo apt-get install gunzip
``` ```
gunzip ~/Downloads/virtualbox.zip.gz
``` ```
unzip ~/Downloads/virtualbox.zip
```

I copied and pasted in your command but apt-get couldn't find the app.

```
rootless@rootless-h8-1039:~/Downloads$ sudo apt-get install gunzip
[sudo] password for rootless: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gunzip

```

---

### Post by SlugSlug on 2012-07-10
miss out that step - I think it's installed by default

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> miss out that step - I think it's installed by default

That made progress.  Now I am back to the error I started with though.

```

rootless@rootless-h8-1039:~/Downloads$ unzip ~/Downloads/virtualbox.zip
Archive:  /home/rootless/Downloads/virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/rootless/Downloads/virtualbox.zip or
        /home/rootless/Downloads/virtualbox.zip.zip, and cannot find /home/rootless/Downloads/virtualbox.zip.ZIP, period.

```

---

### Post by SlugSlug on 2012-07-10
> **Tetrohedron said:**
> That made progress.  Now I am back to the error I started with though.

```

rootless@rootless-h8-1039:~/Downloads$ unzip ~/Downloads/virtualbox.zip
Archive:  /home/rootless/Downloads/virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/rootless/Downloads/virtualbox.zip or
        /home/rootless/Downloads/virtualbox.zip.zip, and cannot find /home/rootless/Downloads/virtualbox.zip.ZIP, period.

```


could you post the output of this again 


```
ls -lh  ~/Downloads
```

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> could you post the output of this again 


```
ls -lh  ~/Downloads
```


Yes.  Here is the output.

```
Archive:  /home/rootless/Downloads/virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/rootless/Downloads/virtualbox.zip or
        /home/rootless/Downloads/virtualbox.zip.zip, and cannot find /home/rootless/Downloads/virtualbox.zip.ZIP, period.

```

---

### Post by SlugSlug on 2012-07-10
> **Tetrohedron said:**
> Yes.  Here is the output.

```
Archive:  /home/rootless/Downloads/virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of /home/rootless/Downloads/virtualbox.zip or
        /home/rootless/Downloads/virtualbox.zip.zip, and cannot find /home/rootless/Downloads/virtualbox.zip.ZIP, period.

```

Thats not the output :)

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> Thats not the output :)

What output would you like?  That's what the terminal returned when I typed "unzip /home/rootless/Downloads/virtualbox.zip "

---

### Post by SlugSlug on 2012-07-10
> **Tetrohedron said:**
> What output would you like?  That's what the terminal returned when I typed "unzip /home/rootless/Downloads/virtualbox.zip "


```
ls -lh  ~/Downloads
```

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> ```
ls -lh  ~/Downloads
```

Got it, sorry.  Here is the output:

```
total 877M
-rw-rw-r-- 1 rootless rootless 877M Jul  9 21:57 virtualbox.zip

```

---

### Post by SlugSlug on 2012-07-10
Was there more than 1 file to download? It does seem like it's part of a split zip.gz :(

not sure if 

```
file 
/home/rootless/Downloads/virtualbox.zip
```

will give us more info..?

---

### Post by Tetrohedron on 2012-07-10
> **SlugSlug said:**
> Was there more than 1 file to download? It does seem like it's part of a split zip.gz :(

not sure if 

```
file 
/home/rootless/Downloads/virtualbox.zip
```will give us more info..?

That was the only file.  I can re-download the file in case something got screwed up or deleted.  Besides that, what information would help?

---

### Post by codemaniac on 2012-07-10
> **Tetrohedron said:**
> Am I misunderstanding your command?  I am typing in "                              gzip compressed data - deflate method ./virtualbox.zip.gz" while in the downloads directory and it is saying no such file or directory.  I typed in ls to check my spelling.  It also wouldn't let me tab to the file.


Extremely sorry , i meant file command.

```
file ./virtualbox.zip.gz
```

---

### Post by Tetrohedron on 2012-07-10
> **codemaniac said:**
> Extremely sorry , i meant file command.

```
file ./virtualbox.zip.gz
```


I typed in file ./virtualbox.zip.  We managed to get rid of the .gz.  Here is what I typed and the output.

```
rootless@rootless-h8-1039:~/Downloads$ file ./virtualbox.zip
./virtualbox.zip: Zip archive data, at least v2.0 to extract

```

---

### Post by codemaniac on 2012-07-10
> **Tetrohedron said:**
> I typed in file ./virtualbox.zip.  We managed to get rid of the .gz.  Here is what I typed and the output.

```
rootless@rootless-h8-1039:~/Downloads$ file ./virtualbox.zip
./virtualbox.zip: Zip archive data, at least v2.0 to extract

```

Then you will only need to unzip the .zip file .

```
unzip ./virtualbox.zip
```

---

### Post by Tetrohedron on 2012-07-10
> **codemaniac said:**
> Then you will only need to unzip the .zip file .

```
unzip ./virtualbox.zip
```


We tried that.  Here is what the terminal returns.

```
Archive:  ./virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of ./virtualbox.zip or
        ./virtualbox.zip.zip, and cannot find ./virtualbox.zip.ZIP, period.

```

---

### Post by codemaniac on 2012-07-10
> **Tetrohedron said:**
> We tried that.  Here is what the terminal returns.

```
Archive:  ./virtualbox.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of ./virtualbox.zip or
        ./virtualbox.zip.zip, and cannot find ./virtualbox.zip.ZIP, period.

```

The problem is exactly what it says. Unzip can't find the line of code that signals the end of the archive, so either: 1. The archive is currupt 2. There are more than 1 parts to the archive

---

### Post by Tetrohedron on 2012-07-10
> **codemaniac said:**
> The problem is exactly what it says. Unzip can't find the line of code that signals the end of the archive, so either: 1. The archive is currupt 2. There are more than 1 parts to the archive

I re-downloaded the file and was able to extract it.  Thank you both for your help.  I also read the man pages for all of the zip and unzip commands discussed so thanks for the inadvertent lesson

---

### Post by SlugSlug on 2012-07-10
> **Tetrohedron said:**
> I re-downloaded the file and was able to extract it.  Thank you both for your help.  I also read the man pages for all of the zip and unzip commands discussed so thanks for the inadvertent lesson


No prob :)

---


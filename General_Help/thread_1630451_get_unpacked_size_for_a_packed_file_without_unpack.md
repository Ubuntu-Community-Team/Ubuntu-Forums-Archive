---
title: "get unpacked size for a packed file without unpacking"
date: 2010-11-25
forum: General Help
---

### Post by DJTurboToJo on 2010-11-25
Hello there,

in Windows I have the abbility to right click on a zipped file and see what the unpacked size would be, even without unzipping the file first. Maybe it's plugin from one of the Unzip, Untar programs I got or maybe a windows tool, I don't know. 

Is there something similar in Ubuntu?

So here's what I want to do:
I have 1000 tar files and I want to know
1) the file size of the packed files (which is easy as it's just the file size now)
2) the file size of the unzipped files (and I really don't want to untar all files)

Is there a nice command that can give the information I need to complete task 2)?

Thanks in advance
DJTurboToJo

---

### Post by Dave_L on 2010-11-25
By "tar file" do you mean .tar.gz?  The following shell command will display that information:

```
$ gzip -lv test.tar.gz
method  crc     date  time           compressed        uncompressed  ratio uncompressed_name
defla a5aabfbc Nov 25 12:21               47432               61440  22.8% test.tar
```

---

### Post by DJTurboToJo on 2010-11-25
Yep, this is the information I can get in windows and thanks to you now in Ubuntu, too!

Is there a way to somehow add this number for several files in a for loop?

---

### Post by Dave_L on 2010-11-25
The command will accept wild card characters.

```
$ gzip -lv *.tar.gz
method  crc     date  time           compressed        uncompressed  ratio uncompressed_name
defla a5aabfbc Nov 25 13:55               47432               61440  22.8% test1.tar
defla a5aabfbc Nov 25 13:55               47432               61440  22.8% test2.tar
defla a5aabfbc Nov 25 13:54               47432               61440  22.8% test.tar
                                         142296              184320  22.8% (totals)
```

---

### Post by DJTurboToJo on 2010-11-25
Awesome. Then I simply copy and paste it in some other program that calculates the size in the form of tar.gz and then as if they were untar'ed.

Thanks!

---


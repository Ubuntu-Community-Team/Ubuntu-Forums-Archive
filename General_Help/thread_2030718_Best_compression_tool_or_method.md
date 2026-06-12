---
title: "Best compression tool or method"
date: 2012-07-21
forum: General Help
---

### Post by Lateralus138 on 2012-07-21
Hey all, I was just curious as to what the best compression tool or method is in Ubuntu, well Linux in general, but Ubuntu is my main Linux OS. In Windows I use 7-zip and the Ultra setting seems to compress to a smaller size than I have ever seen from any other compression utility. I was wondering what is comparable to 7zip ultra method in terms of file size? I don't care about speed really.

---

### Post by codemaniac on 2012-07-21
> **Lateralus138 said:**
> Hey all, I was just curious as to what the best compression tool or method is in Ubuntu, well Linux in general, but Ubuntu is my main Linux OS. In Windows I use 7-zip and the Ultra setting seems to compress to a smaller size than I have ever seen from any other compression utility. I was wondering what is comparable to 7zip ultra method in terms of file size? I don't care about speed really.

You can use 7zip in Ubuntu as well .I guess you need to install the package p7zip from the Universe repository .

---

### Post by Lateralus138 on 2012-07-21
> **codemaniac said:**
> You can use 7zip in Ubuntu as well .I guess you need to install the package p7zip from the Universe repository .

Oh ok, I was trying to install it with apt-get and was trying 7zip by itself and I know I could have searched in the software center, but for some reason didn't think of it til just now lol probably because I never use it. I didn't know there was a 'p' in front of it. I just installed it in Wine, but I always prefer to use the Linux programs if possible. And also I didn't know if there was something else Linux had in place of it. awesome thanks.

---

### Post by codemaniac on 2012-07-21
> **Lateralus138 said:**
> Oh ok, I was trying to install it with apt-get and was trying 7zip by itself and I know I could have searched in the software center, but for some reason didn't think of it til just now lol probably because I never use it. I didn't know there was a 'p' in front of it. I just installed it in Wine, but I always prefer to use the Linux programs if possible. And also I didn't know if there was something else Linux had in place of it. awesome thanks.
```

sudo apt-get update
sudo apt-get install p7zip-full
```

However I use gzip all the time .
You can try up the below compression utilities as well .
[http://www.techradar.com/news/software/applications/best-linux-compression-tool-8-utilities-tested-933098](http://www.techradar.com/news/software/applications/best-linux-compression-tool-8-utilities-tested-933098)

---

### Post by Lateralus138 on 2012-07-21
I guess it was already on my computer but there's no gui of course that's no big deal as I do most things from the terminal anyway. I have been reading about the different compression methods and how to get the best compression for the smallest files and I read somewhere that bzip is supposed to have the best according to this guys benchmarks [here]("http://odzangba.wordpress.com/2009/03/25/gzip-vs-bzip2-vs-lzma/"). But I did my own benchmarks using the best compression methods of both bzip2 and 7zip and I got a folder that was originally 64 mbs down to 26mbs with Bzip2 and down to 16mbs! in 7zip.

Edit: I just tried gzip with the -9 switch for best compression and it only got down to 26mbs as well.

---

### Post by Frogs Hair on 2012-07-21
When right clicking the folder and selecting compress there is a menu in the dialog box. Choose the package type toy want and the list will reflect the compression tools you have installed. Some compression tools might include a GUI independent of the file roller.

---

### Post by Lateralus138 on 2012-07-21
> **Frogs Hair said:**
> When right clicking the folder and selecting compress there is a menu in the dialog box. Choose the package type toy want and the list will reflect the compression tools you have installed. Some compression tools might include a GUI independent of the file roller.
Thanks, I seen about 9 different compression types. I stated above I prefer command lines, but I was interested in gui options anyway so I did some googling and found this q7z for 7zip [here]("http://www.ghacks.net/2010/03/22/q7z-front-end-for-linux-7-zip/") (I had to install pyqt4-dev-tools to install it) and it works great just like Windows gui tool. 

After playing with the tool for a minute I found out it also has the same compression options for xz, bzip, gzip, zip and tar. 

I used each archive type with ultra compression on a text file and it seems that gzip did do the best there. I tried it on some images and it beat them too but only by a little of course images you cant barely compress at all anyway.

Text file (1.1kb) with ultra compression:
xz=828 bytes
bzip2=801 bytes
gzip=774 bytes
zip=818 bytes
tar=10.2 kbs? wow (I did these 3 times with the same results)

I then compressed a folder with multiple files (238.6kbs)  types (part if a gtk theme) and here were its' results:
xz=33.8 kbs
bzip2=43.5 kbs
gzip=51.9 kbs
zip=161.5 kbs
tar=266.2 kbs

It looks like it just depends on what you're compressing for what type you should use. 

Thanx again.

---

### Post by Frogs Hair on 2012-07-21
7zip for Windows has a GUI ,but installs as part of the file roller in Ubuntu.

---

### Post by Lateralus138 on 2012-07-21
> **Frogs Hair said:**
> 7zip for Windows has a GUI ,but installs as part of the file roller in Ubuntu.
Sorry I just edited my post above. I know, I use 7zip for Windows and I said above I have installed it in Wine, I just wish I could get better results from command lines. I don't really like to do anything the "easy way".

---


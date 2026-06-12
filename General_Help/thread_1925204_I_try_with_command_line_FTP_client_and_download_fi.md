---
title: "I try with command line FTP client and download files simultaneously into a tree"
date: 2012-02-14
forum: General Help
---

### Post by operationexodus on 2012-02-14
Simple as research, but after days of research and testing has not given me any results.
I can not find a client that is controlled from the command line, however, and is able to download to a local folder, all contents of my server recursively and multithreaded!

You have some program that is right for me? If you can give me an example code.

Thank you!

---

### Post by winh8r on 2012-02-14
try gftp which is in the repositories

or try here:

[http://www.ncftp.com/]("http://www.ncftp.com/")

hope this helps you

---

### Post by operationexodus on 2012-02-14
Could you pass me the code to use to actually make multithreaded file recovery and how to recover from the root. In both cases! Thank you so much! :)

---

### Post by winh8r on 2012-02-14
If you install either of the utilities I have suggested then you will have all the necessary code on your system for you to use as you require.

Hope this helps.

---

### Post by operationexodus on 2012-02-14
> **winh8r said:**
> If you install either of the utilities I have suggested then you will have all the necessary code on your system for you to use as you require.

Hope this helps.
This is the problem I have read many guides, but no mention of how to download files simultaneously with 5, the whole tree root!

In my server I have about 7000 files and the total weight is about 45 MB, if I had to download everything using only one file at a time takes about 2 hours and a half! But with the simultaneous download 5 files at a time, this time is reduced to about 15 minutes!

So I ask you if you can give me the correct string to start simultaneously at least 5 in the same program ftp download.

---

### Post by winh8r on 2012-02-14
I seem to have misunderstood what it was you were asking in your first post, apologies for that.


There is some helpful information here:

[http://www.mydigitallife.info/upload-mput-and-download-mget-multiple-files-automatically-in-ftp-transfer/]("http://www.mydigitallife.info/upload-mput-and-download-mget-multiple-files-automatically-in-ftp-transfer/")

which might help you out.


or   enter in terminal  man ftp

---

### Post by TheFu on 2012-02-14
> **operationexodus said:**
> Simple as research, but after days of research and testing has not given me any results.
I can not find a client that is controlled from the command line, however, and is able to download to a local folder, all contents of my server recursively and multithreaded!

You have some program that is right for me? If you can give me an example code.

Thank you!

wget will download entire directory structures. I don't know if it is multi-threaded but for 45MB, it should be quick anyway.

[https://www.linuxquestions.org/questions/linux-networking-3/wget-multi-threaded-downloading-457375/](https://www.linuxquestions.org/questions/linux-networking-3/wget-multi-threaded-downloading-457375/) has sample code.

---

### Post by winh8r on 2012-02-14
I suspect the best option is still using the mget with a wildcard * option and specifying

 ftp> prompt

Interactive mode off.


however , I may be wrong as I never transfer more than a few files at a time and rarely use ftp anymore

---

### Post by Khayyam on 2012-02-14
operationexodus ..

As TheFu pointed out, wget can do recursive ftp transfers, its not multithreaded but [this post on LinuxQuestions](http://www.linuxquestions.org/questions/linux-networking-3/wget-multi-threaded-downloading-457375/) explains how to make it behave as though it were.

Documentation can be found in the [Wget Manual](http://www.gnu.org/software/wget/manual/wget.html).

HTH ...

---


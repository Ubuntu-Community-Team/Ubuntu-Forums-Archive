---
title: "amazonmp3 still giving issues in 64 bit despite...."
date: 2010-05-10
forum: General Help
---

### Post by billfish1881 on 2010-05-10
I am running 64bit lucid on my machine. I had a lot of fun getting X-plane working, but eventually did. Now I am working on the amazon MP3 downloader. I have read many threads on the topic. I have installed and run getlibs. Unfortunately it is still coming back with this:

billfish@billDesktop:~/Desktop$ amazonmp3
amazonmp3: error while loading shared libraries: libboost_filesystem-gcc42-1_34_1.so.1.34.1: cannot open shared object file: No such file or directory
billfish@billDesktop:~/Desktop$ sudo getlibs /usr/bin/amazonmp3
No match for libboost_filesystem-gcc42-1_34_1.so.1.34.1
No match for libboost_regex-gcc42-1_34_1.so.1.34.1
No match for libboost_date_time-gcc42-1_34_1.so.1.34.1
No match for libboost_signals-gcc42-1_34_1.so.1.34.1
No match for libboost_iostreams-gcc42-1_34_1.so.1.34.1
No match for libboost_thread-gcc42-mt-1_34_1.so.1.34.1
No packages to install

I am very new to linux, but I've managed to get things working for the most part. Does anyone know why getlibs cannot find and install these dependencies? What should I do next? Thanks everyone for the help.

---

### Post by colin-m on 2010-05-12
Ubuntu Lucid Lynx 64 bit, is missing some dependencies, but luckily someone has produced a script to automate the process ([http://ubuntuforums.org/showthread.php?p=9145072](http://ubuntuforums.org/showthread.php?p=9145072) post #17).
Since you have already part installed the Amazon loader, it would be easier just to open a terminal, copy, paste and run each of the last three lines of the script . 
The second of the last three lines is quite long, so make sure you copy it all.
Hope this helps.

---

### Post by billfish1881 on 2010-05-12
Thankyou very much colin-m! Worked like a charm! Now amazonmp3 is working perfectly. The last three lines were the key.

---

### Post by l33tminion on 2010-06-09
Thanks!

---

### Post by bobmiller1969 on 2010-06-09
[FONT=Georgia][COLOR=Navy]Thanks for the help. A little trial and error and finally got this working. Copied the last 3 lines of the script. Still a no-go. Copied the 4th to last line and that did the trick.[/COLOR][/FONT]

---


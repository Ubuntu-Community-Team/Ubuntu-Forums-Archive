---
title: "k9copy not working, please help"
date: 2012-01-28
forum: General Help
---

### Post by tim_norman2003 on 2012-01-28
so ive use k9copy a number of times successfully, but recently, for no apparent reason it stopped working.

ill use it as normal, when i come to finish the process however an error message will come up, which says: 'Directory already exists.
Please choose another location or rename the DVD title.' (check out the screen shots.)

when i continue another error message will come up and i have no optino to cancel, which will quite k9copy.

ive tried a number of dvds, using a number of different options including going straight to dvd etc, nothing works, ill get the same error message.

ive tried, as the message says, saving it in a different location, and changing the name: nothing.

check out the screen shots for more info .
please could you help me,

thanks
Tim

---

### Post by tim_norman2003 on 2012-01-28
ive tried using different software peices too, but i find k9 the best for me, as its simple, not only to rip, but more importantly, its easy to burn a dvd from an ISO, which i cant do with dvd::rip etc.

---

### Post by tim_norman2003 on 2012-01-28
i tried instaling the medibuntu stuff from 'http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/'

somewhere i look said that may work, but no luck.

check out this screen shot, this is the error message i got after instaling mebibuntu.

---

### Post by bryncoles on 2012-01-28
Hi Tim.  

I think normal forum etiquette is to only bump once in 24 hours.  That said, I am experiencing similar issues as yourself with k9copy, except that after it has told me to save in a different location, it then lets me proceed!

Can you try running k9copy from the terminal, to see if it gives us any more detailed output regarding the problem?

(and to anyone else reading this -- I have no idea what I'm doing!  Feel free to jump in and help too.  Tim, forget you read those last sentences!)

---

### Post by tim_norman2003 on 2012-01-28
sorry, im still pretty new.

how do i run the program through terminal ?

---

### Post by bryncoles on 2012-01-28
Open a terminal (should be somewhere in your dashboard, but I'm afraid I'm not using the same desktop environment as you are, so I cant say exactly where).  Search for / click the 'terminal emulator' option and then just type the name of the software you want to run, in this case k9copy

---

### Post by tim_norman2003 on 2012-01-28
okay, i ran k9copy through terminal, and followed the procession of copying a dvd. im not exactly sure what you need to see, but i copied all the text that was in terminal after the error message came up, and i pressed continue (if your after something else let me know)

tim@tim-desktop:~$ k9copy
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
Disc in /dev/sr0 is a Video DVD
title : "Title 14" 
" /usr/bin/dvdauthor -x /tmp/kde-tim/k9copy//k9arA6739.xml" 
" /usr/bin/genisoimage -gui -v -graft-points -volid COWBOYS_AND_ALIENS -appid k9copy -volset-size 1 -volset-seqno 1 -no-cache-inodes -udf -iso-level 1 -dvd-video -o /home/tim/Desktop/COWBOYS_AND_ALIENS.iso /tmp/kde-tim/k9copy/COWBOYS_AND_ALIENS" 
" /usr/bin/genisoimage -gui -v -graft-points -volid COWBOYS_AND_ALIENS -appid k9copy -volset-size 1 -volset-seqno 1 -no-cache-inodes -udf -iso-level 1 -dvd-video -o /home/tim/Desktop/COWBOYS_AND_ALIENS.iso /tmp/kde-tim/k9copy/COWBOYS_AND_ALIENS"

---

### Post by woo10jw on 2012-02-28
I've been running 10.04 32 bit since it came out and have had no problems with k9copy. I just upgraded to 11.04-64 and k9copy doesn't work anymore. Tried the other versions also with no positive results. So this is how I solved the problem. I install 10.04 32bit on 10gb partition, updated but didn't let it update the new kernel, installed just what I needed to make k9copy work. Everything works fine, just use it till they fix k9copy. Some might think this is overboard, but I'm a noob and not smart enough to fix it the right way. When I said doesn't work, I mean if you uncheck the keep original menus box, I remove everything but the main movie.

---


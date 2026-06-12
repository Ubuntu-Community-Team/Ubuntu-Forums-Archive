---
title: "wget multi mirror download"
date: 2010-03-07
forum: General Help
---

### Post by zazuge on 2010-03-07
yes you can (download one file with mutiple urls)!
but it's not natively supported
the basic idea of donwload accelerators 
is to divide a file to multiple chunks and download each one in parallel
whether form the same server (witch piss off adminitrator because it eats theyr download slots) or not (a more legitemat use of multiple download capability)

now to use that trick in wget you have to do it manually and it may corrupt your downloaded file, so beware.

suppose you're downloading an iso image (ubuntu image)
you want to download it from 6 different servers 
you have to download normally from the first
wget -c "url1" -O image.iso
then use dd to fill zeros to the other chunks
dd if=/dev/zero of=image2.iso bs=1024  count=100000
dd if=/dev/zero of=image3.iso bs=1024  count=200000
dd if=/dev/zero of=image4.iso bs=1024  count=300000
....
for each one use a different server and resume download
wget -c "url2" -O image2.iso
wget -c "url3" -O image3.iso
no you have to stop the download when it passes it's 100M size
for example stop image2 download when it reachs it's 200M size
it's not a problem if you download more than that but beware if you understimate or cute download before that (you can use md5sum of ubuntu CD)
if anyone know how to stop the download at a fixed size tell me!
now use 
dd if=image2.iso of=image.iso bs=1024  count=100000 skip=100000
dd if=image3.iso of=image.iso bs=1024  count=100000 skip=200000
...
now you've got your final image mount the CD and luchn the md5sum integrity check ^^

---

### Post by tg3793 on 2010-12-07
[COLOR="Purple"]**I have a problem also related to download speed. How would I get wget to stop itself and then automatically resume if the download speed drops below 30 Kbs ?**[/COLOR]


~~~~~~~~~~~~~~~~~~~~~~~~~~
**~** Background to problem **~**
~~~~~~~~~~~~~~~~~~~~~~~~~~

For some reason any download I start runs great for about ten to twenty seconds. It quickly builds up to 50Kbs to 90Kbs but then after aforementioned number of seconds it creeps down to 20Kbs and then finally under 5Kbs.

My current solution is to baby sit each download, canceling it and then resuming it with wget -c. This works great but it is very time consuming.

---


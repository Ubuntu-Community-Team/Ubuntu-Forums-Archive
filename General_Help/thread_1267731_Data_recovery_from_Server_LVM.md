---
title: "Data recovery from Server LVM"
date: 2009-09-16
forum: General Help
---

### Post by talsemgeest on 2009-09-16
Ok, so heres the problem:

I had a server, with 3 hard drives, a 1TB, a 320GB, and a 40GB. I started off with the 1TB as a LVM, set up during Ubuntu Server installation, then added the 320GB to the LVM a while later with instructions I found. That all worked fine. This evening I went to add the 40GB to the LVM, this time using webmin to resize it. I typed in the new size, it went to resize, then I lost everything. 

I shut the server off immediately after determining that it could not mount the FS, and I have now booted into the live CD. It seems that it can find a 138GB partition on the 1TB, but since that cannot be my data I haven't tried to mount it. It cannt find any LVGs either.

So, best case scenario is that you guys can find a way to restore the partitions to their former selves. 
Second best scenario is that you can find a way to mount the mangled filesystem so I can copy the files to a remote drive.
Of course, worst case scenario is that I lose 6 months worth of data, as I wasn't able to afford backup media.

I really hope you guys can help me out, this data really is my life-blood, without it I am nothing.

---

### Post by talsemgeest on 2009-09-16
Ok, looks like I was able to restore the lvms on each disk using testdisk, but I still don't know how to put them back together to make the root partition. All help would be appreciated. :)

---

### Post by talsemgeest on 2009-09-16
Bump

---

### Post by unutbu on 2009-09-17
talsemgeest, what is the output of 
```

pvscan
```

If you see "Incorrect metadata area header checksum" there is an interesting and informative blog post about what to do here: [http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)

---

### Post by talsemgeest on 2009-09-18
> **unutbu said:**
> talsemgeest, what is the output of 
```

pvscan
```

If you see "Incorrect metadata area header checksum" there is an interesting and informative blog post about what to do here: [http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/](http://blog.adamsbros.org/2009/05/30/recover-lvm-volume-groups-and-logical-volumes-without-backups/)
Thanks for the help unutbu, I really appreciate it, but I have resigned to using brute-force data recovery methods, for example plugging in the hdds to my windows box and running recuva ( a very good data recovery program).

So once again, thanks for the help, but I've resigned myself to less elegant methods of getting my data back.

---

### Post by bumanie on 2009-09-18
Hi talsemgeest; Thought of trying photorec to recover the data - it will recover 100+ file types.

---

### Post by talsemgeest on 2009-09-18
> **bumanie said:**
> Hi talsemgeest; Thought of trying photorec to recover the data - it will recover 100+ file types.
I'm running that right now but so far it only seems to be getting scrambled mpgs and mp3s, and I didn't even have any mpgs on the system! ;)

---

### Post by talsemgeest on 2009-09-19
Well, I've given up and reinstalled. Might as well get started recreating that 700GB of data ;)

---


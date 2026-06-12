---
title: "Load hard drive BEFORE Dropbox"
date: 2010-02-19
forum: General Help
---

### Post by unxposed on 2010-02-19
Hi,

I've got Dropbox installed and working on Ubuntu 9.10. When I startup I also have my USB external hard drive load up automatically at /media/laCie (I've never changed the settings it's just done this automatically from day 1).

My dropbox folder is sitting at /media/laCie/Dropbox. 

The problem is that every time the computer starts I get a Dropbox popup saying it can't find the Dropbox folder, even though it's blatantly there and working, so I guess this means the hard drive is not loaded before Dropbox tries to find it! How do I change this so the hard drive is automatically loaded first.

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c7cc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
```

Thanks

---

### Post by ankspo71 on 2010-02-19
Hi,
I'm not sure if this will work or not, but I had a similar startup problem with transmission and this solved the problem for me.

Try using this as a startup application command:
```
sleep 15 && dropbox start -i
```(I just tested this in the terminal and it works)
(also adjust the sleep "15" to whatever value you think you need)

If that doesn't work, you might need to make a script:
First, you will need to disable the auto startup of dropbox. You can do that in dropbox preferences or in the startup applications list

Then create the script:
```

#!/bin/bash 
sleep 15 && dropbox start -i ;
```Save the above code as a text file named "start-dropbox.sh" and place it in your home folder.

Now go back to the startup applications list and add the following command:
```
sh /home/your-name/start-dropbox.sh
```Hope this helps.

> PS. If anyone is interested in the transmission script, here it is:
#!/bin/bash 
sleep 15 && nice -n 3 transmission -m ;

---

### Post by ankspo71 on 2010-02-19
Hi Again,

I created the dropbox script to test it on startup, and it works good. 15 seconds sleep time might not be long enough for your drive to load though, so you might want to make that 20 or 25 seconds. I tested the first command in the startup applications list too, but it didn't work. So creating the script might be your only option.

As far as getting your hard drive to load faster, I don't know if it could be done.

Hope this helps.

---

### Post by unxposed on 2010-02-19
Wow, works perfectly. 15 seconds seems to be enough, very satisfying!

Thank you so much!

---

### Post by cong06 on 2010-02-19
When I was using Dropbox, I wanted to disable the start up so I could control it's loading better.
Occasionally it would re-create the start up entry, so I'm not sure if that'll be an issue or not.

---

### Post by unxposed on 2010-02-19
I keep an eye on it and post here if I have any further problems with it.

Thanks again.

---


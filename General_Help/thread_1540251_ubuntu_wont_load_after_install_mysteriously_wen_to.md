---
title: "ubuntu wont load after install mysteriously wen to read only"
date: 2010-07-27
forum: General Help
---

### Post by sanitarium616 on 2010-07-27
i was moving some images over to my external hard drive last night and the install went to read only and i couldn't do anything so i rebooted and now i cant load into the desktop i just get init frames command line and i dont know what to do any help would be apretiated
sanitarium

---

### Post by quixote on 2010-07-30
When you say "the install went to read only" do you mean your ubuntu system became read only or the external hard drive did?  I'm assuming you mean the ubuntu OS.

Is there a chance that somehow during the process of moving you filled up your ubuntu partition?  Boot into recovery mode (the command line mode I think you're talking about) and type ```
df -h
```On my system, for instance, the output looks like this:```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  7.1G   11G  41% /
none                  1.9G  296K  1.9G   1% /dev
none                  1.9G  216K  1.9G   1% /dev/shm
none                  1.9G  104K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw
/dev/sda5             408G  177G  212G  46% /home

```
For your / partition, what is the Use%?

If the occupied space is over about 95%, the system can lock up like that.  The solution is to delete some files from the recovery command line, and try to free up enough space to boot.

If you do **not** have /home on a separate partition like I do (i.e. there'd be no /home partition in the df -h output), then one easy and harmless thing to delete is the .thumbnails directory in your home:```
rm -rf /home/[COLOR="Blue"]your-user[/COLOR]/.thumbnails
```.thumbnails will be recreated later. Substitute your login name for "your-user".  Be very careful with that command and make sure you haven't made any typos. There are **no spaces** anywhere after the first /.  You are root in recovery mode (same as "sudo") and can delete your whole ubuntu partition using a different form of rm -rf.

---

### Post by sanitarium616 on 2010-07-31
the ubuntu os install went read only i have a 1tb hard drive hand had next to nothing on it/installed. i've since given up and reinstalled as i was going mad with out my comp but i will take note of your help which i am very gratefull for 
thank you 
sanitarium

---

### Post by quixote on 2010-08-01
Well, with 1TB, space was definitely not the problem.  I have no idea what the problem could have been then.  Glad to hear you dealt with it, even if brute force was the only solution!

---


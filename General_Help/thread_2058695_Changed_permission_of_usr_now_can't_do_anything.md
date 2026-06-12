---
title: "Changed permission of /usr now can't do anything"
date: 2012-09-16
forum: General Help
---

### Post by ritchie888 on 2012-09-16
I stupidly changed the permission of usr and all its subfolders, now I can't do anything and since restarting things like the internet and trying to use sudo in terminal isn't working. 

How can I get my usr folder back to default permission? I seem to have been stripped of all admin rights.

The command I used to change usr permission was this:

sudo chmod -R 755 /usr

---

### Post by MC_Claus on 2012-09-16
Not quite sure how to fix that one, since CTRL+Z doesn't seem to work in a terminal :)

Do you know your root password? Then you can use 'su' and then chmod?

If you have a live CD/USB stick, perhaps this can help you?

---

### Post by ritchie888 on 2012-09-16
Ok, had a bit of luck with this, tried two methods to get sudo control back. 

First I used the liveCD and mounted my drive and had access that way, being able to change the permission. I've also been able to do the same by dropping to a root shell. Both methods allowed me to change, and I believe I have sudo control back, but still no internet access, nor does it seem to want to let me shutdown without forcing (pressing and holding the power button!).

What I've changed so far is usr/bin/sudo to get my sudo control back, but still need to change all other subfolders within usr so I can get everything back. 

Basically what I need now is for someone with a working system to check their permissions under usr and let me know what I need to change back, I'll be very grateful!

---

### Post by MC_Claus on 2012-09-16
/usr/
[FONT="Courier New"]drwxr-xr-x  12 root root  4096 sep 10 14:33 ./
drwxr-xr-x  24 root root  4096 sep 10 14:33 ../
drwxr-xr-x   2 root root 49152 sep 16 10:08 bin/
drwxr-xr-x   2 root root  4096 sep 10 14:42 games/
drwxr-xr-x  42 root root  4096 sep 10 15:13 include/
drwxr-xr-x 195 root root 40960 sep 16 10:07 lib/
drwxr-xr-x   4 root root  4096 sep 10 11:27 lib32/
drwxr-xr-x   4 root root  4096 sep 10 15:14 lib64/
drwxr-xr-x  10 root root  4096 apr 23 13:34 local/
drwxr-xr-x   2 root root 12288 sep 16 10:07 sbin/
drwxr-xr-x 312 root root 12288 sep 16 10:08 share/
drwxr-xr-x   5 root root  4096 sep 10 11:27 src/[/FONT]

---

### Post by ritchie888 on 2012-09-16
Legend. I'll give this a bash and will let you know.

---

### Post by ritchie888 on 2012-09-16
Unfortunately I still seem to be having permission problems. 

Had a new idea though, can someone tell me how to copy the /usr permissions from the liveCD to my system? 

If I boot into the liveCD and mount my drive, same as before, what would be the command to copy the permissions from the CD to my drive?

---

### Post by ritchie888 on 2012-09-16
Anyone? I'm coming up short here with a solution. No access to wireless or able to shutdown.

---

### Post by MC_Claus on 2012-09-16
I do not know of any oneliner command, that can do what you ask, but I guess you can create a bash script that can do what you ask, but I'm not a big bash wizz, but I guess it should be something in the lines of parsing output from ls -l and doing chmod with that.

Otherwise there is the good old manual way :)

---

### Post by snowpine on 2012-09-16
I would back up /home and reinstall, personally.

---

### Post by micahpage on 2012-09-16
I have done this before, except I did it with / . I fixed it without a reinstall with a liveCD. The problem is I don't remember what exactly i did, nor can find the notes that I wrote to fix it, sorry.

I will post back if i find the notes

---

### Post by Habitual on 2012-09-16
> **snowpine said:**
> ...back up /home and reinstall...

Almost  inevitable.

---

### Post by JKyleOKC on 2012-09-16
++1 to snowpine's re-install suggestion. There's no simple way to undo the effects of such a recursive permissions change, since some of the files require read/execute access for the world while others prohibit it. Only a reinstallation can put everything right, followed by hours of getting updates installed...

At best, it's a learning experience!

---

### Post by steeldriver on 2012-09-16
Agreed - you will probably end up reinstalling whatever you do now. Even if you copy the permissions from the LiveCD system's /usr, there's going to be stuff (i.e. packages you added post-install) that gets missed and will likely remain broken

FWIW if I *did* want to copy the perms from a running LiveCD I would probably try something like this (using 'stat' not 'ls')

```
$ while read file perm; do 
> if [ -e "/path/to/mountpoint$file" ]; then 
> echo chmod "$perm" "/path/to/mountpoint$file"; else
> echo "$file" : not found; fi
> done < <(find /usr -exec stat -c '%n %a' {} \;)

```I have left an 'echo' in which you would need to replace with 'sudo' to make it actually modify anything - it will give you an idea of how it would look

---

### Post by ritchie888 on 2012-09-16
Thanks everyone. 

I wanted to leave reinstalling as a last resort, but had to bite the bullet in the end.

Happily I'm back up to date with everything (minus game downloads) from before my stupidity, so pretty happy with the turn around.

---


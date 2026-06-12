---
title: "System Crash: Urgent Help Required !!!!!"
date: 2010-12-21
forum: General Help
---

### Post by mohanp06 on 2010-12-21
I am a newbie. Posting this thread for the first time here. I tried to search forums but i am not able to get to the solution.

I have 2 accounts in ubuntu.
'user' and 'mohanp'.

I have my important data in 'mohanp' account. but 'mohanp' account has crashed: i am not able to log in. One day suddenly I got some .ICEauthority related message then something like 'could not create home folder'. and now i am not able to log in to mohanp account.

i tried the foll. steps as found on one of the threads:

booting in recovery mode to root, updating EnableAutologin=false in the /etc/gdm/custom.conf file but there is not any such file in that directory.

My 'user' account is working. i am using it temporarily but cannot continue with that for long i fear it may also crash.

Also i need to update my ubuntu but it is saying no free space, It seems that a .Private folder is occupying lot of space. i cannot free space unless i log in into 'mohanp' account.

Also i cannot access my data it seems to be encrypted.

Kindly help me !!!

Thanking in advance..

Best Regards
Mohan

My system : AMD64, Ubuntu 10.04 LTS

---

### Post by dabl on 2010-12-21
> **mohanp06 said:**
> 

 One day suddenly I got some .ICEauthority related message then something like 'could not create home folder'. and now i am not able to log in to mohanp account.



So, it did not crash.  You used "sudo" to run a Gnome package, and it overwrote your user's permissions with root permissions, and now the user is locked out.  This is a common trap that the new users falls into.

Possibly you can fix it by booting into Recovery Console, choose "Drop to root prompt", and then change to the /home/mohanp directory.  When you are at

/home/mohanp#

then you can issue this command:

```
rm .ICEauthority .Xauthority
```

then

```
shutdown now -r
```

and when it restarts, you might be able to log in normally.

If it doesn't work, we will need a little more drastic measure.

---

### Post by mohanp06 on 2010-12-22
I tried the above steps but i got the foll message:

.Xuathority: No such file or directory

i tried shutdown now -r but still i am getting same message after logging in...

---

### Post by dabl on 2010-12-22
There is a slightly more drastic approach, which will delete all of your custom settings, both for the desktop and also for any packages that you have customized.  First, _be very sure_ to change to the /home/mohanp$ prompt -- do NOT do this at the filesystem root.

```
sudo rm -rf .*
```

This will delete every file that begins with a dot, including .Xauthority which you probably misspelled. It will not touch any data files or directories (unless you use a dot prefix on data files).

---

### Post by Verbeck on 2010-12-22
wouldn't it be even more safer to do it like
*sudo rm -rf /home/mohanp/.**
incase he's in the wrong directory?

---

### Post by dabl on 2010-12-22
> **Verbeck said:**
> wouldn't it be even more safer to do it like
*sudo rm -rf /home/mohanp/.**
incase he's in the wrong directory?

_Yes_, safer in the sense of avoiding damage to system.  Less safe (or perhaps less likely to succeed), in the sense of lots more opportunities for typos, which I think is the original problem ....

---

### Post by mohanp06 on 2010-12-23
Well, I tried the given steps but in vain...

Still i am getting the same message after logging in 'mohanp' account..

"could not update ICEauthority file /home/mohanp/.ICEauthority" 

I also tried copying all .* files from 'user' account to 'mohanp' account but in vain...

Also mentioning here just to avoid confusion regarding typo.. it was only in the post above that I had typed incorrectly..while running command i had put '.Xauthority' which was correctly spelled.

(Again please excuse me for the typos in the post: I am really desperate to get my machine running back ASAP  :( )

Thanks and Regards,
Mohan

---

### Post by psusi on 2010-12-23
Boot to rescue mode and type df -h.  If your root ( / ) filesystem is nearly full ( 94% or more ) then you need to free up some space.  You should be able to do this by running apt-get clean.

---


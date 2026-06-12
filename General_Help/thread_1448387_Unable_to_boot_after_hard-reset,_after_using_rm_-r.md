---
title: "Unable to boot after hard-reset, after using rm -r as root."
date: 2010-04-06
forum: General Help
---

### Post by barkaetarboris on 2010-04-06
Hi. First of all, i'll just say this myself. I'm a dumbass and tried to fix somethings that wasn't even a problem from the start and now my 9.10 installation is totally fubar. ](*,)There, done, now let's move on. 

Ok, so I tried to delete a folder after compiling two binaries to the wrong folder and used the ```
rm -r
``` command on what I thought was the folder /home/lars/bin. And to add to the dumbass-ering, I was root while doing this. The computer hangs and leaves me with no other options than doing a hard-reset via power-button.

After rebooting I can't even see the login screen, it just hangs at the Ubuntu symbol. :confused:

So I give the recovery mode option in my grub menu a try and it gives me a bunch of lines, all looking good until I get this and the boot just stops with a blinking underscore.

```
Begin: Running /scripts/init-bottom
Begin: Starting AppArmor profiles
chroot: Cannot execute /etc/apparmor/initramfs: No such file or directory
Failure: AppArmor profiles failed to load
Done.
init: job_process.c:529: unhandled error from job_process_spawn: no such file or directory
init: Failed to spawn hostname main process: unable to execute: No such file or directory
init: Failed to spawn hwclock main process: unable to execute: No such file or directory
init: job:process.c:529: Unhandled error from job_process_spawn: No such file or directory
init: job:process.c:529: Unhandled error from job_process_spawn: No such file or directory
init: Failed to spawn mountall main process: unable to execute: No such file or directory
init: job:process.c:529: unhandled error from job_process_spawn: No such file or directory
init: Failed to spawn mountall post-stop process: unable to execute: No such file or directory
```I've managed to boot with the live-cd and backup my /home/lars data to my Win7 partition, but I don´t know where to go from here using the live-cd...

Should I just beat myself for a while and then reinstall the OS or what...?

The hardware involved is a Asus EEEpc 1000h.

ps. I'm new to Linux and have so-far managed to get around by following guides and tips, just a heads-up.

Thx.

Lars. (barkaetarboris)

---

### Post by QIII on 2010-04-06
Ouch!  Removing recursively while root.

Well.  Don't let anyone tell you they never made a similar mistake when they first started.  If someone tells you that, I'll tell you who's a liar.

What directory were you in at the time?  Depending on what it was, you may have been well and truly fornicated as far as the OS, but I'm glad to hear you got your /home recovered.

---

### Post by jamesisin on 2010-04-06
Yeah, like QIII says it really depends upon which directory you were actually in when you ran rm.  You say you *thought* you were in /home/lars/bin but were you in /bin?  /usr/bin? /?

Also I might remind you that it is April.  This means that 10.04 should be ready any minute.  Maybe this is an opportunity and not so much a disaster?  After all, you were able to save /home.

---

### Post by ankspo71 on 2010-04-06
My advice is as long as you have everything you need backed up, you could perform a reinstall in 20 to 30 minutes. It could take anyone hours (or longer) to find each broken application and reinstalling them. The system might not ever be as good again either. If you have your entire home directory backed up then chances are you have most of your settings backed up as well. I had a similar accident once when I partially deleted my home folder while trying to create a nautilus script for the shred command.

---

### Post by QIII on 2010-04-06
Hmmm.....

Lucid as a production OS right now for a beginner?  Almost...  almost.... almost..........

I've been using it as a primary for quite some time now, but I've also been at this a while.  What would be a minor irritation for me might end up bringing tears of frustration and lost data to a relative newcomer.

Tough call.

---

### Post by barkaetarboris on 2010-04-06
First of, thanks alot for the quick responses, I'm really starting to like this whole Linux-community-helper-outer-thing... :)

> **jamesisin said:**
> Yeah, like QIII says it really depends upon which directory you were actually in when you ran rm.  You say you *thought* you were in /home/lars/bin but were you in /bin?  /usr/bin? /?

I really don't know what directory I was in, but I really do think I was in /home/lars/bin cuz' I had just tried to copy some files there from the terminal and ended up copying the whole folder and subdirectories and not just the few files I wanted. So I thought "F*ck it, i'll just remove this mess and start over" As it turns out, BAD idea... :rolleyes:


[QUOTE=ankspo71]My advice is as long as you have everything you need backed up, you  could perform a reinstall in 20 to 30 minutes. It could take anyone  hours (or longer) to find each broken application and reinstalling them.  The system might not ever be as good again either. If you have your  entire home directory backed up then chances are you have most of your  settings backed up as well. I had a similar accident once when I  partially deleted my home folder while trying to create a nautilus  script for the shred command.     [/QUOTE]I think I got most of it, but I didn't have permission to read a bunch of folders, like .kismet and the likes. Is there a way to become sudo in nautilus so I can see what I'm doing? I don´t wanna mess up even more... :-? EDIT: Never mind. Just did this: ```
sudo nautilus
```

And I'm thinking of this as a learning experience, right now I don´t really care if it takes me some time and frustration finding and fixing broken packages if I could just figure out how to get started and learn from this little mess I've created all by my self!

If I could just get a terminal going I think I might be able to undo my misstakes by googling alot and reinstalling packages...

How would i go about reinstalling packages from the live-cd?

BTW: ```
fsck -fyv /dev/sda5
``` (performed AFTER umonting it) gives me no errors, but I'm thinking maybe the hard-reset wrecked havoc? Or would that have showed up with the fsck? (pardon the engrish, I'm from sweden)

---

### Post by pastalavista on 2010-04-06
You could just reinstall in place without reformatting. Keep user name the same. Manually select partitions and uncheck the format boxes. Save a copy of /etc/apt/sources.list to replace afterwards and do updates and you should be back where you started. I've done it several times without losing any data (backup anyway) ;)

---

### Post by barkaetarboris on 2010-04-06
> **pastalavista said:**
> You could just reinstall in place without reformatting. Keep user name the same. Manually select partitions and uncheck the format boxes. Save a copy of /etc/apt/sources.list to replace afterwards and do updates and you should be back where you started. I've done it several times without losing any data (backup anyway) ;)

Oh, this sounds like the way to go. I'll try this. Will I get a bunch of semi-broken and almost installed programs after doing this? For exampel I have patched my r8187 drivers for my networkcard to work with monitor-mode. I guess those things will be undone?

---

### Post by jamesisin on 2010-04-06
You could take a look at /home/lars/bin using the LiveCD.  That should give you a fair indication of whether that was the directory you borked.

I like the sound of pastalavista's solution, but I would want more details on how to go about it.

QIII - You don't think the final release will be suitable for common users?  I can't imagine it'll be *more* frustrating than "oops, I deleted my system files"...

---

### Post by jamesisin on 2010-04-06
> **barkaetarboris said:**
> For exampel I have patched my r8187 drivers for my networkcard to work with monitor-mode. I guess those things will be undone?

If you create a backup first, you can always dig into that to pick out any remaining config files or what have you.

---

### Post by pastalavista on 2010-04-06
Any files added since the last install will still be there. But any system file you've changed will be overwritten. You shouldn't have to install them again but you will need to reconfigure some of them. Save any config files that aren't in you /home directory along with your sources.list that you remember changing.

---

### Post by barkaetarboris on 2010-04-06
> **jamesisin said:**
> You could take a look at /home/lars/bin using the LiveCD.  That should give you a fair indication of whether that was the directory you borked.

I like the sound of pastalavista's solution, but I would want more details on how to go about it.

QIII - You don't think the final release will be suitable for common users?  I can't imagine it'll be *more* frustrating than "oops, I deleted my system files"...


I'm looking at it now, and everything and everything seems fine. All my folders like Pictures and Documents are still there. And the folders I where trying to delete just sits there, laughing at my futile atempts to evict them... :evil:

Don´t really know what to look for in other folders, as i'm rather new to linux...

---

### Post by jamesisin on 2010-04-06
Just to give you some ideas of scale, my /bin contains 113 items and my /usr/bin contains 2,446 items.  Your system obviously won't have those exact numbers, but this should give you a general idea of scale.

I don't seem to find a /home/[username]/bin folder.  Are you certain of that folder location?  (I looked on both an 8.10 and a 9.10 system.)

---

### Post by barkaetarboris on 2010-04-06
> **jamesisin said:**
> Just to give you some ideas of scale, my /bin contains 113 items and my /usr/bin contains 2,446 items.  Your system obviously won't have those exact numbers, but this should give you a general idea of scale.

Allright, I'll have a look /bin folders. Probably won't do much good but I'm really trying hard to turn this into a good learning thing...

EDIT: /usr/bin had 1481 items and I don't even have an /bin folder.... I can see the boot, cdrom, dev, etc, home, lib and things like that, but no bin folder. Got an sbin though. Not the same i guess.... Did I manage to completely remove the /bin folder...?


> **jamesisin said:**
> I don't seem to find a /home/[username]/bin folder.  Are you certain of that folder location?  (I looked on both an 8.10 and a 9.10 system.)

Yeah, I created that folder to house some of my own installations. Maybe a bad folder name, as it is kinda easy to wreck the OS by messing with the wrong one...

---

### Post by barkaetarboris on 2010-04-06
Just found the .bash_history for root, so let's have a look at what NOT to do. Just gonna cut to the dumbass-part.

```
ls
cd /home/lars/Hamster
cp -r /home/lars/Hamster/ferret/bin bin
cd /home/lars/Hamster
ls
cd bin
ls
cp -r /home/lars/Hamster/hamster/bin bin
cd /home/lars/Hamster
ls
cd bin
ls
ls
rm /bin
rm -r /bin
ls
ls
dir
ls
/bin
cd /bin
```Yup. I'm a dumbass! ):P Having a good laugh at myself right now, I'll tell ya that!

EDIT: Seems I didn't remember the file structure correctly. Honest misstake.

---

### Post by QIII on 2010-04-06
> **jamesisin said:**
> QIII - You don't think the final release will be suitable for common users?  I can't imagine it'll be *more* frustrating than "oops, I deleted my system files"...

Not what I'm saying at all!

I think the RC will be good enough.  Since this is an LTS, I expect it will be a great version for newcomers.

Betas (and we won't even mention Alphas) are generally not the way to go for the uninitiated who want a stable primary system.

---

### Post by jamesisin on 2010-04-06
> **barkaetarboris said:**
> I don't even have an /bin folder... Did I manage to completely remove the /bin folder?

Looks that way.  Your code seems to align with the fact that it's missing.

A couple of words about your code.  First, I generally never su to root.  I use sudo (or gksudo for graphical applications) for any root-like work needed.  I think this is would be considered a best practice for any system using sudo.

Your mistake came when you used rm /bin and rm -r /bin.  The / designation takes you from top (/) of the folder hierarchy.  If you were in a direcotry with a sub called bin you would want to issue rm ./bin or simply rm bin (if bin is empty) or rm -r ./bin or rm -r bin (if you want recursion).

My preference when deleting a directory is to use the full path (rm -r /home/[username]/exact/path) so as to assure myself I am deleting exactly what I intend to delete.

Do you know about tab completion on the command line?  If you type /ho and hit tab your system should change it to /home/ and this makes using those full paths much easier.  Tab completion should also work if you type ~/fol and tab to get /home/[username]/folder.

So, yes, it looks like you deleted your /bin folder.  Oops.  This means that really you would have to recreate that /bin folder.

> **QIII said:**
> Betas (and we won't even mention Alphas) are generally not the way to go for the uninitiated who want a stable primary system.

Hence my saying it *will be* out soon.  The final release comes out this month (or is supposed to), but I don't know which day.

---

### Post by barkaetarboris on 2010-04-07
> **jamesisin said:**
> Looks that way.  Your code seems to align with the fact that it's missing.

A couple of words about your code.  First, I generally never su to root.  I use sudo (or gksudo for graphical applications) for any root-like work needed.  I think this is would be considered a best practice for any system using sudo.

Your mistake came when you used rm /bin and rm -r /bin.  The / designation takes you from top (/) of the folder hierarchy.  If you were in a direcotry with a sub called bin you would want to issue rm ./bin or simply rm bin (if bin is empty) or rm -r ./bin or rm -r bin (if you want recursion).

My preference when deleting a directory is to use the full path (rm -r /home/[username]/exact/path) so as to assure myself I am deleting exactly what I intend to delete.

Do you know about tab completion on the command line?  If you type /ho and hit tab your system should change it to /home/ and this makes using those full paths much easier.  Tab completion should also work if you type ~/fol and tab to get /home/[username]/folder.

So, yes, it looks like you deleted your /bin folder.  Oops.  This means that really you would have to recreate that /bin folder.

I'll definitely do as you suggest and start using sudo instead, and specify the exact path. In ```
rm -r ./bin
``` does the "." specify that only /bin folder under my current directory will be affected?

Gonna reinstall the OS without formatting as per pastalavistas suggestion, and then copy my /home folder and sources list back. If that doesn't work I'll just start from scratch. I did manage to get all my (semi)important files back...

Marking the thread as solved.

Thx for the help and suggestions.

---

### Post by jamesisin on 2010-04-07
The . is a shorthand for whatever is in pwd (print working directory).  You will need it when you want to run a script, for instance, in a directory in which you are (but which is not in your $PATH).

```
$ cd /some/special/folder
$ pwd
/some/special/folder
$ ./myscript.sh
```

It is similar to .. which means the parent to whatever happens to be in pwd.

```
$ cd .. [or cd ../]
$ pwd
/some/special
```

You will see both . and .. if you run ls -a on any directory (they will be the first two items listed as contents).

Sensible enough?

I would still recommend using the full path over using the . shorthand when performing more robust operations (like deleting important directories).

---

### Post by barkaetarboris on 2010-04-08
> **jamesisin said:**
> The . is a shorthand for whatever is in pwd (print working directory).  You will need it when you want to run a script, for instance, in a directory in which you are (but which is not in your $PATH).

```
$ cd /some/special/folder
$ pwd
/some/special/folder
$ ./myscript.sh
```It is similar to .. which means the parent to whatever happens to be in pwd.

```
$ cd .. [or cd ../]
$ pwd
/some/special
```You will see both . and .. if you run ls -a on any directory (they will be the first two items listed as contents).

Sensible enough?

I would still recommend using the full path over using the . shorthand when performing more robust operations (like deleting important directories).


Thanks, that clarifies it.

Just an update, did the reinstallation as per pastalavistas recomendation and it worked great, albeit with some minor bugs. Booting kernel 2.6.31-20 gave me a login screen but no mouse, could login but couldn't use the touchpad. After rebooting I choose 2.6.31-14 and did a full update ('bout 240~Mb), rebooted, choose 2.6.31-20 again, and voilá! Fully operational! My home folder was left intact, didn't have to copy back from my backup. Just some applications and driver updates and it's just the same state as before I messed it up.

Thanks!

---

### Post by pastalavista on 2010-04-08
> **barkaetarboris said:**
> Thanks, that clarifies it.

Just an update, did the reinstallation as per pastalavistas recomendation and it worked great, albeit with some minor bugs. Booting kernel 2.6.31-20 gave me a login screen but no mouse, could login but couldn't use the touchpad. After rebooting I choose 2.6.31-14 and did a full update ('bout 240~Mb), rebooted, choose 2.6.31-20 again, and voilá! Fully operational! My home folder was left intact, didn't have to copy back from my backup. Just some applications and driver updates and it's just the same state as before I messed it up.

Thanks!

I'm glad it worked for you. Next time you're handling multiple files in different directories, it might be easier (it is for me) to use the 'root file manager' ala```
gksu nautilus
``` You can still mess things up if you aren't careful but it makes it a little easier to be careful.

---

### Post by jamesisin on 2010-04-09
> **pastalavista said:**
> ...it might be easier (it is for me) to use the 'root file manager' ala```
gksu nautilus
```

Though this is also dangerous territory, still let's build good habits:

```
gksudo nautilus
```

---

### Post by YannBuntu on 2011-07-25
Hi
For information, a similar case happened to a French user. He could solve it just by reinstalling GRUB via [Boot-Repair]("http://ubuntuforums.org/showthread.php?p=10871917#post10871917").

Hope this will help people getting this bug.

---


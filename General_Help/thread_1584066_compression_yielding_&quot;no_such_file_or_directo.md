---
title: "compression yielding &quot;no such file or directory&quot;"
date: 2010-09-28
forum: General Help
---

### Post by VideoAddicted on 2010-09-28
I'm trying to back up my /home/username folder for the purposes of a clean install.  I'm attempting to compress the folder to fit onto my flash drive and am running into problems.  Regardless of where I try to put the compression, or what compression algorithm I try, they all give me the error "no such file or directory" and that's all the computer will tell me.  Currently I've tried the tar.gz and tar.bz2 algorithms and have tried compressing to //, /home/, and /tmp/.  

Am running Ubuntu 10.04

---

### Post by CharlesA on 2010-09-28
Post what command are you running, please.

---

### Post by VideoAddicted on 2010-09-28
I'm manipulating the files using graphically using gksudo nautilus

---

### Post by CharlesA on 2010-09-28
Ok, so nautilus is giving you an error message?

Try this:

cd into /home/ and run this:

```
sudo tar -acf /tmp/test.tar.gz username
```

---

### Post by VideoAddicted on 2010-09-28
tar: username: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors

ran that code, got that

---

### Post by CharlesA on 2010-09-28
Run it and replace "username" with the name of your home directory.

---

### Post by VideoAddicted on 2010-09-28
That's what I did, I replaced my username in the error with username, sorry for not mentioning that

---

### Post by CharlesA on 2010-09-28
Strange, it worked for me when I tried it.

Was anything placed in /tmp/ ?

---

### Post by psusi on 2010-09-28
Did you remember to cd /home first?  What does ls show?

---

### Post by CharlesA on 2010-09-28
Good point.

Running this will tell you where you are:

```
pwd
```

The reason for changing to the /home/ directory is to grab compress the entire home directory with tar.

---

### Post by VideoAddicted on 2010-09-28
I used cd /home and tried to compress my home folder into tmp and I'm still receiving the error.  and to answer the other question, yes, there are other files in /tmp

---

### Post by CharlesA on 2010-09-28
Ok in that case, try running this from yer home directory:

```
sudo tar -cf /tmp/homedir.tar *
```

---

### Post by VideoAddicted on 2010-09-29
and here we go, more errors

tar: username/.gvfs: Cannot stat: Permission denied
tar: Exiting with failure status due to previous errors

like always, I replaced all instances of my name in the error with "username"

---

### Post by CharlesA on 2010-09-29
Do you have an encrypted home directory?

I don't know why it's throwing up that error.

---

### Post by VideoAddicted on 2010-09-29
I never did anything to that effect manually, but if you'll tell me how to check, I'll gladly relay the information.

---

### Post by psusi on 2010-09-29
> **VideoAddicted said:**
> and here we go, more errors

tar: username/.gvfs: Cannot stat: Permission denied
tar: Exiting with failure status due to previous errors

like always, I replaced all instances of my name in the error with "username"

This is normal when using sudo.  Either don't use sudo, or ignore this message.

---

### Post by CharlesA on 2010-09-29
> **psusi said:**
> This is normal when using sudo.  Either don't use sudo, or ignore this message.

That normal with using tar with sudo, then?

---

### Post by VideoAddicted on 2010-09-29
Is there another way then to compress my /home/username directory so that I can back it up?

---

### Post by VideoAddicted on 2010-09-29
Don't know if this helps, but there is a homedir.tar archive in my /tmp directory which when I try to view its contents yields the following errors

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

---

### Post by CharlesA on 2010-09-29
I figure there is something screwy about yer home directory.

I'd suggest just copying everything in it to another place and going from there.

---

### Post by psusi on 2010-09-29
> **CharlesA said:**
> That normal with using tar with sudo, then?

It is normal when using sudo with anything that walks your home directory.  The .gvfs directory is only accessible to you, not to root.

> **VideoAddicted said:**
> Is there another way then to compress my /home/username directory so that I can back it up?

You already did.

> **VideoAddicted said:**
> Don't know if this helps, but there is a homedir.tar archive in my /tmp directory which when I try to view its contents yields the following errors

tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

What happens when you do tar tf /tmp/homedir.tar?

---

### Post by CharlesA on 2010-09-29
> **psusi said:**
> It is normal when using sudo with anything that walks your home directory.  The .gvfs directory is only accessible to you, not to root.

Thanks for the info. I was under the impression that the root account can access everything on the file system.

I tried the same command on my desktop install and it spit back the same error. Using tar without sudo worked fine.

Thanks.

---

### Post by VideoAddicted on 2010-09-29
psusi's suggestion starts yielding a list of the files that should be in the archive but then yields the following error

Error while copying

Files in the folder "jesse" cannot be handled because you do not have permissions to see them.

On the other hand, when I tried to run the previous command without using sudo I got this

tar: Cowardly refusing to create an empty archive
Try `tar --help' or `tar --usage' for more information.

which is an error that I've yet to see in this glorious adventure of mine

---

### Post by jwbrase on 2010-09-29
> **VideoAddicted said:**
> psusi's suggestion starts yielding a list of the files that should be in the archive but then yields the following error

Error while copying

Files in the folder "jesse" cannot be handled because you do not have permissions to see them.

What do you get with:

```
sudo ls -l jesse
```

Run from the parent folder of "jesse"?

You should see a bunch of files listed this way:

```
-rw-r--r--  1 [owner]  [group]         [size] [date] [time] filename
```

If the first "r" isn't there for any of the files in jesse, or if [owner] is anything other than "username" (most likely "root"), that will explain the error. For all files that don't have the first "r", run:

```
sudo chmod u+r filename
```

For any files where [owner] is not "username":

```
sudo chown username filename
```

---

### Post by VideoAddicted on 2010-09-30
the first command yields

ls: cannot access jesse: No such file or directory

---

### Post by VideoAddicted on 2010-09-30
scratch that, forgot to run in /home directory

---

### Post by VideoAddicted on 2010-09-30
Some files had dr at the beginnings rather than -r but other than that every single file had that first r and the owner in every case was /home/jesse

---

### Post by psusi on 2010-09-30
I can only guess that you are mixing up pieces of different commands.  Open a terminal, and it should already be in your home directory.  You can tell this because the prompt will show "~/".  Then run:

tar czf stuff.tar.gz --exclude=stuff.tar.gz *

---

### Post by VideoAddicted on 2010-09-30
running that code from the default directory (/home/jesse) yields the following

jesse@chrome:~$ cd /home
jesse@chrome:/home$ tar czf stuff.tar.gz --exclude=stuff.tar.gz *
tar: stuff.tar.gz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

I've now started the code running in the /home directory and I'm currently waiting for it to finish, I'll post again when it does.

---

### Post by dino99 on 2010-09-30
you can set your rights as you want/need with mountmanager

---

### Post by psusi on 2010-09-30
> **VideoAddicted said:**
> 
jesse@chrome:~$ cd /home

Don't do this part.

> **VideoAddicted said:**
> 
jesse@chrome:/home$ tar czf stuff.tar.gz --exclude=stuff.tar.gz *
tar: stuff.tar.gz: Cannot open: Permission denied
tar: Error is not recoverable: exiting now

I've now started the code running in the /home directory and I'm currently waiting for it to finish, I'll post again when it does.

That's what you did above and you got an error because you can't create a file in /home.  Maybe you meant to say you tried it again WITHOUT changing to /home?

---

### Post by VideoAddicted on 2010-09-30
the code finally ran through, but I'm not sure if it did anything, here's what's in my terminal.

jesse@chrome:~$ tar czf stuff.tar.gz --exclude=stuff.tar.gz *
jesse@chrome:~$ 

It ran through without errors, but it didn't yield any new lines of text in the window either...

however, there is now a jesse folder in my filesystem that seems to have everything i need but I'm not sure.  What folders should I look for that are important beyond my miscellaneous word docs and the such?

---

### Post by VideoAddicted on 2010-09-30
> **psusi said:**
> Don't do this part.



That's what you did above and you got an error because you can't create a file in /home.  Maybe you meant to say you tried it again WITHOUT changing to /home?

No, when I don't change it, I get errors.  If I change the directory to /home/ then the code runs through as I mentioned although I'm not totally sure that it was effective

---

### Post by psusi on 2010-09-30
> **VideoAddicted said:**
> the code finally ran through, but I'm not sure if it did anything, here's what's in my terminal.

jesse@chrome:~$ tar czf stuff.tar.gz --exclude=stuff.tar.gz *
jesse@chrome:~$ 

It ran through without errors, but it didn't yield any new lines of text in the window either...

however, there is now a jesse folder in my filesystem that seems to have everything i need but I'm not sure.  What folders should I look for that are important beyond my miscellaneous word docs and the such?

Then it worked.  You understand the purpose of this was to pack all of your files into stuff.tar.gz?  What you might call zipping.  Your last comment doesn't make sense in that context.

---

### Post by renkinjutsu on 2010-09-30
I propose this as a solution: (because I like to have higher compression)```

tar --exclude=${HOME}/.gvfs --exclude=${HOME}/backup.tar.xz -cpvJf ${HOME}/backup.tar.xz ${HOME}
```

That should give put a "backup.tar.xz" in your home directory (/home/username)
Also, it's recommended that you don't use your computer while you backup with tar, because tar is very sensitive to files changing during the archiving process. When you use programs many hidden files may be written to, making tar give you errors.

---

### Post by VideoAddicted on 2010-09-30
I have run a complete search of my filesystem, and there is no file called stuff.tar.gz.  I am trying the other suggestion which will compress everything into a tar.xz but it will take a while yet and I will post with results once it resolves.

---

### Post by VideoAddicted on 2010-10-01
I've tried running it through a few times now, and recently my computer has started crashing spontaneously.  So, I haven't been able to get it to finish because of how long it takes.  Any suggestions?

---

### Post by psusi on 2010-10-01
Open a terminal and run ls -l stuff.tar.gz.

---

### Post by VideoAddicted on 2010-10-01
ls: cannot access stuff.tar.gz: No such file or directory

---

### Post by renkinjutsu on 2010-10-01
I wonder why your computer is crashing.. maybe low disk space?

show us ```
df -h
```

---

### Post by VideoAddicted on 2010-10-01
jesse@chrome:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G  141G   76G  65% /
none                 1003M  264K 1002M   1% /dev
none                 1007M  184K 1006M   1% /dev/shm
none                 1007M  200K 1006M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sr0              4.2G  4.2G     0 100% /media/Oblivion GOTY 1
jesse@chrome:~$ 

I'm also very curious.

---

### Post by psusi on 2010-10-01
My guess is that if your computer crashed not long after you made the tar, the file was lost because of the crash.  Try making it again.

---

### Post by VideoAddicted on 2010-10-01
I ran the code again, and it seemed to go through without any major problems.  I found stuff.tar.gz in my home folder and tried to open it and was greeted with the followed errors.

tar: Skipping to next header
tar: Exiting with failure status due to previous errors

Not sure what this means, I hope you do.

---

### Post by psusi on 2010-10-01
I think your disk might be hosed.  Open the disk utility and run the extended smart test.

---

### Post by VideoAddicted on 2010-10-02
I'm sorry, but could you tell me how to do that?  On another note, will doing a fresh install of the OS fix it or do you think that it's actually the disk that having problems?

---

### Post by psusi on 2010-10-02
System -> Administration -> Disk Utility.  Click on the drive, then click smart data, then click self test.

---

### Post by VideoAddicted on 2010-10-02
Thanks, unfortunately I don't have access to my system till tomorrow evening so I will post with results as soon as I can.

---

### Post by VideoAddicted on 2010-10-03
I ran the short self scan as well as the extended self scan and neither found any problems with my hard drive.  They both said that the drive was fine and that there were no 'bad sectors'.

---

### Post by VideoAddicted on 2010-10-05
Today I took my system into my computer science professor and he was able to get my system to backup without errors.

---


---
title: "tar Takes forever"
date: 2010-05-07
forum: General Help
---

### Post by slick666 on 2010-05-07
Dear forum,

What I wanted to do is backup my home directory and install 10.04 (I had 9.04) and then restore the home directory. My home dir was about 150 GBytes. I ran the command below
```
tar --use-compress-program=lzop -cf homeDir.tar.lzop /home/user
```

I then ran
```
lzop -t homeDir.tar.lzop
```
to test it and it tested out fine. It compressed it down to about 110 GBytes. I copied the file off the machine and installed 10.04.

On the new system I copied the file on and first decompressed it using this command
```
lzop -x homeDir.tar.lzop
```
and it gave me the file **homeDir.tar**.

I'm now trying to untar the file but everything seems to hang. Right now I'm executing ```
time tar --extract homeDir.tar 
``` and it's just sitting there. I copied the tar file off onto another system and it's doing the same thing. I've let this thing run now for about 3 hours with no change.

I know archive the files might add some overhead but it only took me an hour to archive and compress it to begin with. Add to that I transfered the uncompressed in an hour. At this rate it would have made more sense to scp the files over directly. Why would it take this long to unarchive this file?

Any thoughts appreciated.

---

### Post by jbrown96 on 2010-05-07
> **slick666 said:**
> Dear forum,

What I wanted to do is backup my home directory and install 10.04 (I had 9.04) and then restore the home directory. My home dir was about 150 GBytes. I ran the command below
```
tar --use-compress-program=lzop -cf homeDir.tar.lzop /home/user
```

I then ran
```
lzop -t homeDir.tar.lzop
```
to test it and it tested out fine. It compressed it down to about 110 GBytes. I copied the file off the machine and installed 10.04.

On the new system I copied the file on and first decompressed it using this command
```
lzop -x homeDir.tar.lzop
```
and it gave me the file **homeDir.tar**.

I'm now trying to untar the file but everything seems to hang. Right now I'm executing ```
time tar --extract homeDir.tar 
``` and it's just sitting there. I copied the tar file off onto another system and it's doing the same thing. I've let this thing run now for about 3 hours with no change.

I know archive the files might add some overhead but it only took me an hour to archive and compress it to begin with. Add to that I transfered the uncompressed in an hour. At this rate it would have made more sense to scp the files over directly. Why would it take this long to unarchive this file?

Any thoughts appreciated.

try adding -vv or -v after tar to give you more output.

---

### Post by lmarmisa on 2010-05-07
You can list the contents of your tar file typing this command

> 
tar tvf homeDir.tar
Best regards,

Luis

---

### Post by slick666 on 2010-05-07
I've tried the -v and -vv options too
```
tar -xvvf homeDir.tar
```

It gave me the same output. I've let the script run for 11 hours now but I'll be back to check on it later. I have the time option just in case it finishes.

---

### Post by lmarmisa on 2010-05-07
The problem is probably related to the writing of the files because some of the destinations files can be locked by the different programs that you are running. So I recommend to check the contents of the tar file using the t option and not the x.

tar tvf homeDir.tar

If the tar file is Ok, you could try to restore the content of the tar file in a temporary directory different than /home/user. In a next step you could try to move the files or directories from this temporary directory to the /home/user.

---

### Post by slick666 on 2010-05-10
What I ended up doing for the extraction was to extract under root in the /root folder. what I would expect is that all the directories under the home directory would appear. I'm not using the verbose option but the program has been running on two computer for almost 70 hours now. It only took an hour to compress in the first place so something has gone wrong.

File roller seems to be able to look in the archive and pull out individual files so I'm going to try that and see if I can get anywhere.

---

### Post by slick666 on 2010-05-10
Man I can't believe this works
```
tar --use-compress-program=lzop -xvf homeDir.tar.lzop
```

Why would this work and not the other way that I tried?

---


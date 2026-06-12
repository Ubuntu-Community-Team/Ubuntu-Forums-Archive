---
title: "Backing up Ubuntu 9.10 problems/questions"
date: 2010-03-21
forum: General Help
---

### Post by SCort5 on 2010-03-21
Currently I am backing up ubuntu 9.10 using the terminal with the following commands:

sudo su

cd /

**tar cvpzf mybackup.tgz / --exclude=/backup.tgz --exclude=/proc --exclude=/lost+found   --exclude=/mnt --exclude=/sys** --exclude=/media

As it started to work the backuping stopped with this message: 

tar: Exiting with failure status due to previous errors

this is a few lines before the message:

...
/boot/vmcoreinfo-2.6.31-20-generic
/boot/System.map-2.6.31-14-generic
/boot/vmcoreinfo-2.6.31-14-generic
/boot/initrd.img-2.6.31-14-generic
/boot/System.map-2.6.31-20-generic
/boot/abi-2.6.31-20-generic
tar: Exiting with failure status due to previous errors


What is wrong? Is abi-2.6.31-20-generic the problem? What should I do?

---

### Post by blueridgedog on 2010-03-21
I recommend running the backup and piping the output to a file so you can see the error.  For example:

```
tar cvzf test.tgz /documents/ > errors.txt
```

When the failure hits, you can review errors.txt to see what it actually complained about.

One error I see is that you are creating a file called mybackup.tgz, but not excluding it, so it is possible that it is being backed up while it changes.

---

### Post by SCort5 on 2010-03-21
> **blueridgedog said:**
> I recommend running the backup and piping the output to a file so you can see the error.  For example:

```
tar cvzf test.tgz /documents/ > errors.txt
```When the failure hits, you can review errors.txt to see what it actually complained about.

One error I see is that you are creating a file called mybackup.tgz, but not excluding it, so it is possible that it is being backed up while it changes.


Actually I did exclude the backup file.

---

### Post by blueridgedog on 2010-03-21
You are creating a file called mybackup.tgz and excluding a file called backup.tgz.  There may be more to the command than I see, but I would still direct standard output to a file to see what is going on.

---

### Post by SCort5 on 2010-03-22
What do you mean by "direct standard output"?

---

### Post by blueridgedog on 2010-03-22
If you run the command:

```
tar cvzf test.tgz /documents/
```

You will get messages in the terminal.  The printed messages that are displayed as the program runs are called "standard output"  i.e. the basic printing that the program or task sends back to the terminal.

Sometimes the messages go by too fast to notice and it makes it hard to track down an error.  

In such cases, a good practice is to direct the text (called standard output) to a file.  To do this you use the ">" sign to send the text/standard output to a file.  Here is an example:

```
tar cvzf test.tgz /documents/ > errors.txt
```

In this case the text messages that would normally be printed on the screen are sent instead to the fire errors.txt.  After the command runs, you can view the file and learn whey the operation failed by looking for information that you missed previously.

---

### Post by SCort5 on 2010-03-23
so using the commands you gave me, I should check what errors I have. Through this I will be able to determine what went wrong meaning.

In my case I should replace 'test.tgz' with 'backup.tgz' but what should I do for the '/documents/ part then?


Edit: By the way this is the site that I got the code from:
[http://www.hddsaver.com/content/26/index.html](http://www.hddsaver.com/content/26/index.html)

---

### Post by blueridgedog on 2010-03-23
Your command would look like this:
```

tar cvpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media > errors.txt
```

I changed your first exclude to match the name of the file you are creating (mybackup.tgz) and added "> errors.txt" at the end so that the ouput of the command goes into the text file, rather than on on screen.  

After the command runs, you can review the file "errors.txt" to see if there were any abnormalities in the job.

It may run fine by excluding "mybackup.tgz" rather than "backup.tgz".

Good luck and you can post the errors here if you find the cause of the failed backup job.

---

### Post by SCort5 on 2010-03-23
The changing the 'backup' to 'mybackup' didn't work.

The errors seem to keep happening at '/boot/abi-2.6.31-20-generic'

I do not see anything wrong on errors.txt

---

### Post by john newbuntu on 2010-03-24
errors.txt in your case is actually called a standard output and not standard error.
Any error or message that you see on your screen that immediately follows the command is the standard error (since it was not redirected to another file).

A few such errors could be:
tar: Removing leading `/' from member names
tar: Removing leading `/' from hard link targets
tar: /var/run/dbus/system_bus_socket: socket ignored
tar: /home/jack/.gvfs: Cannot stat: Permission denied
etc.

Can you please list all such errors in your next post.  BTW, you can also safely ignore the /tmp directory.  So add "--exclude=/tmp" to your command without quotes.

Also, _immediately after you run the command_, type:
```
echo $?
```
and let us know what it prints.  This is the error code of the tar command.

Sometimes, it is possible for the root to not have access to certain files or a potential corruption on files that might cause it to not include it in the tar/zipped file leading to a failure while tar'ing.

---

### Post by SCort5 on 2010-03-24
> **john newbuntu said:**
> 

Also, _immediately after you run the command_, type:
```
echo $?
```and let us know what it prints.  This is the error code of the tar command.




Typed that it and all that came out was 

'2'

Is that supposed to tell me the number of errors I have?

---

### Post by john newbuntu on 2010-03-25
If tar succeeded, it would have returned 0.  2 indicates your tar command failed.  You did not list the other messages that showed up on your screen.  We can try and solve this once you list it.

---

### Post by SCort5 on 2010-03-25
> **john newbuntu said:**
> If tar succeeded, it would have returned 0.  2 indicates your tar command failed.  You did not list the other messages that showed up on your screen.  We can try and solve this once you list it.


And how would I be able to pick out the errors?
Unless you mean I have to comb through every line in the error file.

---

### Post by john newbuntu on 2010-03-25
The tar command that you ran was something like:

tar bla bla bla .... > errors.txt

Now, after you run this command, anything that gets printed on the screen from the very next line (i.e, the stuff that does not go into the file errors.txt) are errors.  Please post these errors.

---

### Post by blueridgedog on 2010-03-25
Post the exact command you used, and attach the errors.txt file you created and I and others can look for the cause of the failure.

---

### Post by SCort5 on 2010-03-25
```
sudo su


cd /


tar cvpzf mybackup.tgz / --exclude=/backup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp


Then:
echo $?

```I cannot post the errot.txt becasue it is 10.3 mb

Edit: I will try to separate the error.txt into a few different files

---

### Post by blueridgedog on 2010-03-26
You are doing this:

```
tar cvpzf mybackup.tgz / --exclude=/backup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp
```

I suggest you turn off verbosity and again exclude the file you are creating:

```
tar cpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp
```

It may be without the "v" switch, you can see what is happening.

---

### Post by SCort5 on 2010-03-26
So as soon as I used this code:

```
tar cpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp
```

I got these errors

```
tar: Removing leading `/' from member names
tar: /var/run/synaptic.socket: socket ignored
tar: /var/run/cups/cups.sock: socket ignored
tar: /var/run/atieventsd.socket: socket ignored
tar: /var/run/samba/winbindd_privileged/pipe: socket ignored
tar: /var/run/acpid.socket: socket ignored
tar: /var/run/avahi-daemon/socket: socket ignored
tar: /var/run/dbus/system_bus_socket: socket ignored
tar: Removing leading `/' from hard link targets
tar: /home/john/.gvfs: Cannot stat: Permission denied
tar: /dev/log: socket ignored
tar: Exiting with failure status due to previous errors

```

I think having the 'v' in there was the proper way...

---

### Post by john newbuntu on 2010-03-27
It appears that the problem lies with the following directory/filesystem:
tar: /home/john/.gvfs: Cannot stat: Permission denied

You can exclude that one directory and see if you get an error code of 0.

.gvfs, I believe is a mount point for some/all of FUSE and can be ignored for the most part when doing tar, rsync and such. Now try the command:

```
tar cvpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp --exclude=/home/john/.gvfs > output.txt
```

After you run this, run 
```
echo $?
```
and check that it is 0.
The other messages you get such as "socket ignored" and "removing leading /" can be ignored.

If you have more than one home directory, replace that last piece of code in your command with /home/*/.gvfs

---

### Post by SCort5 on 2010-03-27
So after using this:

```
tar cvpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp --exclude=/home/john/.gvfs > output.txt
```

I got something additional:

```
tar: /output.txt: file changed as we read it
```
I'm guessing that I would have to exclude 'output.txt' as well

After this code:
```
echo $?
```

I got '1' which I am assuming means I have only one error to deal with which is the 'output.txt'.

Should I go ahead and add:

```
--exclude=/output.txt
``` as well?

---

### Post by john newbuntu on 2010-03-27
right scort5.

---

### Post by SCort5 on 2010-03-27
Ok so I did that and typed 'echo $?' and the number came to zero.

I will use the 

```
tar cvpzf mybackup.tgz / --exclude=/mybackup.tgz --exclude=/mybackup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media --exclude=/tmp --exclude=/home/john/.gvfs --exclude=/output.txt
```No problems right?

Edit: Ok I think I got everything. mybackup is 10.7 gb which when I calculated is about the same amount as the filesystem.

Thanks everyone. Putting this as solved for now.

---

### Post by blueridgedog on 2010-03-28
> **SCort5 said:**
> S

I think having the 'v' in there was the proper way...

I am glad you made progress.  Removing the "v" allowed you to see the errors, as it prevents showing you all the files being backed up.

I think you have all the tools to make what you want work now.

---


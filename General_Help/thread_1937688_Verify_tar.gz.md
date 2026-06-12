---
title: "Verify tar.gz"
date: 2012-03-08
forum: General Help
---

### Post by sdsnyr94 on 2012-03-08
This should be a quick one - 

On our mail server, a script runs nightly to create a .tar file of a set of subfolders, and then copies that file to the local Dropbox folder to sync. This file is now getting to be over 40 Gb, and this is becoming an issue due to size limits and upload speeds.

Originally this backup was done to tape, and was a .tar.gz file... when I upgraded the server a while back we moved from the tape to dropbox. When I tested some of the backup files, the files seemed to be corrupted (I think I was receiving some unexpected EOF stuff)... and so I went back to just .tar files with better results.

Now, I want to go back to compressing the file, but I would like to add some sort of verification in the backup script so that I know immediately if the data is valid. From this link: [http://stackoverflow.com/questions/2001709/how-to-check-if-a-unix-tar-gz-file-is-a-valid-file-without-uncompressing](http://stackoverflow.com/questions/2001709/how-to-check-if-a-unix-tar-gz-file-is-a-valid-file-without-uncompressing)

> To test the tar file inside is not corrupt:

gunzip -c file.gz | tar tf file.tar.gz

As part of the backup you could probably just run the latter command and check the value of $? afterwards for a 0 (success) value. If either the tar or the gzip has an issue, $? will have a non zero value.

Can someone please advise me on how to properly do this. I understand the logic of it, just not sure of the proper code.

Thanks.

---

### Post by Lars Noodén on 2012-03-08
There are a couple of ways to test the file.

```

tar Ozxf file.tar.gz > /dev/null && echo OK || echo FAIL

```

Or

```

tar ztf file.tar.gz > /dev/null && echo OK || echo FAIL

```

I'm not sure of the ways that a tar ball can go bad, but in my test of a truncated file, both do the trick.

---

### Post by Lars Noodén on 2012-03-08
Just thinking about it a bit more, the examples above only test for the integrity of the file and not for the presence or absence of files.  Maybe it could be run through grep.  

```

tar ztf file.tar.gz | grep somefile > /dev/null && echo OK || echo FAIL

```

[egrep](http://manpages.ubuntu.com/manpages/oneiric/en/man1/egrep.1.html) could also be used to string together several choices with logical OR.

---

### Post by haqking on 2012-03-08
so is the corruption after the tar or after the copy ?

cant you md5 it ?

Or am i missing the point ?

cheers

---

### Post by sdsnyr94 on 2012-03-08
> **haqking said:**
> so is the corruption after the tar or after the copy ?

cant you md5 it ?

Or am i missing the point ?

cheers

It's been about 6 months or so since I switched to just a .tar file, and I do not have any of the corrupted files to use as an example. If I recall correctly, I believe the corruption occurred DURING the tar.gz creation.

The initial server and backup script was put in place by an employee who is no longer with the company, and nobody ever checked if the backups were valid... until I started checking before upgrading the server last summer. Part of the issue could have been that the backup was being created with the mail server online, where mailboxes were changing (mail coming in) while the backup script was running. At about the same time that I switched to just a .tar file I also added a line to the script to stop the mailserver during it's backup... so that may have fixed the corruption issue.

Regardless, my concern is to make sure I am never at a point where I need the restore from a backup just to find out it is corrupted.

---

### Post by sdsnyr94 on 2012-03-08
> **Lars Noodén said:**
> Just thinking about it a bit more, the examples above only test for the integrity of the file and not for the presence or absence of files.  Maybe it could be run through grep.  

```

tar ztf file.tar.gz | grep somefile > /dev/null && echo OK || echo FAIL

```

[egrep](http://manpages.ubuntu.com/manpages/oneiric/en/man1/egrep.1.html) could also be used to string together several choices with logical OR.

Sorry, I think you lost me here... in your example is "somefile" a file that I am comparing the tar.gz content to? For example, my backup script does create a txt file of the files that it backup up... would I be comparing the content of the .tar.gz to the txt?

---

### Post by Lars Noodén on 2012-03-08
> **sdsnyr94 said:**
> Sorry, I think you lost me here... in your example is "somefile" a file that I am comparing the tar.gz content to? For example, my backup script does create a txt file of the files that it backup up... would I be comparing the content of the .tar.gz to the txt?

"somefile" is the name of some arbitrary file that is going to end up inside the tarball.  So what [font=Courier New]ztf[/font] does is list the files in the tarball, adding grep checks for the presence of a specific file in that list.

---

### Post by Diametric on 2012-03-08
> **sdsnyr94 said:**
> It's been about 6 months or so since I switched to just a .tar file, and I do not have any of the corrupted files to use as an example. If I recall correctly, I believe the corruption occurred DURING the tar.gz creation.

The initial server and backup script was put in place by an employee who is no longer with the company, and nobody ever checked if the backups were valid... until I started checking before upgrading the server last summer. Part of the issue could have been that the backup was being created with the mail server online, where mailboxes were changing (mail coming in) while the backup script was running. At about the same time that I switched to just a .tar file I also added a line to the script to stop the mailserver during it's backup... so that may have fixed the corruption issue.

Regardless, my concern is to make sure I am never at a point where I need the restore from a backup just to find out it is corrupted.

This makes sense because if I recall there is a check in the tar process that verifies itself against original data - I need to double check this...

---

### Post by sdsnyr94 on 2012-03-08
> **Lars Noodén said:**
> "somefile" is the name of some arbitrary file that is going to end up inside the tarball.  So what [font=Courier New]ztf[/font] does is list the files in the tarball, adding grep checks for the presence of a specific file in that list.

OK, so using your example, if I did:

tar ztf test.tar.gz | grep testme.txt > /dev/null && echo OK || echo FAIL

I would then be checking if the "testme.txt" file exists in test.tar.gz? 

If this is correct, that may be hard to do with the number of files that are added/removed daily in the users email directories. Unless I can export a list of files (from the OS) to a txt file, then compare the content of the txt to the .tar.gz (like doing a diff between 2 files).

---

### Post by Lars Noodén on 2012-03-08
> **sdsnyr94 said:**
> 
I would then be checking if the "testme.txt" file exists in test.tar.gz? 


Yes.  It's not so good except for a spot check of one or two files.  It's not going to scale up.  

There's also the [--verify](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tar.1.html) (-W) option which might help.

---

### Post by sdsnyr94 on 2012-03-08
> **Lars Noodén said:**
> Yes.  It's not so good except for a spot check of one or two files.  It's not going to scale up.  

There's also the [--verify](http://manpages.ubuntu.com/manpages/oneiric/en/man1/tar.1.html) (-W) option which might help.

Of course I overlooked that entry because I was not expecting it to be -W... thanks for the heads up, that should do fine.

Using your initial examples to verify integrity of the file, along with -W in the creation of the file should suit my needs.

Thanks!

---

### Post by sdsnyr94 on 2012-03-08
Well, using the -W gives "tar: Cannot verify compressed archives"

So my backup will now look like this:

  ```

tar -cWvf filename.tar /dir1 /dir2 > Backup.txt

gzip filename.tar

tar Ozxf filename.tar.gz > /dev/null && echo OK || echo FAIL
```

Backup will take a little longer due to having to compress separately, but it should be ok.

Now I have 2 other questions (sorry),

 - what does tar do with -W if it fails verification? Does it just bomb out, or retry?
 - can I send the output of the 3rd line to append the Backup.txt file created in line 1. 
                 
Basically, I want line 1 to output a list of all files backed up to Backup.txt. Then I would like to echo "Integrity Check" and the "OK/Fail" result from line 3 as the last line in Backup.txt

---

### Post by Lars Noodén on 2012-03-09
I'm not sure what tar will do when it fails.  I expect that it would probably just stop and return a value other than 0.

I'm not sure what you mean to do with the third line but you can grab it like this:

```

*someprogram* | awk 'NR==3 { print $0 }'

```

---

### Post by sdsnyr94 on 2012-03-09
> **Lars Noodén said:**
> I'm not sure what tar will do when it fails.  I expect that it would probably just stop and return a value other than 0.

I'm not sure what you mean to do with the third line but you can grab it like this:

```

*someprogram* | awk 'NR==3 { print $0 }'

```

```
tar Ozxf filename.tar.gz > /dev/null && echo OK || echo FAIL
```
outputs an OK or a FAIL message when it checks the file. I want that output to go at the end of the file that is created in the first command (Backup.txt in my example above).

This way, when I view the txt file I see something like this:

dir1/file1
dir1/file2
dir1/file3
dir2/file1
dir2/file2

Integrity Check.... [OK/FAIL] (Based on output of the above command)

This way, I can view 1 file and see the files that were backed up, along with if the integrity check passed or failed.

Hope that clarifies it a little.

---

### Post by sdsnyr94 on 2012-03-09
Well, cheap and dirty way for me to get what I wanted:

```
echo "Integrity Check" >> Backup.txt| tar Ozxf Wood.tar.gz > /dev/null && echo OK >> Backup.txt || echo FAIL >> Backup.txt
```

I am sure there is a much better way, but this does the job.

---

### Post by sdsnyr94 on 2012-03-09
And to answer another question - 

When I added the -W to my backup script and the verify fails, the script hangs.

I came in this morning to a non-functioning mail server...the backup:

stops mailserver service
does backup w/Verify
starts mailserver service

the verify hung the script, so the service never got restarted... guess I'm not going that route! ](*,)

---


---
title: "tar is missing files"
date: 2009-12-26
forum: General Help
---

### Post by Kissack on 2009-12-26
Sorry, my mistake - origianl message here, was irrelevant due to my mistake in setting up script
-- 
Allan

---

### Post by dcstar on 2009-12-27
> **Kissack said:**
> This has me beat after hours, so it is a request for help.  I had a backup script under ubuntu 7.xx that backed up my home and a few config files.  Over the break I have built a 9.10 server with a view to swapping the boxes over. The script is not working, in that it is missing files.  I resorted to runnign it via putty as for example, for a test "tar -cvvf /tmp/test1.tgz /home/allan/" this shows all files scrolling up the screen (as far as I can tell at the speed it goes) but the tar file is incomplete. there are no error messages to be seen and I cannot see any obvious differences in the files it does backup and those it doesnt. in a directory it may do soem files but not others, and sometimes complete direcotories are missing.  The results a reproduceable so it is not random.  However copying a subset of the files somewhere else results in all being tar'd wheres as the files in the orignal locations were only partial tar'd !

I'm stuck.  Any pointers would be usefull

-- 
Allan

Send the tar screen output to a file and examine it at the end for any errors.

---

### Post by john newbuntu on 2009-12-27
After you run the tar command, always use "echo $?" to check the status. A non-zero value generally indicates failure of some sort.
I suspect that the problem you have is with a few file/directories having permission issues.  I am assuming that you have sufficient space in /tmp to hold the archive.

What you could try and do is to copy the entire /home/allan to /tmp and then tar it up to a file called newtarfile.tar.  Read the archive using "tar -tvf newtarfile.tar > out1".
Repeat the same using your original tar file and redirect the output to "out2".

You could then do "sdiff -s out1 out2" to determine what you are missing and then look at possible permission issues.
Also, use the 'z' option in tar to have files gzipped.  It leaves you with a smaller resultant file.

---

### Post by Kissack on 2009-12-27
Thanks. I'll try this later (off out visiting family now). I dont think it is a permissions issue, but clearly something is wrong  so I'll follow the steps and see whether it reveals anything  - it certainly is odd.

I'll report back.

-- 
Allan

---

### Post by Kissack on 2009-12-28
Ok,thanks again.  Mystery solved.

It turned out to be a problem with winRar on a Vista machine that I used to view the archive.  Although it didnt report an error when double clicking the tar withing the zip it was failing to read the archive correclty.  When I un-rar's it in stages to a directory it did eventually report an header error.

I donwloaded winzip and that was fine, all files were there.

So thanks for your help, it did get me there in the end, even if it was a windows platform problem and not ubuntu - I should have known better :-)

-- 
Allan

---


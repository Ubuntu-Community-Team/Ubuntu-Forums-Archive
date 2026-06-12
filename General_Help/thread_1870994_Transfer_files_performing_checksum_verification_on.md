---
title: "Transfer files performing checksum verification on destination"
date: 2011-10-28
forum: General Help
---

### Post by chopstickkk on 2011-10-28
Hi,

My problem is this.

I work in the film industry and moving away from film towards digital, I need to transfer files from one place to another more and more often. These files are usually large when they're video footage and sometimes I get handed the only copy of a shot that literally cost thousands!!!

So...

I'm looking for a program or a simple terminal set of instructions that will transfer files from a source to a destination and then perform a checksum verification on the destination, verifying it is the EXACT SAME as the source, and then send a log to a text file. I mostly use Macs but this needs to work with Linux also - plus you guys are cleverer so that's why I came here ;)

So far I have gotten this far using rsync (but I'm open to any program/terminal instruction) ...

Pass 1 - To copy the files
```
rsync -avv /source /destination ¦ tee /destination/textlog-pass_copy.txt
```Pass 2 - To verify the files
```
rsync -acvv /source /destination ¦ tee /destination/textlog-pass_verify.txt
```(I'm not sure if the ¦ tee is Mac specific but it seemed to work better than > as the info came to the terminal output aswell as the textfile)

So the idea is to use rsync to do a straight archival copy and then run rsync again to do a checksum copy. Since the material is already there from the 1st pass it should spit out ...UPTODATE suffixes for every file, thus, to my knowledge, verifying that the destination is bit perfect identical to the source.


Now...

1 - Am I acheiving my goal here or am I way off!?!?!
2 - Is there a faster way that would also be a verified bit perfect replica?
3 - Is there a simpler way!?


Thanks in advance guys, I've not posted much here but this forum's saved me on more than a few occasions!

John.

---

### Post by gsmanners on 2011-10-28
My files aren't worth thousands of dollars, but I sometimes use par2 just to make sure my files won't go poof in some small way. The cool thing about par2 is that it can do the double-duty of verification and repair (if the damage is less than your redundancy you decided on when you made the archive).

I don't think whether this or that method is faster or simpler would even cross my mind in such an operation. It's your job, right? So, as they say, well done is quickly done.

---

### Post by quadproc on 2011-10-28
> **chopstickkk said:**
> 
I'm looking for a program or a simple terminal set of instructions that will transfer files from a source to a destination and then perform a checksum verification on the destination, verifying it is the EXACT SAME as the source, and then send a log to a text file. I mostly use Macs but this needs to work with Linux also - plus you guys are cleverer so that's why I came here ;)

I think that md5sum will do what you want if you use it as part of a small script.  The md5sum program reads a file and converts it into a hash which is effectively unique to that file.  So if you md5sum your original file and your copy then the two md5sums should be identical; if there is even a single bit of difference between the files then the md5sums will not match.

To read more about it, try
```
man md5sum
```To try it out, try
```
md5sum /etc/hostname
```or substitute your favorite testing file.

quadproc

---

### Post by quadproc on 2011-10-28
After thinking about this subject for a bit, I came up with a script that shows one way to do the task.

This script does not do error checking or handling.  The script does not handle all possible exceptions so it would be wise to flesh it out by adding such logic as is appropriate to your environment.

You will need to add suitable logic for obtaining the appropriate path names and file names; I just used "file1" and "file2" for my test case.  You can substitute your own code.  You will need to decide where a log file(s) should be located and you will need to either back them up and truncate them, throw them away, or append to them when you perform each copying/checking session.

```
#!/bin/bash

## set up the source file(s) to be checked with a loop, case, or similar statement here;
## replace the next two lines with your own code
source_f="file1"
dest_f="file2"
##

## for each file, do the following:
x1=`md5sum $source_f`
x2=`md5sum $dest_f`
a1=( $x1 )
a2=( $x2 )
sum1=$a1[0]
sum2=$a2[0]
if [ $sum1 = $sum2 ]
 then printf "same\n" # make an entry in the "OK copies" log
 else printf "diff\n" # make an entry in the "bad copies" log
fi
##

## if you need to then clean up, close files, change directories, etc.
exit 0

```quadproc

---


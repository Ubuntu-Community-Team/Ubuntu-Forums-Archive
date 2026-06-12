---
title: "Make a list of files on a disk"
date: 2010-07-18
forum: General Help
---

### Post by tuxerman on 2010-07-18
I have a 320GB external HDD which I use to take the load off my crammed-and-begging-for-mercy primary hard disk. It developed some strange problem once and refused to mount, and refused to get detected even in the BIOS. Fortunately the warranty got me a shiny new one.
Now, my issue is, I have a lot of files on it which I have downloaded off the net during my unlimited-usage time everyday. Suppose i lose all data again, I can easily obtain those files back again, IF i knew what all was actually there.  

So is there some way by which I can make a list of the files that are in each dir of the disk, in some human-readable format, so that I have my neat little index of my HDD?

---

### Post by ankspo71 on 2010-07-18
Hi,
If all you need is a simple list, then the ls command with the recursive option should work nicely.

Here is an example:
```
ls -R /media/sdb1 > myfiles.txt
```
The above command will recursively list the contents of my sdb1 partition, then save the results to a file called myfiles.txt in my home folder.
PS. It will list each directory's contents too
Hope that helps.

You can type the command "man ls" in the terminal to see more options, if necessary.

---

### Post by TechBeastie on 2010-07-18
Well, the output of these commands will be somewhat messy, but they're probably the fastest and simplest mechanisms for obtaining the kind of list you're looking for.  

Try either ```
 ls -alR [mount point of external disk, such as /media/disk] 
```
or
```
 du -a 
```

---

### Post by willjammn on 2010-07-18
The bash program called tree might be what you are looking for.

---

### Post by tuxerman on 2010-07-18
Yes, though all the options work nicely, tree does the job quite handsomely :) Plus, it's easy to set the depth of the tree, so I can have the output piped to different files depending upon the depth I require. Thanks :)

---


---
title: "rm -r accident"
date: 2010-04-22
forum: General Help
---

### Post by bingcrosby on 2010-04-22
Hey guys,

This is my first post!  Congratulations on such a great forum!

A while back, I accidently commanded:

\media\MyPassport\ rm -r

Obviously, about after 1 sec I killed the job.

Luckily, I haven't written to the drive and can use testdisk to copy those deleted files back.

I am wondering if there is any particular order to which rm -r deletes so I know which files and folders I have to backup.  For instance, I don't know if files inside subdirectories could have been damaged, although Testdisk doesn't list the folder as gone.  Some files and folders are listed as deleted in subdirectories, although I am not sure if I did those myself prior to rm -ring the whole drive. 

For instance, testdisk generates a list starting that starts with deleted files and directories, then normal folders (which contain deleted files and folders but I could have intentionally done this in the past perhaps), and then more deleted things and more normal things.

So does rm -r just delete the "tag" or "link" to the file and folder, so can I assume that if the original folder is not deleted, everything under it is the same as before I issued that idiotic command?  In addition, does rm -r delete in order so I can assume anything else listed as deleted after that initial list of deletes was done intentionally be myself in the past?

Is there any advice for this situation or a better, more efficient, data retrieval method?

Thanks and kind regards,

Peter.

---

### Post by iponeverything on 2010-04-22
```
\media\MyPassport\ rm -r
```

This won't do anything.


"\media\MyPassport\ " with a space after it, will just wait and "rm -r" is an incomplete command.

Word to the wise, use the -i flag for rm until you are sure its going to delete the correct stuff.

---

### Post by Dayofswords on 2010-04-22
also, the slash is going the wrong way =p

---

### Post by iponeverything on 2010-04-22
If you are just mixed up about the syntax of command and did in fact to a recursive delete, I don't think testdisk restores the files based on the deletion order, but rather by their location on the physical device.

---

### Post by bingcrosby on 2010-04-22
Sorry guys, I mistyped the command.

$ cd media
$ rm -r MyPassport

Sorry, I haven't been in the terminal that much lately (probably a good idea).

If I got it wrong again I can say I absolutely issued this command to the whole drive.

---

### Post by bingcrosby on 2010-04-22
Testdisk gives you a list of all files and folders in the directory.  The deleted ones are in red and the ones currently still visible in the terminal or GUI in white.

I am not sure how testdisk orders them, nor am I sure about what order rm -r works in.  I did accidently write a new file to the drive, and looking the drive up on testdisk again, the first listing which had previously been a red deleted file, was now taken up by a new file in white.

---

### Post by iponeverything on 2010-04-22
> 
So does rm -r just delete the "tag" or "link" to the file and folder, so can I assume that if the original folder is not deleted, everything under it is the same as before I issued that idiotic command? In addition, does rm -r delete in order so I can assume anything else listed as deleted after that initial list of deletes was done intentionally be myself in the past?


To answer your some of your questions, it depends on the type of filesystem. ext3 zero's the inode and ext2 just marks it as deleted leaving the pointers alone.

[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

---

### Post by bingcrosby on 2010-04-22
@iponeverything Thanks for the link, but I don't understand what it's talking about exactly.  Inode?

But I can tell you the external drive is FAT32 formatted.

---

### Post by iponeverything on 2010-04-22
> **bingcrosby said:**
> @iponeverything Thanks for the link, but I don't understand what it's talking about exactly.  Inode?

But I can tell you the external drive is FAT32 formatted.

I don't think that you can just undelete the directory and still have the files in it. I am pretty sure that a recursive delete first enters the directory and removes the files and then removes the directory.

---

### Post by Grenage on 2010-04-22
It's because of easy mistakes, I always specify the full path when using *rm*.

---

### Post by bingcrosby on 2010-04-22
What order would the recursive delete go in?  Is that the same order as what testdisk displays?

For example, if testdisk displays a list like,

[COLOR=Red]asdf.txt
asdf.doc
asdf.flac
asdf.pic
asdf(directory)[/COLOR]
ghjkl1(directory)
ghjkl2(directory)
[COLOR=Red]asdf(directory)
ghjkl.doc[/COLOR]
ghjkl3.pic

I need to undelete, asdf.txt, asdf.doc, asdf.flac, asdf.pic, asdf(directory) and POSSIBLY anything in ghjkl1(directory).  ghjkl2(directory) and ghjkl3.pic would be fine and I previously deleted asdf(directory) and ghjkl.doc NOT the recursive delete.

---

### Post by bingcrosby on 2010-04-22
If someone has an alternate solution to testdisk, that would be helpful as well.

---

### Post by Serpher on 2010-04-22
Did you check if any of the files were deleted? Unless you used the 'f' option as well in your command, it will constantly ask you if you want to delete each file looking like this:

Would you like to delete regular file abc? [y/n]:

---

### Post by bingcrosby on 2010-04-22
Yes files were deleted from the USB drive.

The message:
Would you like to delete ...

did not come up.

---


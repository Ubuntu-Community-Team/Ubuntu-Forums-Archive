---
title: "Consolidate folder contents into one 'virtual' folder"
date: 2009-07-04
forum: General Help
---

### Post by Ndyanabo on 2009-07-04
Suppose I have folders A, B, C, etc. Each have thousands of sub-directories and files. I want to create one big virtual folder, in which I consolidate the contents of A, B, C, without actually moving the contents from their original location. 

I suppose there would be some way to do this with an indexer (which one to use?, I currently don't use one), but I'm worried that it might be kinda slow, since there will be over 7,000 sub-directories.

I'd also like programs to be able to look in it exactly as if its a real folder. I don't know if that would work with an indexer, or if some sort of script could be written.

should be doable, right?

---

### Post by michy99 on 2009-07-04
I am not sure exactly what you are trying to do here, but I have a question. What if folder A and folder B each have a file (or folder) with the same name? Won't this cause a major problem with consolidation?

---

### Post by Ndyanabo on 2009-07-04
yeah, that's a potential problem. I guess the size of the problem depends on the specific solution.

---

### Post by lovinglinux on 2009-07-04
What you want can be achieved with [Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link) (aka symlink) [wikipedia.org].

You can rename a symlink to whatever you want. So you can have a symlink on your desktop named **~/Desktop/Virtual** that actually points to **~/Pictures**. Then whenever you save a file to **~/Desktop/Virtual** it will be physically saved into **~/Pictures**.

You can create a symlink with nautilus or via command:

```
ln -s ~/Pictures ~/Desktop
```

This will create a symlink in the **~/Desktop** folder pointing to **~/Pictures**. The resulting "folder" inside **~/Desktop** will be named **Pictures**, but you can rename it.

You can also put symlinks inside other symlinks ;)




*UKeywords: 649167 2009 july symlink*

---

### Post by michy99 on 2009-07-04
But does this answer the OP's question about 'consolidating' the folders? (I'm still not sure exactly what he means by that.)

---

### Post by lovinglinux on 2009-07-04
> **michy99 said:**
> But does this answer the OP's question about 'consolidating' the folders? (I'm still not sure exactly what he means by that.)

That's true.

He could use a command to list the content of the the folders he want to consolidate, then pipe the results through a symlink creation command. The only problem I see is that he would have to generate the symlinks with sequential numbers or something else to avoid conflicting symlink names.

---

### Post by Ndyanabo on 2009-07-04
> **lovinglinux said:**
> What you want can be achieved with [Symbolic_link](http://en.wikipedia.org/wiki/Symbolic_link) (aka symlink) [wikipedia.org].



sounds promising, but I'm not sure if we're talking about exactly the same thing. Can I create a single symbolic link to several folders? In your example, what if I had ~/Pictures1, ~/Pictures2, ~/Pictures3, etc. Can I link all of the them to ~/desktop/Virtual, so that when I open ~/desktop/Virtual, I see the contents of Pictures1, Pictures2, Pictures3, as if they were consolidated in that one directory (i.e. ~/desktop/Virtual)?

is that clearer, michy99? I'm trying to virtually consolidate the contents of various directories. 

Its a common problem: related files all over different locations in your file system. You want to have a place where you can see all the stuff, as if it were in one file folder. Often an indexing program can help with this, but I'm wondering if theres some other way to set up the linkage.

thanks!

---

### Post by michy99 on 2009-07-04
That's what I thought you were trying to do, but I don't know any easy way to do it.

---

### Post by lovinglinux on 2009-07-04
> **Ndyanabo said:**
> Can I create a single symbolic link to several folders?

I don't think so.

---

### Post by KeyserSoze93 on 2009-07-04
Try lndir

```
man lndir
```

---

### Post by Ndyanabo on 2009-07-04
> **KeyserSoze93 said:**
> Try lndir

lndir looks cool, but again, not really what I had in mind. That one makes a directory of symbolic links to the contents of another single directory. I guess what I'd need is a directory of symbolic links to multiple directories.

But can't I do what I'm talking about with an indexing program? Just save a search for * in the contents of folders I want? Which indexing program is good? I found Tracker to be very buggy in older versions. Beagle?

---


---
title: "question on conditionals"
date: 2012-04-15
forum: General Help
---

### Post by BigBennyC on 2012-04-15
Hello everyone, and thanks in advance for reading this.  I'm running a script that takes an image file called *.cub, runs some good processing on it, and creates a new file called *.trimmed.cub with the same base name.  This new file with the new extension exists through the processing, not just at completion.  The script is set up to do this process through all the files in a directory with a foreach loop (foreach i *.cub).  It's a lengthy process and I have a lot of images, so I'm thinking about making a few copies of the script and running them all at the same time.  Would this be a problem?  If not, I'd like to set up some sort of conditional that will skip *.cub files which already have a *.trimmed.cub equivalent, so the same image is not processed twice.  What would this look like?  Can I sneak it into the foreach statement?  Thanks!

---

### Post by callmemahavir on 2012-04-15
I have understood that *.cub converted *.trimmed.cub by some script.

I suggest running the script one by one for each *.cub is most correct one.

If more script runs at same time it may lead to consuming more resources in system.

And also you may not know how many *.cub files are there.

Also there is no much difference between the two (running one or many scripts).

---

### Post by BigBennyC on 2012-04-15
Yes, I'm sure I didn't explain too well!  The script converts files one at a time, but a single file takes over an hour, and I have about 200 files.  So, I want to run multiple copies of the script to process multiple images at once.  I think a few examples might be better.

For example, for the script to process p01.cub, p01.trimmed.cub must not exist.  If it does exist, skip to p02.cub, and check for p02.trimmed.cub, and so on.  I do not know how to say *.trimmed.cub does not exist.

What I more or less want is this:
foreach i (*.cub, such that *.trimmed.cub does not exist)
    run processing...

or

foreach i (*.cub)
     set base=`**basename** $i .cub`
     if $i.trimmed.cub does not exist
          run processing...

---

### Post by callmemahavir on 2012-04-15
Please understood this...

Both running single script and multiple script is not much difference.
Because the single script takes complete resource of your system so performs well but multiple script takes very high resources and slow the process. 

If system resources are go low may crash the entire process (For multiple script).

What is script language you are using ?

Check the script language reference to know how to check the file exists or not.

---


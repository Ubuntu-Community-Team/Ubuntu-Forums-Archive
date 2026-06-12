---
title: "Bash script - not duplicate files"
date: 2010-09-01
forum: General Help
---

### Post by StuartN on 2010-09-01
I am working through a collection of many thousand photographs in many collections, spanning decades. One of the folders is a "Selected_images" folder which should only contain copies of images from the collections.

How can I check that the files in "Selected_images" are all indeed copies and have an identical counterpart somewhere in the collections hierarchy, not necessarily with the same name?

At present I am scanning the output of **fdupes -r collection**, which is tedious (although, in fact, no photographs should ever be duplicated except in "Selected_images").

---

### Post by Brandon Williams on 2010-09-02
fdupes is definitely the right tool for finding the duplicates when the filename could be different, although I would typically use 'fdupes -rn1' to get more relevant and parse-able results. What about it is making you want to move away from it?

The process I would use is to run fdupes to get a list of all duplicated files, saving it off to a file. Then I would loop over the list of files in Selected_images and use grep to verify that each one is in the duplicates list.

---

### Post by StuartN on 2010-09-03
> **Brandon Williams said:**
> What about it is making you want to move away from it?

The process I would use is to run fdupes to get a list of all duplicated files, saving it off to a file.

Thanks very much. I did much the same as you suggested, saving the output of fdupes in a file and then passing all the Selected_images filenames through grep to list all those which did not have a duplicate.

The biggest problem was identifying new / original files outside the image store that were not duplicated within the image store, i.e. where an individual has created or modified a file and not saved it in its correct folder. These new files have to be identified and either placed in the correct collection, or re-united with their original parent file.

In an ideal world, there would never be duplicates and all filenames would be unique. In the real world fdupes is a great help.

---

### Post by Wahlgren on 2011-04-10
Hi, new here and looking for a way to organize my duplicate images as well. I found this thread after searching.

I have allot of duplicate photos, in fact it is so many photos I have no way of sorting them out manually even if I know where the duplicates are located. I used gThumbs built in duplicate finder and it did a great work! But to organize from there was not an easy task and I have to go trough each picture one by one to sort out which one to save and which one to erase.

I know there are duplicates by different image sizes, because some of the original files have been edited in photoshop, but still show up as duplicates. If I want to sort out these duplicates that have a smaller size, what is the best way to do this?

I've found some bash scripts that automatically remove duplicates, but I want to move all duplicates with smaller size to its own folder before deleting them.

If anyone have a easy way to do this I am forever grateful to you!

Edit: > joakim@ubuntu:~$ fdupes -rnm --summarize Bilder/
16492 duplicate files (in 12496 sets), occupying 63609.9 megabytes :cry:

---

### Post by Wahlgren on 2011-04-14
Guess I better try make the script by my self. Will come back to this thread if I manage to create one.

Edit: Was to complicated to fix with the script so installed Picasa 3.8 instead and from there managed to organize photos by date and with Adobe Bridge I could search metadata and exif info for what pictures where created in Adobe Photoshop Lightroom. Had allot of pictures exported from Lightroom and got mixed up with the originals. So now about 50% of the photos are organized. Guess there was no good free tools for this on Linux, so had to rely on Windows/Wine for this work to be done.

---


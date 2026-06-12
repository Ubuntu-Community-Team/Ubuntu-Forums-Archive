---
title: "better duplicate file/directory weeding, script maybe?"
date: 2011-04-07
forum: General Help
---

### Post by LewRockwellFAN on 2011-04-07
Here is what I want a program or script to do:
1. Look for pairs of duplicate files, a la fslint
2. Upon finding a pair of duplicates, compare the directories that contain them.
3. If the directories, including all their subdirectories and files all the way down, are also duplicates, compare the directories that contain them, and so on all the way up to the highest directories that are identical.
4. Move on to the next duplicate pair not in a pair of directories already noted as duplicates, repeating the process until all duplicates have been found.
5. Then output some sort of report, again a la fslint (at least functionally - I don't care about the visual appearance as long as I can understand it) but not showing the numerous individual duplicate file pairs (or trios or n-os) that are part of some duplicate directory structure, but only the duplicate directories at the most inclusive (i.e, "higher", closer to /) level at which there is a match and NOT showing any subdirectories or files in those directories.  Individual file duplicates would be shown only if they were not part of some larger redundant structure. And then of course I could pick which to delete. I don't care about fancy options like replacing the duplicates with links.

I can visualize what I want very clearly but I am not confident I have described it effectively. It will be much easier to see for those who have used fslint, especially if they have used it on a large and very disorganized file structure with many levels of hierarchy.  But since it can be summarized by fairly simple rules I thought perhaps it might be scriptable. (Down, Spellchecker!) And if it seems likely to you that that is so, perhaps you could point me toward what commands I need to study or a good strategy for searching for them.

A halfway approach would be if I could get something like fslint to report on duplicate directories and only on directories. Especially if they could be sorted by the size of their total content (i.e., total amount of data in all files in all sub directories all the way down).

Better than nothing would be at least being able to sort the duplicate files found by directory. Then at least I'd have some reason to suspect a whole bunch of duplicates all found in "/media/copied from failing seagate/2010/stuff from john/weird subdirectory/" having duplicates all in "/miscellaneous/wtf is this/" might possibly justify checking if the whole directories were redundant rather than have to go through all the files. 

If I had to do this with the tools I already know about there would be an AI in synaptic that I can tell "R. 
Daneel, organise this mess for me, will ya?" before I finished.  I've looked at least briefly at a bunch of programs in this category and none of them seem to be any more sophisticated than fslint although they could have capabilities not mentioned in the descriptions. Any relevant thoughts would be appreciated.

---

### Post by LewRockwellFAN on 2011-04-22
Maybe I should start at top and work down instead. If I understand du correctly it is giving me the total size in bytes used by all files in a directory, including the files in its subdirectories, and sub-subdirectories, etc., not counting cluster slack. Any directories have contents with identical large sizes would be likely to be identical and could be further checked.  So if I:

cd /media
du > du-output.txt

I'll get a text file consisting of a line for each directory in all filesystems that media points to with first the total size of contents, followed by a tab character, followed by the complete pathname/filename. Please correct me if I'm wrong. So next I'd need to sort these lines by the value of the numbers at the beginning of each line and look for directories with identical total content size. I should be able to do that by loading the text file in OOOcalc but when I add a function in the third column to spot consecutive entries with identical sizes OOOcalc crashes when I paste the function into the whole column. Presumably that is a resource issue. I've been frustrated by OOOcalc almost-but-not-quite working before. Anyway, there is probably some more elegant way to sort it. If I have to use an alphabetical sort, I'd have to somehow pad the numerals with leading 0s to a uniform length.

I'd appreciate any thoughts anyone has to offer on this.

---


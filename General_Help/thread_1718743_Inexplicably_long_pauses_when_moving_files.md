---
title: "Inexplicably long pauses when moving files"
date: 2011-03-31
forum: General Help
---

### Post by bc9 on 2011-03-31
Hi,

I'm wondering what might be causing some VERY long delays when I move groups of files from one directory to another on the same drive. In the GUI, I simply multi(shift)select a few dozen items at once (a set of JPEGs previously downloaded from my camera) and drag them together from the source directory window (where I downloaded all the images from the memory card) into a new/empty folder/window specific to that group of images. Just routine sorting of files basically... 

Once I 'let go' ('dropping' the items into their destination) there's often a SURPRISINGLY long delay before I can do something else within the GUI... open another file, or rename an item, etc... This delay can take a few seconds to more than a minute (if moving a couple hundred files at once)... this 'wait' during such a routine 'housekeeping' task seems surprising to me. During these delays, I CAN open/use other programs such as System Monitor or a browser... it just seems that additional GUI/filesystem tasks must wait out the delay before proceeding. If I go ahead and try to do another filesystem task during the delay anyway, it gets buffered... the file won't open/next files don't get moved/etc... UNTIL the delay from the first operation is complete (updated item counts resulting from file moves aren't reflected in List View until the delay is finished too). 

According to System Monitor (see image attachment for screen cap during one of these delays...) one CPU is pegged (the "gvfsd-metadata" process, which I guess corresponds to the file/move) and the other 3 cores are relatively idle, and there's plenty of free RAM/no swap. I'd have thought such a delay wouldn't be an issue with Ubuntu/my PC... maybe I have something set up incorrectly? Other clues: intermittently, during these delays/file operations, the GUI shuts down all open windows (folders)... as if the delays/buffered tasks caused some sort of reset. The hard drive is internal SATA formatted regular Ext4 and the Ubuntu on my PC is the 32-bit version since I figured my Dell is too old (about 4-5 years) to justify the 64-bit version. Like most folks, there are LOTS of files/folders on my drives, but I only have 3 file windows open at once most of the time, and am only displaying the item names and 'sizes'... no other columns. Nothing other than the 'move' itself is running at the time which could help explain the delay.

Any advice on how to do away with this delay would be appreciated... though I'm fairly new to Ubuntu/Linux I'm assuming it's not simply a matter of horsepower since what I'm doing seems like routine/easy housekeeping tasks. Thanks in advance for any help! :)

---

### Post by bc9 on 2011-04-09
Having received no responses, I spoke with a friend of a friend who's a longtime Linux guy and he suggested deleting a directory using this command: 

rm -rf ~/.local/share/gvfs-metadata

...whether the files inside get corrupted over time, or just overlong, I have no idea. Deleting it (it gets automatically recreated later) did seem to alleviate the worst of the delays, so I'd recommend trying that if you have a similar problem. Turns out that there's a thread here which discusses this in more detail (though I'm unsure whether my slowdown had the same cause, as I've never run out of disk space like some other users):

[http://ubuntuforums.org/showthread.php?t=1421580](http://ubuntuforums.org/showthread.php?t=1421580)

...unless I learn otherwise, I assume it'll be necessary to repeat this process in the future unless whatever causes it is corrected in a future Ubuntu release. 

Hope this post might help others down the road.

[I]Added May 26, 2011: it was already necessary to delete the gvfs-metadata file again.
And again on June 9, 2011. I do a lot of file moving/housekeeping stuff, but having to do this so often seems a bit ridiculous. Before today's deletion, this is what was in the ~/.local/share/gvfs-metadata directory:[/I]

-rw------- 1     9172 2011-06-09 12:46 home
-rw-r--r-- 1    32768 2011-06-09 12:46 home-2d81f774.log
-rw------- 1      208 2011-05-28 11:16 trash:
-rw-r--r-- 1    32768 2011-05-28 11:16 trash:-a840fb59.log
-rw------- 1  4402312 2011-06-09 12:50 uuid-d1207e22-8137-4324-b25a-29f323109058
-rw-r--r-- 1    32768 2011-06-09 12:50 uuid-d1207e22-8137-4324-b25a-29f323109058-a5a6c729.log

*...whatever the reason is for these long delays, and whatever the reason why deleting that directory and its contents helps (for a little while at least) I don't know. Whatever the reasons, the fact that moving files ONLY USES A SINGLE CPU doesn't help. (file moves on the same drive involve very little actual I/O... the files aren't really being moved: their paths are simply being updated to reflect their new locations in the file hierarchy). Being able to have all four cores work on the move would improve this problem considerably I suspect. *

---


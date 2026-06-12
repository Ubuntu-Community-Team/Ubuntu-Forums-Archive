---
title: "Nautilus Limitations"
date: 2010-10-29
forum: General Help
---

### Post by dirtyHANS on 2010-10-29
Nautilus - limitations?
 I do most of my work in file mgmt., from sorting new movies,msic,and pics, 
literally 10,000's of files of genre,type, and collections, all activated in place by selection
through the chosen file mgr.  - although i may enque music into a player, i never save playlists;
rather i select drag & drop, or right click choose enque. This particular option, i have found, comes only 
through a program called SMplayer, a front end for the Gnome Mplayer.
 Back when i was still a Windows user (shudder) i used a great little app called
Exprint - choose any folder, anywhere, and choose output of that folder's contents;
-where is this function under linux? - and then i right clicked a folder, and chose properties - 
- and what happened? well, it appeared to scan that folder, giving me the number of files,
 they're combined size, and the free space on that device.
- i reasoned, where is this data? can i somehow make a script, to gather directory contents, and make text file, for saving, or priintout
like, a list of all my movies? - can anyone help? please?

---

### Post by trikster_x on 2010-10-30
> -where is this function under linux? 

Are you talking about being able to print out a directory view to paper?  Not really understanding what you want to do.

> i reasoned, where is this data?

Well, it is the data polled from every file in the selected directory and any subdirectories, so it will be contained within those files.  That is why larger directories can sometimes take a few seconds to fully calculate the size.

> can i somehow make a script, to gather directory contents, and make text file, for saving, or priintout
like, a list of all my movies?

try this page:  [http://www.simplehelp.net/2009/04/08/how-to-save-the-output-of-a-linux-command-to-a-file/]("http://www.simplehelp.net/2009/04/08/how-to-save-the-output-of-a-linux-command-to-a-file/").  With the proper modifications to the "ls" command or "find" command, you can pretty much pull any info from any directory you want.

You would be surprised what the command line is capable of in a linux environment.  I would suggest you read up a bit on the "find" and "ls" commands.  You might find them enlightening.

---


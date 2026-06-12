---
title: "Playing an audio file"
date: 2011-11-12
forum: General Help
---

### Post by ki4jgt on 2011-11-12
I have a program which needs a command to issue to the system to play an audio file. I've tried totem, but the problem is I can't continue using the software until I switch windows and close totem. Is there a command I can give the program to allow it to play audio files without requiring and entire GUI?

---

### Post by Rodney9 on 2011-11-12
> **ki4jgt said:**
> I have a program which needs a command to issue to the system to play an audio file. I've tried totem, but the problem is I can't continue using the software until I switch windows and close totem. Is there a command I can give the program to allow it to play audio files without requiring and entire GUI?

I'm not too sure what you mean but there is a program in Synaptic clled MOCP and it runs from the commmand line 

From their website - [http://moc.daper.net/](http://moc.daper.net/)
What is MOC?
MOC (music on console) is a console audio player for LINUX/UNIX designed to be powerful and easy to use.

You just need to select a file from some directory using the menu similar to Midnight Commander, and MOC will start playing all files in this directory beginning from the chosen file. There is no need to create play lists like in other players.

If you want to combine some files from one or few directories on one play list, you can do this. The play list will be remembered between runs or you can save it as an m3u file to load it whenever you want.

Need the console where MOC is running for more important things? Need to close the X terminal emulator? You don't have to stop playing - just press q and the interface will be detached leaving the server running. You can attach it later, or you can attach one interface in the console, and another in the X terminal emulator, no need to switch just to play another file.

MOC plays smoothly, regardless of system or I/O load because it uses the output buffer in a separate thread. It doesn't cause gaps between files, because the next file to be played is precached while playing the current file.

Internet stream (Icecast, Shoutcast) are supported.

Key mapping can be fully customized.


Rodney

---

### Post by Sunil S Tantry on 2011-11-12
Suppose if you want to play mp3 files,you can do so by first installing mpg123 package using the command:

**sudo apt-get install mpg123**

And then use the following command to play the file:

**mpg123 filename**

---

### Post by ki4jgt on 2011-11-12
> **Sunil S Tantry said:**
> Suppose if you want to play mp3 files,you can do so by first installing mpg123 package using the command:

**sudo apt-get install mpg123**

And then use the following command to play the file:

**mpg123 filename**

That's what I was wanting. Thanks.

---


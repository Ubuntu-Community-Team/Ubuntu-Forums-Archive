---
title: "Searching Files &amp; Sharing Files"
date: 2011-04-06
forum: General Help
---

### Post by Nasair on 2011-04-06
Hello,
I've made a switch from Ubuntu 10.10 to xubuntu 10.10 for speed reasons, and through more research and experiments, I found I could have achieved most but not everything I wanted in Ubuntu without needing to switch...anyways, my questions:

1. I've been through about a dozen different applications that let me search for files on my hard drive, but I've yet to find one that can do what the default windows search in XP can do. I wan to be able to search a drive/folder select all the found files (or just a few) and pull/move those files to another location. It doesn't have to be drag and drop but some ability would be nice. I know with the gnome search I can copy them to a new location but I just want to be able to find my files and move them. I have a lot of music in different folders and I'd like to just move them to one folder. Any help would be awesome.

2. In Ubuntu it is really easy to share a file. In xubuntu it is, well not as straight forward. I looked around and decided the only easy solution would be to use Samba. My question is am I missing something, or is Samba my best bet? I want to share files to multiple OSs and some not Linux.

And sorry but I wasn't sure if this should be under "Desktop Environments"

Thank you,
Nasair

---

### Post by 3Miro on 2011-04-06
1. I don't know about find graphical program, but it should be pretty easy to write a script to move your files around. You can probably make a simple one line command. Like this:

```
find /home/my_username -iname '*.mp3'
```
this will list all your .mp3 files. You can then copy them to a folder:
```
cp `find /home/my_username -iname '*.mp3'` /home/my_username/Music
```
You can use mv for move in place of cp. This command will have some trouble if the names of the songs have spaces, but otherwise it will work. This is more complicated than windows, but with a simple scripting like that you can do really a lot of stuff.

BTW the program that you are looking for may exist, it is just the I don't know about it as I don't use such things.

2. Windows 7 can read NFS, you have to install something, but it is easy. I prefer NFS to Samba big time.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

[http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/](http://sagehacks.wordpress.com/2009/01/21/howto-mount-nfs-shares-under-windows-7/)

If you setup shares under Ubuntu, you are using Samba. If you want, you can install Nautilus from under XFCE and it should let you setup shares in just the same way.

---

### Post by Nasair on 2011-04-06
[3Miro]("http://ubuntuforums.org/member.php?u=777773"), Thank you for the reply...

For 1, I do have spaces in the names and the reason I wanted a graphical option was because not all of the files I want to move. Some files have names that don't make sense and I need to go through and rename them according to what folder they are in. I can move the files that already have names that are correct, but to restate some files are like "1231231231.mp3" in Folder Linkin Park/Hybrid Theory, so I need to rename these before I can move them.

For 2, Sweet, so I can install Nautilus and then use the Nautilus share that way!? I'm only worried it will slow things down, but I can test this. Can XP read NFS? I mostly have pre-Vista Windows Machines.

Thank you again!

---

### Post by 3Miro on 2011-04-07
> **Nasair said:**
> [3Miro]("http://ubuntuforums.org/member.php?u=777773"), Thank you for the reply...

For 1, I do have spaces in the names and the reason I wanted a graphical option was because not all of the files I want to move. Some files have names that don't make sense and I need to go through and rename them according to what folder they are in. I can move the files that already have names that are correct, but to restate some files are like "1231231231.mp3" in Folder Linkin Park/Hybrid Theory, so I need to rename these before I can move them.

For 2, Sweet, so I can install Nautilus and then use the Nautilus share that way!? I'm only worried it will slow things down, but I can test this. Can XP read NFS? I mostly have pre-Vista Windows Machines.

Thank you again!

1. You can try some of the less popular file managers like Krusader. They may have graphical search options.

2. You should be able to setup Samba shares from Thunar, but if it doesn't work, you can also use Nautilus. Nautilus would be used only for setup, once you have the things working, you can close it. Samba doesn't require Nautilus to run.

AFIK NFS under XP is hard. Windows 7 has it "natively" with a regular addon from MS, XP probably requires software from somewhere else.

---

### Post by nothingspecial on 2011-04-07
If the songs have correct tags, puddletag or easytag will let you rename them based on the song title.

---

### Post by Nasair on 2011-04-07
1, I can use the tags to rename the songs but I still need a search that lets me "move" files and not copy. I think I tired Krusader, but I'll give it another try. I have tried several file managers. I just find it strange I seem to be the only person that wants/would use this type of feature :confused:

2, Okay, that makes sense. I got that one figured out.

---

### Post by nothingspecial on 2011-04-07
Just a thought, if these are all music files, guayadeque music player will do that for you.

---

### Post by Nasair on 2011-04-07
> **nothingspecial said:**
> Just a thought, if these are all music files, guayadeque music player will do that for you.

I still need a search to find files and move them. I have videos in a similar situation and pictures, but thank you for the suggestion. I usually use mp3tagger

---

### Post by nothingspecial on 2011-04-07
I meant that guayadeque will search and move the files for you.......not just tag them.......


....but sadly only music ones

---

### Post by Nasair on 2011-04-14
I think I might have come up with something while trying a different search on Google:
[http://ubuntuforums.org/showthread.php?t=1352611](http://ubuntuforums.org/showthread.php?t=1352611)

```
find . -name '*.avi' -exec cp '{}' /target/directory \;
``````
mv */*.avi /media/disk/videos
```This last one is a little more simple, and if you add more */*s you can go more directories deeper
```
mv */*/*/*.avi /media/disk/videos 
```etc...

I'll have to give this a try but it still would be nice to have a graphical way of doing this


Wow, I just realized the first reply in this thread gave me this answer but I dismissed it at the time because I was hell bent on a gui option...my bad.

---

### Post by mastablasta on 2011-04-14
NFS for WinXP - it requires additional software provided by MS.
[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)
 
Required programme download 
[http://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)

---

### Post by Nasair on 2011-05-16
> **mastablasta said:**
> NFS for WinXP - it requires additional software provided by MS.
[http://support.microsoft.com/kb/324055](http://support.microsoft.com/kb/324055)
 
Required programme download 
[http://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)

Does anyone know a way to get windows 7 to be able to read EXT4 drives from the browser without a program, as in just a driver. I looked at:
[http://www.acc.umu.se/~bosse/]("http://www.acc.umu.se/%7Ebosse/")

I haven't been finding a lot of results.

---


---
title: "Folder problems...complete Ubuntu newbie"
date: 2009-10-10
forum: General Help
---

### Post by djm227 on 2009-10-10
So I've been wanting to try out Linux for a while, but didn't know that you could install it on an existing windows computer until a few days ago.  That's exactly what I did, and the last few days I have just been trying to get used to the various functions, and trying to figure out how to do the basic things that I used to do on windows.  

While messing around with the creation and moving of folders and various files today, I ran into some trouble.  I'll explain exactly what happened:

I created two folders, one of which I put several useless files into.  I tried moving the one with the files into the empty one.  I was expecting the folder and its contents to disappear from the desktop and appear in the empty folder, like it does on windows.  Instead, the folder with the files did appear in the other folder, but it also remained on the desktop.  I thought maybe in linux you can't move folders, but they copy instead.  So I deleted the one on the desktop...but after doing that, the one that I moved into the folder disappeared as well.  That made me think that maybe I had created a link by accident.  So i restored the folder with the files, and then tried deleting the copy I had put into the new folder.  It disappeared, but the one on the desktop did not.  However, the one on the desktop could then not be opened.

I played with it for a while, and eventually I wound up with 1 file which is of "unknown" type, and it can not be deleted, opened, or even moved.  How did this happen, and how do I get rid off this annoying file?  Any help would be appreciated.  

Thanks a lot for the help.  So far I really like Ubuntu, but it doesn't seem to like me very much.  It's been 3 days and I've already managed to crash it, which I thought was impossible, and I've had tons of little problems like this folder one.  I'm not gonna give up though, I'm too sick of windows to do that.

---

### Post by delcypher on 2009-10-10
Hmm I'm not exactly sure what happened but it might be worth quickly discussing with you moving/copying/linking files in ubuntu.

Using keyboard combinations in ubuntu to do copying do different things in ubuntu comapared to windows.

With no keys pressed, the default is "move folder or file". When you drag the icon it will have an arrow next to it. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131502&stc=1&d=1255200137[/IMG]


If you hold CTRL whilst draging a file or folder this will do "copy folder or file", the icon should have a + symbol next to it
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131501&stc=1&d=1255200137[/IMG]

If you hold ALT whilst draging a file or folder a ? symbol will appear next to it and when you let go of mouse button a menu will pop asking what you want to do "Move Here ", "Copy Here", "Link Here" or "Cancel"
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131503&stc=1&d=1255200137[/IMG]

The nearest equivalent to shortcuts (in windows) are symbolic links (there is another type of link called a hard link but let's not get into that). They are quite different from windows shortcuts.

*symbolic links can be named anything (in windows the file must end in .lnk)
*symbolic links work better than windows shortcuts. E.g. if you try to open say a shortcut to a text file in windows, windows may try to open the link rather than the file the shortcut links to. In ubuntu the link will always be followed!

Links usually have an arrow next to them as show below.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131504&stc=1&d=1255200740[/IMG]

Without watching what you did I can't really tell what you actually did.

If you're willing to type in a few commands I can show you how to remove the file that doesn't seem to want to disappear.

Hope this helps a little.

---

### Post by djm227 on 2009-10-10
Thanks for the info.  It does seem pretty weird, since I wasn't holding any buttons down, just dragging the folder from one place to another.  Maybe it was a fluke, hopefully it won't happen again.  I do want to get this "unknown file" out of here though, so I would really appreciate some info on how to do that.

---

### Post by antony.s on 2009-10-10
Try...

Open terminal
cd Desktop/
sudo rm *thefilename*

---

### Post by delcypher on 2009-10-10
Ah... the command line (also refered to as the shell or terminal).

Although Ubuntu has a pretty nice interface , if you want to do powerful things then you will often need to go to the command line.

I could take you through how to remove it via the user interface but it's not guaranteed to work, where as with the command line, if you want something removed, IT WILL BE REMOVED!

BE WARNED! Pay great attention to what you type in the command line, you can render your computer inoperable if you type in something wrong.

Okay to this "file of the undead"... (I'll call it fotu.txt in my examples)

1. Find the the your file is in. You can do this by "right clicking" on it and selecting properties, there will be a bit that says ```
Location: /path/to/fotu.txt
```

2. Now start up gnome-terminal (Applications > Accessories > Terminal)

3. Type ```
cd "/path/to/"
``` to execute a command you need to press enter.
Where /path/to is the folder you found in step 1. The cd command stands for "change directory" this puts you into that directory. Make sure there is a space between cd and /path/to . Make sure you put quotes (") around the path too. The quotes are unnecessary if the path has no spaces or brackets in it, but if it does using quotes is the easiest way to sort it out.

4.You should now be in the correct directory, to check type
```
pwd
```
This stands for "path working directory", this tells you which directory you are in

5. Now that you're in the right directory run this command
```
ls -l
```
The ls program lists the contents of the current directory (it can list other directories if you tell it to). The -l is an option it tells ls to show everything in list view.

The output should look like something like this.
```
total 3192
-rw-r--r-- 1 dan dan 1843200 2009-10-08 23:16 01926_calaformentor_1680x1050.jpg
-rw-r--r-- 1 dan dan 1409024 2009-10-08 23:16 aletta_720.wmv
-rw-r--r-- 1 dan dan    2452 2009-10-08 23:16 brendan
drwxr-xr-x 2 dan dan    4096 2009-10-10 20:21 test dir

```

This tells you a huge amount of information, which you may need later

6. Now we will remove the file (fotu.txt). type in this command.
```
rm "fotu.txt"
```

7. If you get an error message please post the error message on this forum post as well as the output of the "ls -l" command (please put this in the code tags (# button on post editor on forum) so it is readable).

running the command "switch user do" ```
sudo rm "fotu.txt"
``` will almost certainly remove your "file of the undead" but it will be worth finding out why the normal rm command won't work.

Anyway that's a crash course in removing a file via the command line.
Let me know how you get on. If you'd like to learn more about using the command line then [http://lowfatlinux.com/]("http://lowfatlinux.com/") is a good place to start.

---


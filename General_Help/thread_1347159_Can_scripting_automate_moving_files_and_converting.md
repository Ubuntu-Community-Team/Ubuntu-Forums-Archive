---
title: "Can scripting automate moving files and converting?"
date: 2009-12-05
forum: General Help
---

### Post by slope on 2009-12-05
Is there a way to have a script or something that can manage my media folder for me?

I.e:
Today I have my media files all scattered around in one folder, with lots of sub folders without any real structure. As I add content this will shortly become impossible to manage. So now is the time to do something clever and put linux to work and automate the task.

**Is there a clever way to make moving files and converting some files all go on autopilot?**

i.e: certain file endings like .flac goes into a designated folder called lossless. MP4, mkv, avi etc goes into designated folder called movies. All files and sub folders of course. And also for the lossless folder I would like to have a duplicated folder except this folder is named MP3, and contains all sub folders and files from lossless but rather then flac format the files will be mp3@320kbits.

**So to sum it all up:**
1: Script need to be able to move folders, sub folders and files to designated folders based on file type. (Mkv, flac, mp4 etc)

2: Script needs to convert certain file types into other, img to iso, flac to mp3 etc.

3: Script must monitor folders so if new files are added to target folder the flacs are also added as mp3's to mp3 folder.

4: Also there will be times when there are need to unrar some files, and then first script can move files.

Btw, is there any limits to how many files or sub folders xubuntu can hold? I have years ago met this problem using windows, anything like that excist in linux?

---

### Post by Sin@Sin-Sacrifice on 2009-12-05
I doubt anyone is going to write the script for you but this is all possible. [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php) should be of some help. There are programs you can use like flac2mp3, mv, and crontab that can schedule and get this done for you.

---

### Post by amturnip on 2009-12-05
Have a look at the book, "Wicked Cool Shell Scripts".

And remember that Linux has both hard and soft links... no need to risk the welfare of your files when practicing a shell script to organize them.  Your script can simply create a new directory that is a nicely structured facade for your existing directories of media files.

---

### Post by slope on 2009-12-06
Thx guys. Course no one is to write the script :-)

First reason for posting here was to check if this at all is doable in linux. And so it seems :-)

What I then is after is a rough outline, maybe a script someone already put together or maybe links to sites that have this type of scripts.
If I have a script to start with I can make modifications along the way and hopefully in the end I have automated repetitive boring tasks as well as learned a lot along the way.

Btw, I have seen a flac to mp3 script somewhere but now I can not find back to it, so if you know what I am talking about let me know.

---

### Post by falconindy on 2009-12-06
This is **really** easy with inotify. Basically, you can create a "dropbox" directory wherein you can toss files you want sorted. The inotifywait program will run in the background and monitor the directory for file creation events. When it sees a file, it passes the file to the read program which passes it to a case statement which determines where the file goes. This should get you started:

```
#!/bin/bash

its-a-rar() {
       unrar ex "$1"
}

inotifywait -qm --event CREATE -format %f /path/to/dropbox | while read $file; do
        case "${file##*.}" in
           "flac")      mv "$file" /path/to/flac ;;
           "mp3")       mv "$file" /path/to/lame ;;
           "mkv")       mv "$file" /path/to/vid ;;
           "rar")       its-a-rar "$file" ;;
        esac
done
```
You will likely need the inotify-tools package (not sure if that comes installed by default). 

Edit: To answer your question about directory limits, ext4 has none.

---

### Post by slope on 2009-12-06
Thx man.
I will try out this right away.
I am on xubuntu 8.04 LTS and sadly can't take advantage of ext4, so I am using ext3. So I guess by the sound of it ext3 has some limits?

---

### Post by falconindy on 2009-12-06
> **slope said:**
> Thx man.
I will try out this right away.
I am on xubuntu 8.04 LTS and sadly can't take advantage of ext4, so I am using ext3. So I guess by the sound of it ext3 has some limits?
You've got a limit of ~32000 sub-directories per directory. Not sure if there's an absolute max directory limit.

---


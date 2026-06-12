---
title: "How to move music files from all subdirectories to parent directory"
date: 2010-03-01
forum: General Help
---

### Post by capleton on 2010-03-01
I've found several posts discussing how to do this in with the terminal, but none exactly fit what I am trying to do.  And since I'm still very new, I was hoping for some help.

I have a parent directory called "Music." The subdirectories all start with "artist", some go further as in "artist/album/cd1".  So right now the structure varies in the following ways:

music/artist"a"/song.flac
music/artist"b"/album"1"/song.mp3
music/artist"c"/album"2"/cd1/song.ogg

How can I move all the files (or the file types that I choose) to the parent directory "music"?

(By the way, for any who are interested, this is so that I can use an external hd with a PS3. ("playstation 3"--for anyone who was in my predicament searching the threads)

---

### Post by Danawar on 2010-03-01
Hey [capleton]("http://ubuntuforums.org/member.php?u=559656"), I'm not sure if this will work but perhaps it is worth giving it a try on a test folder.
```
 find /Music -name '*.mp3' -exec mv {} ~/Desktop/folder 
```Change the values to your requirements let me know if it goes ok.

-Dan

---

### Post by capleton on 2010-03-01
Thanks for the quick response Dan,

I don't quite understand everything the syntax is saying which may be why i can't get it to work.  Here's what happened:```
*****@N120:/media/disk-1/music2$ find /music -name '*.flac' mv {} /media/disk-1/music2
find: paths must precede expression: mv
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```
I bet it's got something to do with me being in the directory i'm trying to move the files into...

---

### Post by tgalati4 on 2010-03-01
[http://ubuntuforums.org/showthread.php?t=1385966&highlight=recursively+copy+files+parent+directory](http://ubuntuforums.org/showthread.php?t=1385966&highlight=recursively+copy+files+parent+directory)

I like the volcano.py script.  It blows all files from subdirectories up into the current directory.

Copy the volcano script into a file called volcano.py
Add executable privileges to it:

sudo chmod +x volcano.py

Make a copy of your music directory:

cp -R /Music /Joe_the_Volcano
cd Joe(tab)
./volcano.py

(Stand back.)

Let us know if it really works.

---

### Post by Jose Catre-Vandis on 2010-03-01
Try this, works for me:
CD to the top line folder and run this command:
> export IFS=$'\n';for i in $(find $1 -name "*.mp3" -type f);do cp "$i" /Music;done
Again change the filetype (*.mp3), the command (cp -> mv ?) and destination folder (/Music) to suit.


*Note: couldn't get Danawar's line to work, problem with missing argument for -exec (but not sure why?)*

---

### Post by blur xc on 2010-03-01
> **Danawar said:**
> Hey [capleton]("http://ubuntuforums.org/member.php?u=559656"), I'm not sure if this will work but perhaps it is worth giving it a try on a test folder.
```
 find /Music -name '*.mp3' -exec mv {} ~/Desktop/folder 
```Change the values to your requirements let me know if it goes ok.

-Dan

Maybe it should be-
```
 find **~**/Music -name '*.mp3' -exec mv {} ~/Desktop/folder **\;**
```

Now that will only move files with mp3 extensions.  If there are other files in your subdirectories that also need moving, album art, whatever try -
```

find ~/Music -type f -exec mv {} ~/[destination folder] \;
```

Both those commands assume your music is in your /home/username/Music folder.  If it's somewhere else, you need to modify the command you will actually run.  In the first command, the -name option says to find all files that end in .mp3, then execute the mv command, taking the found file (the {} part, though sometimes I see it uses with single quotes around it like this '{}') and moving it to the specified directory.  I don't know why the command needs to end with a "**\;**"  It's just how I've seen it used, and doesn't work for me if I omit that part.  In the 2nd command, the "-type f" tells the command to find only files, since it wouldn't make sense to move directories.

The find command is very powerful and very useful.  

BM

---

### Post by sgosnell on 2010-03-01
The path is wrong here.  /music is not what you want.  If you're in the directory to be searched, use '.' for the current directory.  If the directory is below the one you're in, just use the name of the directory, without the '/'.  /anydirectory always means the directory 'anydirectory' under the root directory '/'.  From your home directory, you would use /media/disk-1/music2, if that's the one you want to search.  You can always use the full qualified directory path, from anywhere.

---

### Post by capleton on 2010-03-02
Thanks for all the help!  And it is solved 8-)

I used code from Danawar, blur xc, and sgosnell.   I went to the parent directory (the one i wanted to move all the files to and that had all the subdirectories in it) and ran

```

*****@N120:/media/disk-1/Music$ find . -name '*.mp3' -exec mv {} . \;
*****@N120:/media/disk-1/Music$ find . -name '*.mp4' -exec mv {} . \;
*****@N120:/media/disk-1/Music$ find . -name '*.wma' -exec mv {} . \;
*****@N120:/media/disk-1/Music$ find . -name '*.wav' -exec mv {} . \;

```
as those are all the file types the PS3 can play.  

Now it takes foreeeeever to open the music directory, but hey, at least now i can play music from it on the PS3.

Thanks again to everybody!

---


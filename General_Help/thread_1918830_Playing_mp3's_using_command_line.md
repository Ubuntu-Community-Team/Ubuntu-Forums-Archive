---
title: "Playing mp3's using command line"
date: 2012-02-01
forum: General Help
---

### Post by Wuxin on 2012-02-01
I want to know how to play mp3's on RhythmBox or SMPlayer using the command line rather than front end format.  Can this be done in Ubuntu?  I'm trying to get more comfortable using the command line and haven't figured out a way to play mp3's.  Any input on this would be greatly appreciated!

---

### Post by marshmallow1304 on 2012-02-01
```
mplayer file.mp3
```

You can also control a running instance of SMPlayer using something like
```
smplayer -send_action pause
```

---

### Post by Wuxin on 2012-02-01
Thanks for this!  Okay...just a few points of clarification.  In the first command, did you mean to put *smplayer* rather than *mplayer*?  smplayer is of course the Ubuntu version of mplayer, but I didn't know if perhaps the player would respond to both commands.  Where you wrote *file* is that where you would put the name of the song?  What if the song is within an album (or larger folder)...would you need to put the album name prior to the specific song?

In the second command, is the idea you write in *-send_action* and then the name of the function you want (e.g., pause, stop, repeat, etc.)?  Supposing you wanted to change songs in midstream--can that be done via command line?  (Do you not have to use the tilde (~) in any smplayer functions?  I think you do in mplayer.)  Thanks so much for your attention!

---

### Post by llamabr on 2012-02-01
I use mplayer, too.   Mplayer will play from a url streaming mp3.  Try this:

```
mplayer http://wnyc2.streamguys.com/wnyc2
```

There's also something called music123, which is a little script that will play your music files, and call diffferent programs depending on their filetype.  Neat.

---

### Post by Wuxin on 2012-02-01
I am confused...you'll have to take this more slowly, I'm a novice.  Do you mean that Ubuntu can use mplayer instead of smplayer?  My understanding was that smplayer is the version for Ubuntu.  What is this url streaming that you refer to?  Is that a way to play the recordings on my hard drive or is it a streaming source?  Is music123 and add on for mplayer or is it a separate program?  I'm interested...please explain more.  Thank you for your information!

---

### Post by Chronon on 2012-02-02
SMplayer is just a front end for Mplayer.

---

### Post by raja.genupula on 2012-02-02
Hi actually what he is trying to say is you can use mplayer for both command line mp3 play and as well as command line mp3 streaming . 

ok i got an tutorial for you which explains all the things you can do with mplayer 

[http://www.linuxtutorialblog.com/post/tutorial-playing-around-with-mplayer](http://www.linuxtutorialblog.com/post/tutorial-playing-around-with-mplayer)

I hope that can help you . 

All the best.

---

### Post by Khayyam on 2012-02-02
Wuxin ...

There are various command line players ([mpg321]("http://mpg321.sourceforge.net/"), [splay]("http://sourceforge.net/projects/splay/"), to name but two) which have (curses) interfaces and all kinds of features (playlists, stop/start/skip/pause commands, etc).

There is a patched version of cplay that uses mplayer as the backend, and has various features (naviagtion, playlists, stop/pause/play, equaliser, and more). Its just a small python script and can be downloaded [here]("http://www.argafal.de/cgi-bin/index.pl?page=projcplay&nolog=0").

Place it some place in you $PATH and run. By default you'll get a naviagtion window, but you can pass pass options/parameters to it if you so wish:

```
cplay --help
Usage: cplay [-nrRv] [ file | dir | playlist ] ...
```HTH ...

---

### Post by Wuxin on 2012-02-02
Thanks for all the info above!  Unfortunately I've tried the various commands mentioned,
but mplayer (or SMPlayer) does not recognize my mp3 files.  What could be the problem?  I have successfully downloaded the material (and it is in a music file) but mplayer apparently fails to recognize them.  Any suggestions??  Incidentally, the music plays fine
when using the front-end format.

---

### Post by visakh0474 on 2012-02-02
Try to play the music file using vlc mediaplayer.If vlc is not installed, install it using software centre or any other means.vlc can also be opened in command line.The command is written below.

       vlc file.mp3

---

### Post by Wuxin on 2012-02-02
I've tried this but still no music.  This is the response I get in the terminal:

Yuhan-ThinkPad-T43:~$ mplayer That Will be the Day
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

What could be missing here?

---

### Post by qyot27 on 2012-02-02
If there are spaces in the filename, there needs to be quotes around it (or a \ before every space).

mplayer Yada Yada Yada.mp3 = won't work
mplayer "Yada Yada Yada.mp3" = works
mplayer Yada\ Yada\ Yada.mp3 = works

---

### Post by Wuxin on 2012-02-02
Thank you for that!  Can you abbreviate a file name if it is a long title?  How can
you do that so that the file is recognized?  Thanks in advance.

---

### Post by Wuxin on 2012-02-02
Ah...frustrating!  This is what I got even with the quotes:

ThinkPad-T43:~$ mplayer "that will be the day.mp3"
MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing that will be the day.mp3.
File not found: 'that will be the day.mp3'
Failed to open that will be the day.mp3.


Exiting... (End of file)

What am I doing wrong here?  It would seem this should work.

---

### Post by Wuxin on 2012-02-04
I know that Ubuntu can play mp3 recordings because I can do it easily through the GUI format.  The problem is, and it remains a problem--why can't I get it to work through a command line?  My music files are all in a folder called "music" and, I would think, it should be easy enough to write a path from the player to the folder and to the particular song.  For some reason, the paths posted thus far haven't worked for me.  Any ideas??  Thanks!

---

### Post by howefield on 2012-02-04
> **Wuxin said:**
> What am I doing wrong here?  It would seem this should work.

It can't find the file you are referring to, you are either not giving the path to the file or mispelling it ?

Use the tab key to auto complete when typing out file names, helps reduce typos as well as being quicker.

---

### Post by Khayyam on 2012-02-04
> **Wuxin said:**
> [...]  My music files are all in a folder called "music" and, I would think, it should be easy enough to write a path from the player to the folder and to the particular song.  For some reason, the paths posted thus far haven't worked for me.  Any ideas??  Thanks!

Wuxin .. why not install cplay (or some similar curses based CLI interface) as per [my previous post](http://ubuntuforums.org/showpost.php?p=11658701&postcount=8). You can then navigate to "music/*" and play/pause/etc whole albums, or directories, recursively, without having to select each track from the command line.

HTH ...

---

### Post by qyot27 on 2012-02-04
> **Wuxin]Thank you for that! Can you abbreviate a file name if it is a long title? How can
you do that so that the file is recognized? Thanks in advance.[/quote]
No, but you can use tab auto-complete, as mentioned above, to speed things up.  Just start typing the title and then hit the tab button.  It'll allow you to cycle through any files that match the first few letters you typed.

[QUOTE=Wuxin said:**
> I know that Ubuntu can play mp3 recordings because I can do it easily through the GUI format.  The problem is, and it remains a problem--why can't I get it to work through a command line?  My music files are all in a folder called "music" and, I would think, it should be easy enough to write a path from the player to the folder and to the particular song.  For some reason, the paths posted thus far haven't worked for me.  Any ideas??  Thanks!
A) *nixen filenames are case-sensitive.  "That Will Be The Day.mp3" and "that will be the day.mp3", or any other variation of capitalization, will be treated as different files.

B) You need to navigate into the directory that contains the file you want to play, or use either an absolute or partially relative path:
mplayer /home/username/music/filename.mp3
mplayer music/filename.mp3

cd music
mplayer filename.mp3


You can also check whether you're in the right place by using ls to list the contents of the directory. ls can also take search patterns so that it can show only matching entries.

ls = lists the files in current directory
ls *.tar.gz = lists only files ending in .tar.gz
ls That* = lists all files starting with the word That (as mentioned before, it's case-sensitive)




One thing to do (if you use Nautilus as your file manager) would be to install nautilus-open-terminal, which will add an 'Open Terminal Here' option to the right-click menu.  You can use it to make sure you're in the same directory as the files you want to mess with.

---

### Post by Wuxin on 2012-02-05
Again thank you all for the constructive input.  It's good to know there are folks out there
who know more than I do and are generous with their knowledge.  Apparently, my system is unable to recognize my mp3 files.  I tried the suggestion of inserting <ls That*> and received the following:

ThinkPad-T43:~$ ls That*
ls: cannot access That*: No such file or directory

I don't know why, at least through a terminal, my system can't identify files that are clearly there!  If I open the music folder and point the cursor to the individual song files, it plays perfectly.  Yet when I attempt to do the same through the terminal (which is what I set out to do here), I can't get a response.  I've tried every configuration suggested here, but nothing seems to work.  I'm sure there is a way (and it's probably simple!), but I'm still unable to find it.  Thank you for any further ideas.

---

### Post by howefield on 2012-02-05
If the song plays through one of your GUI applications, it will play via the command line.

ls lists the content of the folder that you are in, so you would simply use ls on it's own (or with the name of the folder in full).

If you can use ls and you get a listing of the music files all you'll need to type is mplayer nameofsong.mp3 

Remember linux is case sensitive.

When you open a terminal chances are that you will be in your home folder., type 

```
cd Music
``` 

then do an ls, do you see the mp3 files or are they in another sub folder in which case you can drill down until ls gives you a listing of the files you want to play.

I have in my Music folder another called Hank Snow - Legendary-CD 3

To play all the songs in the folder I type the following after opening the terminal.

```
mplayer Music/Hank\ Snow-Legendary-Cd\ 3/*.mp3
```

The asterix is a wildcard so it plays all songs in the folder.

---

### Post by nothingspecial on 2012-02-05
To play your music collection randomly

```
mplayer -quiet -shuffle -playlist <(find ~/Music -type f)
```

In my bash_aliases file I have this line

```
alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f)'
```

So to play random music I just type

```
ran
```

---

### Post by 3rdalbum on 2012-02-05
Try this.

Type 'mplayer ' as you would normally, leaving a spacebar at the end. But instead of typing the file name, drag the file from your file browser window to the terminal.

It will put the full file path into the terminal so you can run it as a command and it will work.

With what you are currently doing, your terminal has not been navigated to the directory that contains the song, and you haven't specified that it's in a different directory. That's why you're getting "No file or directory".

---

### Post by Wuxin on 2012-02-05
Excelsior!  Howefield thanks for your find clarification!  Going the route of changing directory of "Music" and taking it from there worked like a charm.  Songs now play from the command line.  One point of clarification: my understanding was that in Linux the forward slash(/) is always used.  When is the backslash (\) used?  (Wasn't that the DOS
convention?)

3rdalbum I haven't yet tried your suggestion but I will!  I'm not exactly sure what I did
differently other than start with the Music directory.  It would seem that I should be able to mark a path from Home to Music and so on.  But thanks so much everyone for your help and expert knowledge.  Maybe someone knows a good book and/or website that gives an overall explanation of the Linux command line?

---

### Post by howefield on 2012-02-05
> **Wuxin said:**
> Excelsior!  Howefield thanks for your find clarification!  Going the route of changing directory of "Music" and taking it from there worked like a charm.  Songs now play from the command line.  One point of clarification: my understanding was that in Linux the forward slash(/) is always used.  When is the backslash (\) used?  (Wasn't that the DOS
convention?)

You're very welcome.

In this case, the back slash is used to "escape" the spaces in the file name, not to signal the filename or path. You can also wrap the filename in quotes for the same effect.

I noticed some articulate command line youtube tutorials at an introductory level, try these..

[http://www.youtube.com/watch?v=AO0jzD1hpXc](http://www.youtube.com/watch?v=AO0jzD1hpXc)

6 short videos, I think. Worth a look.

---

### Post by Wuxin on 2012-02-06
Howefield--this is a very fine tutorial!  The material is clearly explained and useful.  Based on what I saw there, it appears that the trouble I was having with getting mplayer to work within the terminal had to do with the "absolute" vs. "relative" directories.  Your suggestion pointed me in the direction of using the "relative" approach (i.e., <cd Music>) and that worked great.  Why is it, however, I'm having trouble getting mplayer to respond through the "absolute" directory?  It would seem both should work fine.  But thanks again for this reference--I look forward to watching all 6 parts!  (Would recommend this to others as well!)

---

### Post by howefield on 2012-02-06
For example, I have a track called 109-ann_lee_-_2_times.mp3 in my Music folder.

Using the terminal and from anywhere in the file structure the track can be played using an absolute path

```
mplayer /home/user/Music/109-ann_lee_-_2_times.mp3
```

or

```
~/Music/109-ann_lee_-_2_times.mp3
```

The tilda being a shortcut to your home folder.

---

### Post by Wuxin on 2012-02-06
I hate to keep writing in on this but there is still a problem.  Even copying the absolute paths clearly and identical to the format presented, mplayer doesn't recognize my folder
of mp3's.  Is there some way of storing mp3's that makes them more accessible or recognizable?  Once again, thanks--I appreciate the support on this.

---

### Post by Wuxin on 2012-02-07
Okay...this may be a complicating factor: Within my general directory "Music" I have sub-directories (e.g., "50s and 60s rock," "Miles Davis," etc.).  So how do I insert the sub-directories into the path (following "Music") and the the designated file within that sub-directory?  Thanks once more!

---

### Post by howefield on 2012-02-07
Just follow the path down to the mp3 tracks eg,

```
mplayer /home/user/Music/subfolder/subfolder/subfolder/109-ann_lee_-_2_times.mp3
```

or 

```
mplayer ~/Music/subfolder/subfolder/subfolder/109-ann_lee_-_2_times.mp3
```

Change "subfolder" to correspond with the actual names of your folders.

---

### Post by Wuxin on 2012-02-14
Thanks so much one and all for excellent help and support!  What fantastic resources we have on this site! Much obliged!

---


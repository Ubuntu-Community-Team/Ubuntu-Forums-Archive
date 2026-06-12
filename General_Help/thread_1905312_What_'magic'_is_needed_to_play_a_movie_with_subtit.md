---
title: "What 'magic' is needed to play a movie with subtitles (when srt files exist)?"
date: 2012-01-06
forum: General Help
---

### Post by rocksockdoc on 2012-01-06
I have an avi file and subtitle srt files but the movie won't show the  subtitles with the default Totem Movie Player 2.30.2 on Ubuntu and there is no menu (that I can find) in Totem to choose the subtitles (English, French, German, etc.) to play.

What 'magic' is needed to play a movie with subtitles?

Here is a directory listing of the available file structure:
./movie.avi <=== this is the movie 
./movie.idx
./movie.sub
./movie_srt/english.srt <=== these are apparently the subtitle files
./movie_srt/italian.srt  
./movie_srt/french.srt
./movie_srt/german.srt  

Is my movie player wrong or is my file structure wrong or do I need to make a setting somewhere that I haven't made to select the subtitles to show up in the playing of the movie?

---

### Post by pr3zident on 2012-01-06
try downloading VLC and then use your subtitles there i found it easier to use and do ...

---

### Post by philinux on 2012-01-06
> **pr3zident said:**
> try downloading VLC and then use your subtitles there i found it easier to use and do ...

+1 install VLC from the software center.

---

### Post by Sijmen on 2012-01-06
Within VLC navigate on the menubar to Video - Subtitles Track. There you can select with track you want :)

Btw, give the srt file the same name as the movie. that way it picks the subs when you load the movie. And place the subs in the same directory.

Another note, VLC will pick the *.sub as the subtitles file, my guess is that *.sub contains all the languages in one file. With the above method you can pick the language you want.

---

### Post by rocksockdoc on 2012-01-07
> **Sijmen said:**
> Within VLC navigate on the menubar to Video - Subtitles Track. There you can select with track you want 

Thanks. I installed VLC from the Ubuntu Software Center.

VLC worked like a charm to display the subtitles.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210383&stc=1&d=1325925201[/IMG]

---

### Post by whatthefunk on 2012-01-07
Although your problems appears to be solved, Id also like to mention that subtitles can easily be displayed with mPlayer as well.  Edit > Set Subtitles and then just choose the .srt file you want.

---

### Post by rocksockdoc on 2012-01-07
> **Sijmen said:**
> give the srt file the same name as the movie. that way it picks the subs when you load the movie. And place the subs in the same directory.

Another note, VLC will pick the *.sub as the subtitles file, my guess is that *.sub contains all the languages in one file.

Interestingly, in my tests, VLC Player only read the subtitle file in the current directory if it was named *.sub and not *.srt (which I found surprising).

As an aside, this thread on a different question pointed me toward smplayer:
- SOLVED] 			 			[Is there a conversion program that can flip an avi file 180 degrees?]("http://ubuntuforums.org/showthread.php?t=1905318")

An interesting note is that smplayer DID read the subtitle file in the current directory whether or not it was named *.sub or *.srt. 

If both (.sub & *.srt files existed, both smplayer & VLC player apparently took the *.sub file.

However, smplayer gave the option to read the srt file separately ... 

Go figure. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210384&stc=1&d=1325926347[/IMG]

---

### Post by rocksockdoc on 2012-01-07
> **whatthefunk said:**
> subtitles can easily be displayed with mPlayer as well.  Edit > Set Subtitles and then just choose the .srt file you want.

Is "Mplayer" the same as "SMplayer"?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210381&stc=1&d=1325923601[/IMG]

---

### Post by whatthefunk on 2012-01-07
> **rocksockdoc said:**
> Is "Mplayer" the same as "SMplayer"?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210381&stc=1&d=1325923601[/IMG]

smPlayer is a front end for mPlayer I believe.

---

### Post by rocksockdoc on 2012-01-07
> **whatthefunk said:**
> smPlayer is a front end for mPlayer I believe.

Thanks. I'm not familiar with the terminology.

Both worked with the subtitles I had (VLC & SMplayer/Mplayer).

SMplayer/Mplayer seemed more powerful than VLC though ... for example, SMPlayer could download subtitles from an Internet database.

Of course, the Internet database didn't have any of the subtitles I tested (it figures); but at least it has that capability. :)

Also SMPlayer/MPlayer seemed to handle 'both' the sub & srt files more gracefully than did VLC Player ... so for subtitles at least (with my extremely limited experience so far), I'd recommend SMPlayer over VLC (for now) if all you wanted to do was good subtitles.

---

### Post by rocksockdoc on 2012-01-07
I think I know where the problem lies.

Apparently the idx & sub files go hand in hand - they comprise a bitmat image of the subtitle which is superimposed onto the video:
 [http://www.afterdawn.com/guides/archive/convert_subtitles_from_sub-idx_to_srt.cfm](http://www.afterdawn.com/guides/archive/convert_subtitles_from_sub-idx_to_srt.cfm)
> VobSub's IDX and SUB subtitle format has become popular due in large  part to its flexibility and nearly universal compatibility with media  players. But there are still times when you need something different,  especially when dealing with older file formats like AVI where subtitles  need to be in text format rather than images which VobSub rips from a  DVD. Fortunately VobSub also includes a tool capable of converting subtitles to text-based formats like SRT or SSA

While the srt file is a stand-alone text file for that same avi's subtitles:
 [http://www.calcitapp.com/AVIAddXSubs.php](http://www.calcitapp.com/AVIAddXSubs.php) 
> **The idx/sub format.** This format uses a pair of files, one with  	extension idx and another with extension sub. These files go together and  	replace the srt in your player. Using idx/sub, because are external files  	(that is, not incorporated), you can subtitle any kind of video file. avi/mkv/mp4,  	you name it, if your player supports the combination.

So, for example, if I wanted to PERMANENTLY add the subtitles, apparently I have these options:

[LIST=1]
[*]To incorporate **XSUB** subtitles in the avi from **srt **files.
[*]To incorporate **XSUB** subtitles in the avi converting **idx/sub**  	files.
[*]To incorporate **XSUB** subtitles in the avi coming ***from a combination***  	of **srt** and **idx/sub** files.
[*]To generate **idx/sub** files from **srt** and use them as  	external subtitle files (in place of the original srt) in supporting players  	to subtitle any kind of video **(avi/mkv/mp4 etc)**.
[/LIST]
I'll look into these options in detail but won't be reporting back here because that task is off topic for this question.

---

### Post by rocksockdoc on 2012-01-09
I found a very nice more permanent method of playing a movie with subtitles!

Googling for a better solution, I found DeVeDe, a video DVD creator:
$ sudo apt-get install devede

Among many other options, DeVeDe will create a new video (whether AVI, or MP4, or DVD ISO) which will have the subtitles as a selectable option in any hardware DVD player.

In DeVeDe, you simply load the subtitle files and define their language, e.g., 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210488&stc=1&d=1326104459[/IMG]

DeVeDe will input subtitles of the following formats:
sub, .srt, .ssa, .smi, .txt, .aqt, .jss or .a s s

These will be true DVD subtitles, in the sense that you can enable or disable them in your hardware DVD player. You can even move their location up a bit for older equipment.

Here is a good help file for using DeVeDe for subtitles and other video conversions:
- [How to use DeVeDe on Ubuntu to convert video files with subtitles]("http://files.majorsilence.com/devede/docs/file.html")

---


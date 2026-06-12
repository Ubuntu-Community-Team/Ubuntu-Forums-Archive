---
title: "Beginner Scripting Question- How to Wait When &amp;&amp; Doesn't Work"
date: 2012-01-03
forum: General Help
---

### Post by Cluadia on 2012-01-03
Solved! :D   Solution coming soon.  Thanks Paddy Landau and Carranty!

**Hi!** I'm taking my first leap into scripting, and after pulling hair out for hours and hopeless google searches, here I am, sorry people  :P  

**Problem:**
My goal here is to create a desktop recording script which also does some seemingly needless other things after it has finished recording my desktop.  (With ffmpeg, you can stop recording by pressing ctrl+c in the terminal)
The problem I'm having is that I can't figure out how to get the script to wait until the recorder has finished recording to progress onto the next step.   Using && or even ||, it just seems to execute the next line of code immediately.   I took a look at trying to figure out how to make wait pid() things work, but geez..    For the life of me I just can't figure that out, or if it is even the right solution to this anyway.

If anyone can help me figure how on earth I should be approaching this script to make it work the way I intended---    ----geez, that would be way too nice!



**What am I intending with this script?**
I'll break down the script:

 ```
lxterminal -e ffmpeg  -f x11grab -s 1580x1050 -r 16 -i :0.0 -sameq /folder/video.mkv && mencoder /folder/video.mkv -o /folder/very-low-fps-version/video.mkv -ovc x264 -x264encopts 
```

Here, I'm calling a terminal window for the ffmpeg desktop recording script.  The reason I am calling a new terminal window for this is because Im not sure how I would stop the recording without a terminal  (this scripts intended use is as a one click button on my .. desktop, let's say.   This seems to work fine!     

The second part of this script takes that recorded video and makes another really low fps version of it and puts it in a separate folder  (for voluntary archival reasons if you must know! :P)

And so..  as mentioned, figuring out how to make the second part of the script wait until the recording has stopped has been.. tough! (the desktop recording terminal window closes immediately following recording ceasing by the way).   Is it possible to make a command that says essentally "when that terminal closes, go to the next command?"


**Here is the complete script, just in case any recommendations would break the next renaming component my script for some reason.**

```
lxterminal -e ffmpeg  -f x11grab -s 1580x1050 -r 16 -i :0.0 -sameq /folder/video.mkv && mencoder /folder/video.mkv -o /folder/very-low-fps-version/video.mkv -ovc x264 -x264encopts subq=1:bframes=2:b_pyramid=normal:weight_b -ofps .15 -nosound  && /folder/very-low-fps-version/videozee.mkv /folder/very-low-fps-version/new-fancy-name-with-the-date' '$(date +%Y-%m-%d)' h'$(date +%Hm%Ms%S).mkv &  mv -i /folder/video.mkv /folder/original-uncompressed-video-with-a-new-fancy-name-with-the-date' '$(date +%Y-%m-%d)' h'$(date +%Hm%Ms%S).mkv
```

Thanks so much for even considering to help out on this, hehe.  I hope the karma gods give you more marshmellows in your Lucky Charms

---

### Post by carranty on 2012-01-03
I've never tried recording my desktop (or have even ever used ffmpeg) so I can't help you with that aspect but running one command after another should be really simple.  For instance lets say I want to open gedit (a graphical word processor) and want to create a new folder called 'Test' - but I only want this folder to be created after gedit has closed (a crazy scenario I know, but the solution should work for you to).  I open a terminal an type 

```
 gedit ; mkdir ~/Test
```This command opens gedit, at which point I can type anything I like, but the folder test has not yet been created.  When I close gedit, the folder is created.

Writing the line 

lxterminal -e gedit ; mkdir ~/Test

and then running it will do the same.

So basically I think replacing the && with a semicolon ; here

lxterminal -e ffmpeg  -f x11grab -s 1580x1050 -r 16 -i :0.0 -sameq /folder/video.mkv** &&** mencoder /folder/video.mkv -o /folder/very-low-fps-version/video.mkv -ovc x264 -x264encopts

will do the trick.

Hope that helps.

EDIT : Also, as your script gets longer keeping it on one line can make it difficult to edit, rather than typing

[I]lxterminal -e gedit ; mkdir ~/Test 

[/I]I could create a text file with the following text

[I]#!/bin/bash
gedit
mkdir ~/Test[/I]

The two codes are entirely equivalent but the second allows you to break your script up to make it more readable (and also to comment it).

---

### Post by Paddy Landau on 2012-01-03
When you start lxterminal, there is already an instance running, and so it simply asks lxterminal to start a new window.

That's why your request appears to end immediately.

To do it automatically, rather write a script to do what you want, as follows.
```
[COLOR=Blue]**#!/bin/bash**[/COLOR]

[COLOR=Blue]# Leave a message.[/COLOR]
[COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'Starting to record the session.'[/COLOR]

[COLOR=Blue]# If ffmpeg is stopped with ^C, continue with the script.[/COLOR]
[COLOR=DarkRed]**trap**[/COLOR] [COLOR=Magenta]'echo'[/COLOR] SIGINT

[COLOR=Blue]# Record my session.[/COLOR]
[COLOR=DarkRed] if ! **ffmpeg**[/COLOR]  -f x11grab -s 1580x1050 -r 16 -i :0.0 -sameq /folder/video.mkv
[COLOR=DarkRed]then[/COLOR]
        [COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'ffmpeg (1) failed.'[/COLOR]
        [COLOR=DarkRed]**exit**[/COLOR] 1
[COLOR=DarkRed]fi[/COLOR]

[COLOR=Blue]# No longer ignore requests to terminate.[/COLOR]
[COLOR=DarkRed]**trap**[/COLOR] SIGINT

[COLOR=DarkRed]if ! **mencoder**[/COLOR] /folder/video.mkv -o /folder/very-low-fps-version/video.mkv -ovc x264 -x264encopts
[COLOR=DarkRed]then[/COLOR]
        [COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'mencoder (1) failed.'[/COLOR]
        [COLOR=DarkRed]**exit**[/COLOR] 1
[COLOR=DarkRed]fi[/COLOR]

[COLOR=Blue] # Leave a message.[/COLOR]
[COLOR=DarkRed]**echo**[/COLOR] -e [COLOR=Magenta]'\nRecording finished.\nStarting to archive session.'[/COLOR]

# Archive the session.
[COLOR=DarkRed]if ! [/COLOR][COLOR=DarkRed]**ffmpeg**[/COLOR]  -f x11grab -s 1580x1050 -r 16 -i :0.0 -sameq /folder/video.mkv
        [COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'ffmpeg (2) failed.'[/COLOR]
        [COLOR=DarkRed]**exit**[/COLOR] 1
[COLOR=DarkRed]fi[/COLOR]

[COLOR=DarkRed]if ! **mencoder**[/COLOR] /folder/video.mkv -o /folder/very-low-fps-version/video.mkv -ovc x264 -x264encopts subq=1:bframes=2:b_pyramid=normal:weight_b -ofps .15 -nosound
[COLOR=DarkRed]then[/COLOR]
         [COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'mencoder (1) failed.'[/COLOR]
         [COLOR=DarkRed]**exit**[/COLOR] 1
 [COLOR=DarkRed]fi[/COLOR]
 
[COLOR=Blue]# I am not sure you got this next bit quite right, but I could be wrong:[/COLOR]
[COLOR=DarkRed]/folder/very-low-fps-version/videozee.mkv[/COLOR] /folder/very-low-fps-version/new-fancy-name-with-the-date[COLOR=Magenta]' '[/COLOR]$([COLOR=DarkRed]**date**[/COLOR] +%Y-%m-%d)[COLOR=Magenta]' h'[/COLOR]$([COLOR=DarkRed]**date**[/COLOR] +%Hm%Ms%S).mkv
[COLOR=DarkRed]if[/COLOR] [[ ${?} != 0 ]]
[COLOR=DarkRed]then[/COLOR]
        [COLOR=DarkRed]**echo**[/COLOR] 'Folder bit failed.'
        [COLOR=DarkRed]**exit**[/COLOR] 1
 [COLOR=DarkRed]fi[/COLOR]

[COLOR=Blue]# Move the file.[/COLOR]
[COLOR=DarkRed]if ! [/COLOR][COLOR=DarkRed]**mv**[/COLOR] -i /folder/video.mkv /folder/original-uncompressed-video-with-a-new-fancy-name-with-the-date[COLOR=Magenta]' '[/COLOR]$([COLOR=DarkRed]**date**[/COLOR] +%Y-%m-%d)[COLOR=Magenta]' h'[/COLOR]$([COLOR=DarkRed]**date**[/COLOR] +%Hm%Ms%S).mkv
[COLOR=DarkRed]then[/COLOR]
          [COLOR=DarkRed]**echo**[/COLOR] [COLOR=Magenta]'mv failed.'[/COLOR]
          [COLOR=DarkRed]**exit**[/COLOR] 1
  [COLOR=DarkRed]fi[/COLOR]
```

---

### Post by Cluadia on 2012-01-03
It works!  Woooooohooo!!    Resulting solution will be edited into the first post soon.

Carranty:   For whatever reason, the ; didn't work! I guess its something specific with the ffmpegs encoder compared to gedit (emphasis on guess, I have no idea what I'm doing  :D).   Thank you very much for taking the time to give helping a try though!  Additional compliments and the "Carranty effect" in the next paragraph, haha.

 I was always a bit intimidated by getting knee deep in figuring out how bin and bash works, but after having a taste of its power, and having a bit of success and understanding how it works, I think its probably worth it.  Thanks for the recommendation!   I was getting rather lost in that script's code already, haha.

Thanks again!

Paddy Landau:  With a little tweaking, with your script, I was able to achieve complete satisfaction with achieving my goals with this :D   To write that whole script out out of pure kindness is absolutely amazing.  Thank you so much!   People like you should be making millions.  Use this as a reference, if not!  :D  I hope at least others who just happen to run into the same problem as this can find this post in the search engines.

I will be editing my first post to include the solved script and mark as solved as soon as I can find a few more minutes.   The tweaks were really nothing more than erasing a few lines of code (erasing the exits namely).   For some reason both the ffmpeg portion and the mencoder portion were resulting in exits, even if they succeeded.  However, the mv parts did not result in !s.  Can't say that my tweaked code won't blow things up in the future as I have no idea what I'm doing still past a little php experience, hehe.   But if it helps you at all in the future to know that ffmpeg and mencoder return !s in those scenarios after finishing, I thought I'd mention!

Thanks again x 40 million and endless good luck!

---

### Post by Paddy Landau on 2012-01-04
> **Cluadia said:**
>   People like you should be making millions.
LOL, if only! Pay it forward when you can.

---


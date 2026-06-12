---
title: "How do I write a Script or shell?"
date: 2010-08-11
forum: General Help
---

### Post by PDA1 on 2010-08-11
I want to automate a simple process using a script of shell or whatever it's called with Terminal (we used to call them "batch" files in the old DOS days). 

Here are the commands I want to execute in order.  I want to them to execute sequentially upon completion of the previous command-

1rst Command-  ffmpeg -i VideoFile1.avi -sameq intermediate1.mpg

2nd Command- ffmpeg -i VideoFile2.avi -sameq intermediate2.mpg

3rd Command- cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg

4th Command- ffmpeg -i intermediate_all.mpg -sameq FONAL.avi


Please keep it simple- I'm not too knowledgeable in programming.

---

### Post by TyLLy_4 on 2010-08-11
Try this ... 

this operator && only runs the second command after and if the first command executed properly. 

```

#!/bin/sh
ffmpeg -i VideoFile1.avi -sameq intermediate1.mpg && ffmpeg -i VideoFile2.avi -sameq intermediate2.mpg && cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg && ffmpeg -i intermediate_all.mpg -sameq FONAL.avi


```

Copy that into a text file and rename it to name.sh. Also ypou have to right click it and set permission to execute.

---

### Post by PDA1 on 2010-08-11
Excellent!  Thanks so much.

You make it look easy.

&&.....what a simple command.

---

### Post by linux18 on 2010-08-11
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

I have found this to be the most helpful guide to shell scripting newbies

---

### Post by TyLLy_4 on 2010-08-11
Ubuntu makes it easier ... i just had that same need jesterday. 

Shell script is really easy. Next time make a Google search for what you need. 

Most likely someone already made a shell script you can download and modify 

:D

---

### Post by linux18 on 2010-08-11
> **TyLLy_4 said:**
> Ubuntu makes it easier ... i just had that same need jesterday. 

Shell script is really easy. Next time make a Google search for what you need. 

Most likely someone already made a shell script you can download and modify 

:D
lol, great sig!

---

### Post by FakeOutdoorsman on 2010-08-12
Another method.  This simply concatenates the input audio and video formats.  Not guaranteed to work for all formats, but it will look better than anything else when it does work because there is no re-encoding.  Inputs should should have the same audio and video formats, frame rate, frame size, etc.
```
#!/bin/sh
# usage: ./ffcat.sh input1.foo input2.foo output.foo
ffmpeg -i concat:"$1|$2" -acodec copy -vcodec copy "$3"
```
You'll also need to compile a more recent FFmpeg to use the *concat* protocol (unless you're using Maverick):

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by PDA1 on 2010-08-12
I have no idea what any of your script means.

Would you please explain each part?

---

### Post by FakeOutdoorsman on 2010-08-12
This script is the equivalent to:
```
ffmpeg -i concat:"/path/to/input.avi|/path/to/input2.avi" -acodec copy -vcodec copy out.avi
```

[indent]**ffmpeg** - The ffmpeg binary.
**-i concat:** - Tell ffmpeg to use the *concat* protocol which will concatenate the inputs that you give it.
**-acodec copy** - Copy the audio streams from the inputs.  Like a copy and paste from the inputs to the output.
**-vcodec copy** - Copy the video streams from the inputs to the output.
**out.avi** - The output file.[/indent]

If you want to use it as a script file copy the code from my previous post and place it into a file called *ffcat.sh*.  Then make it executable:
```
chmod +x ffcat.sh
```
Then run it like this:
```
./ffcat.sh anyone_want_a_peanut.avi rodents_of_unusual_size.avi output.avi
```

---

### Post by PDA1 on 2010-08-12
That's great....thanks.

The other question I have is what if the audio formats are different?  I did a "combine" file today and the 2nd part of the video sounded like Lurch from the Adams family talking.

Any idea how to solve that one?

---

### Post by FakeOutdoorsman on 2010-08-12
> **PDA1 said:**
> That's great....thanks.

The other question I have is what if the audio formats are different?  I did a "combine" file today and the 2nd part of the video sounded like Lurch from the Adams family talking.

Any idea how to solve that one?

Here are two ways.  This is like my previous example, but re-encodes the audio to MP3. You should probably use an output format that can handle your specific video format and MP3 audio format.  MKV is my favorite.  See [Comparison of container formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats) for a nice chart.
```
#!/bin/sh

# usage: ./ffcat.sh input1.foo input2.foo output.foo
ffmpeg -i concat:"$1|$2" -vcodec copy -acodec libmp3lame -ac 2 -aq 4 -ar 44100 "$3"
```
This next example is adapted from the [FFmpeg FAQ](http://www.ffmpeg.org/faq.html#SEC27).  It will re-encode both the video and audio and is good if your input video and audio formats vary.  It uses named pipes to avoid large intermediate files.

This script is designed for a more recent FFmpeg than what Lucid has, but it can be changed to work with older FFmpeg versions.  You will need to [enable the mp3 encoder](http://ubuntuforums.org/showthread.php?t=1117283) if you use FFmpeg from the repository. Also, change *-vpre slow* to *-vpre hq* if you use FFmpeg from the repository (unless you're using Ubuntu Maverick or above).
```
#!/bin/sh

# Re-encode and combine two inputs using named pipes to avoid large intermediate files.
# Adapted from FFmpeg FAQ: 3.15 How can I join video files?
# http://www.ffmpeg.org/faq.html#SEC27

# Usage: ./ffcombine.sh input1.foo input2.foo output.mkv

# Exit upon error
set -e

# Make named pipes
mkfifo temp1.a
mkfifo temp1.v
mkfifo temp2.a
mkfifo temp2.v
mkfifo all.a
mkfifo all.v

# Re-encode audio
ffmpeg -i "$1" -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 - > temp1.a < /dev/null &
ffmpeg -i "$2" -vn -f u16le -acodec pcm_s16le -ac 2 -ar 44100 - > temp2.a < /dev/null &

# Re-encode video and combine everything
ffmpeg -i "$1" -an -f yuv4mpegpipe - > temp1.v < /dev/null &
{ ffmpeg -i "$2" -an -f yuv4mpegpipe - < /dev/null | tail -n +2 > temp2.v ; } &
cat temp1.a temp2.a > all.a &
cat temp1.v temp2.v > all.v &
ffmpeg -f u16le -acodec pcm_s16le -ac 2 -ar 44100 -i all.a -f yuv4mpegpipe -i all.v -acodec libmp3lame -aq 4 -vcodec libx264 -vpre slow -crf 24 -threads 0 -y "$3"

#Delete named pipes
rm -f temp[12].[av] all.[av]

exit
```

---

### Post by TyLLy_4 on 2010-08-12
sorry I'm not very good with multimedia stuff. But I'm sure you can find some useful info here. 

[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)

also you might wanna try sing the GUI? 
[http://brian.carnell.com/articles/2008/winff-gui-for-ffmpeg/](http://brian.carnell.com/articles/2008/winff-gui-for-ffmpeg/)

---

### Post by PDA1 on 2010-08-12
[QUOTE=FakeOutdoorsman;9712192]This script is the equivalent to:
```
ffmpeg -i concat:"/path/to/input.avi|/path/to/input2.avi" -acodec copy -vcodec copy out.avi
```Thanks for the effort.  I tried it but it doesn't work.

Here's the code I wrote-

```
ffmpeg -i concat /home/Mike/Desktop/Video wdl1.mpg|/home/Mike/Desktop/Video wdl2.mpg -acodes copy -vcodec out.mpg
```

---

### Post by FakeOutdoorsman on 2010-08-12
> **PDA1 said:**
> Thanks for the effort.  I tried it but it doesn't work.
In what way did it not work?  Show any error messages you may have received.  Otherwise I'll have to guess what is wrong.
> **PDA1 said:**
> Here's the code I wrote-
```
ffmpeg -i concat /home/Mike/Desktop/Video wdl1.mpg|/home/Mike/Desktop/Video wdl2.mpg -acodes copy -vcodec out.mpg
```

Your command has some errors and is missing some things.  Try this:
```
ffmpeg -i concat:'/home/Mike/Desktop/Video wdl1.mpg|/home/Mike/Desktop/Video wdl2.mpg' -acodec copy -vcodec copy out.mpg
```

---

### Post by PDA1 on 2010-08-12
The error is "no such file or directory".

The error is probably on my side.  Too tired to work on it write now.

Thanks.

---


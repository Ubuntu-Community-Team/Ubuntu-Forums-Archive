---
title: "Bash script help (SIMPLE)"
date: 2010-11-11
forum: General Help
---

### Post by JoeTheDude on 2010-11-11
I was just toying around with Bash scripting and wrote this up:

```

#!/bin/bash
echo "Video filename: "
read video
echo "Output mp3 filename: "
read audio
ffmpeg -i "$video" -ab 192k "$audio"
echo "Done!"
read
```

Just rips the audio from a video file using ffmpeg. Nice and simple. Doesn't work though. Actually it does work if I manually type in the directory/filename for the video and audio variables. But if I drag the video file into the terminal window (copying in its absolute directory), it doesn't work. I'm guessing the reason is that when you drag something into the terminal, it gets apostrophes placed around it. So when ffmpeg tries to locate the file, it says it can't be found because it thinks the apostrophes are literally part of the directory name.

Soooo, how do I get around this? Seems like it should be pretty simple.

---

### Post by JoeTheDude on 2010-11-11
Bump!

---

### Post by p424n0id on 2010-11-11
Try removing the " 's from the variables.

---

### Post by JoeTheDude on 2010-11-11
> **p424n0id said:**
> Try removing the " 's from the variables.

I've tried that and about a million other things. I have narrowed it down to the issue being with the apostrophes.

Say I drag a file into terminal.
```
'/home/user/file.mp4'
```
When executing commands in the terminal normally, the apostrophes are seen as containing a literal string. But when making a bash variable equal to the above code, it sees the apostrophes as *actual* apostrophes in the directory/file name.

So I need some way to trim away the first and last apostrophes from my variables before I execute ffmpeg with them. I Google'd this but only found vague articles talking about a command called Sed, but I couldn't find a thorough explanation of how it works anywhere.

---

### Post by Isaac356 on 2010-11-11
This was the best I could think of. It's kind of ugly, but it should work.

```

#!/bin/bash
echo "Video filename: "
read video
video=${video#\'}
video=${video%\'}
echo "Output mp3 filename: "
read audio
audio=${audio#\'}
audio=${audio%\'}
ffmpeg -i "$video" -ab 192k "$audio"
echo "Done!"
read
```

EDIT:
I think what p424n0id meant was to remove the double quotes from the ffmpeg line. In that case, the single quotes would be substituted directly in, and everything would work itself out. I'm not entirely sure how well it would work (and if there were no apostrophes, like you decided to manually type it, it probably would not work), but this script should only remove apostrophes if they exist, so it's all good. Only thing that would make this better is to learn how to use sed.

---

### Post by JoeTheDude on 2010-11-12
> **Isaac356 said:**
> This was the best I could think of. It's kind of ugly, but it should work.

```

#!/bin/bash
echo "Video filename: "
read video
video=${video#\'}
video=${video%\'}
echo "Output mp3 filename: "
read audio
audio=${audio#\'}
audio=${audio%\'}
ffmpeg -i "$video" -ab 192k "$audio"
echo "Done!"
read
```

EDIT:
I think what p424n0id meant was to remove the double quotes from the ffmpeg line. In that case, the single quotes would be substituted directly in, and everything would work itself out. I'm not entirely sure how well it would work (and if there were no apostrophes, like you decided to manually type it, it probably would not work), but this script should only remove apostrophes if they exist, so it's all good. Only thing that would make this better is to learn how to use sed.

Hey look at that, it works! Thank you, sir. I still need to read more on string manipulation but this will do fine for the time being. Thanks again.

---


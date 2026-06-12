---
title: "bash script using ffmpeg failing with &quot;invalid argument&quot;"
date: 2011-09-26
forum: General Help
---

### Post by pythonscript on 2011-09-26
I'm trying to write a bash script that calls ffmpeg to convert an avi file to an mp4 file. This is the code:

```

ffmpeg -i "$0" -acodec libfaac -ab 128k -vcodec libx264 -vpre baseline -s 320x240 -threads 0 -crf 20 "$1"

```

The command works perfectly when I call it from the shell and substitute file names for the parameters; however, when I call the bash script with

```

sh nokia.sh 1.avi out.mp4

```

or

```

./nokia.sh 1.avi out.mp4

```

I get the following error:

```

ffmpeg version N-31651-gf52ad8c, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jul 27 2011 10:56:58 with gcc 4.5.2
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-nonfree --enable-postproc --enable-version3 --enable-x11grab
  libavutil    51. 11. 0 / 51. 11. 0
  libavcodec   53.  9. 0 / 53.  9. 0
  libavformat  53.  6. 0 / 53.  6. 0
  libavdevice  53.  2. 0 / 53.  2. 0
  libavfilter   2. 27. 3 /  2. 27. 3
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
nokia.sh: Invalid data found when processing input

```

The file is executable, so what am I missing?

Thank you!

---

### Post by sisco311 on 2011-09-26
sh is not bash. In Ubuntu, sh is a symlink to dash. 

$0 is the name, or the path, of the script.

1, 2, 3 ... are the positional parameters, they contain the arguments that were passed to the current script or function.

See: [http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

Oh, and don't use extensions for your scripts. Scripts define new commands that you can run, and commands are generally not given extensions. Once again bash scripts are not sh scripts, so don't use .sh

---

### Post by pythonscript on 2011-10-09
Thanks for the help; that's a great link that you posted, and it's been quite helpful. The script is working great now. No .sh extension, just executing the script, plain and simply. The $0 was my main problem, and with that fixed it's converting great. 

Thanks!

---

### Post by sisco311 on 2011-10-09
You are welcome!

Don't forget to mark this thread as [SOLVED].

---


---
title: "Trouble escaping input paths on a simple BASH script"
date: 2011-04-21
forum: General Help
---

### Post by juliushibert63 on 2011-04-21
I've written a small script to reencode video using mencoder that accepts two inputs, 1st an oringinal file and second the name of the new file.

However I'm having a lot of trouble trying to escape the path once inside the script. The paths are supplied to the script escaped but don't seem to remain escaped.

Here's the script 

```
#!/bin/sh

INPUT_File="$1"
OUTPUT_File="$2"

echo "Starting encoding video"
echo $INPUT_File
echo $OUTPUT_File

mencoder $INPUT_File -channels 6 -ovc xvid -xvidencopts fixed_quant=4 -vf harddup -oac copy -o /media/Media/Xbox360/$OUTPUT_File
echo "Finished converting the files"
exit 0

```

and here's the output;

```
./convert-video-xbox.sh /media/Media/TV/30\ Rock/Season\ 05/30\ Rock\ -\ s05e03\ -\ Let\'s\ Stay\ Together.mkv test.avi
Starting encoding video
/media/Media/TV/30 Rock/Season 05/30 Rock - s05e03 - Let's Stay Together.mkv
test.avi
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
File not found: '/media/Media/TV/30'
Failed to open /media/Media/TV/30.
Cannot open file/device.

Exiting...
Finished converting the files

```

I've tried just about every combination of escaping the variables with single and double quotes to no suck luck.

---

### Post by mcduck on 2011-04-21
Did you try using the quotes not only when defining the variables, but also when *using* them?

```
#!/bin/sh

INPUT_File="$1"
OUTPUT_File="$2"

echo "Starting encoding video"
echo "$INPUT_File"
echo "$OUTPUT_File"

mencoder "$INPUT_File" -channels 6 -ovc xvid -xvidencopts fixed_quant=4 -vf harddup -oac copy -o /media/Media/Xbox360/"$OUTPUT_File"
echo "Finished converting the files"
exit 0
```

---

### Post by juliushibert63 on 2011-04-21
No I hadn't but that worked a treat!

Thank you very much.

---


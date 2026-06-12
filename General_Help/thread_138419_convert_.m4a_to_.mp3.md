---
title: "convert .m4a to .mp3"
date: 2006-03-01
forum: General Help
---

### Post by eyebrowman92 on 2006-03-01
i was wondering how to convert a .m4a to a .mp3 because my mp3 player doesn't read .m4a's. does anyone know how?

---

### Post by powder on 2006-03-01
I wouldn't recommend doing that, you will definitely lose audio quality converting mp3 -> m4a.  What audio player are you using?  I'm using Beep Media Player with the mp4 plugin and it works just fine.

---

### Post by eyebrowman92 on 2006-03-01
i mean portable mp3 player. i'm using an iriver h10 and it isn't compatible with .m4a's

---

### Post by RAOF on 2006-03-01
You can do it from the command line with
```
gst-launch0.8 filesrc location=*/path/to/m4a* | decodebin | lame preset=1001 quality=0 | filesink location=*/path/to/output*
```

I should be able to whip up a quick bash script to automatically convert all the m4a files in the current directory for you...

---

### Post by powder on 2006-03-01
If that's the case, go right ahead. ;)

---

### Post by RAOF on 2006-03-01
And here it is:  Copy this script into a file, and make it executable:
```

#!/bin/bash                                                                       

IFS=\"
GSTLAUNCH=gst-launch-0.8
ENCODER=lame
ENCODEOPTIONS=preset=1001 quality=0
INPUTEXTENSION=$1
OUTPUTEXTENSION=mp3

INPUTFILES=`find $2 -iname *.$INPUTEXTENSION -printf %p\"`

usage() {
    echo "Usage is $0 <extension> <path>"
    echo "$0 will transcode all files with the specified extension"
    echo "in the <path> directory, and all subdirectories"
    echo
    echo "Example: "
    echo "$0 m4a Music"
    echo "Will convert all the *.m4a files in the ./Music directory"
    echo "and all it's subdirectories to .mp3 files"
}

if [[ $# != 2 ]] ; then
usage ;
exit ;
fi

for INPUT in $INPUTFILES ;
do OUTPUT=`echo $INPUT | sed s/.$INPUTEXTENSION/.$OUTPUTEXTENSION/` ;
echo "Converting \"$INPUT\" to \"$OUTPUT\"" ;
$GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! \
$ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\" ;
done

```

---

### Post by fishmorg909 on 2006-03-02
Or you could go to Applications > Add Applications > Sound & Video, and add Sound Converter. It does the job.

---

### Post by froggontherocks on 2006-04-20
Thanks for the Idea about the sound converter program.

---

### Post by Mapleman on 2006-09-21
I am 3 days old to Ubuntu and wondering how to port to file and make executable as mentioned above, I have a lot of m4a songs to covert to mp3, any help is appreciate eh

Thanks:confused: :?:

---

### Post by bretticus on 2006-10-11
> I am 3 days old to Ubuntu and wondering how to port to file and make executable as mentioned above, I have a lot of m4a songs to covert to mp3, any help is appreciate eh

I just used the sound converter program. Although that was good of RAOF to whip up a bash script. And the automatic mp4 finding feature would be beneficial to your plight. So just do the following at a command prompt (terminal) ...

```

$ sudo apt-get install gstreamer0.8-tools
$ gedit mp42mp3 &

```

Copy and paste everything from RAOF's code section into gedit and save.

To make the script executable, use the chmod command in the terminal again...

```

$ chmod +x mp42mp3

```

Now just type...

```

$ ./mp42mp3

```

command prompt which will show you how to use the program. For example,the following will text should show up among the usage instructions...
> 
Example: 
./mp42mp3 m4a Music
Will convert all the *.m4a files in the ./Music directory
and all it's subdirectories to .mp3 files


Keep in mind, I haven't tested this but it should work.

---

### Post by kloy1334 on 2006-11-04
So I tried this method and it doesn't work for me.
I would simply like to convert some mp4s to mp3s.
Below is the echo I get back from the script.

```

jeff@desktop:~/Downloads$ ./mp42mp3 m4a Denison_Witmer-Safe_Away.zip_FILES
Converting "Denison_Witmer-Safe_Away.zip_FILES/01 Steven.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/01 Steven.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12902 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/02 Breathe In This Life.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/02 Breathe In This Life.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12910 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/03 Over My Head.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/03 Over My Head.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12918 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/04 This And That.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/04 This And That.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12926 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/05 Closer To The Sun.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/05 Closer To The Sun.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12934 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/06 What Will Stay_.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/06 What Will Stay_.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12942 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/07 Miles.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/07 Miles.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12950 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/08 Dain.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/08 Dain.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12958 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/09 Los Angeles.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/09 Los Angeles.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12966 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/10 Around Everything.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/10 Around Everything.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
^[q./mp42mp3: line 28: 12974 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/11 I Would Call You Now.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/11 I Would Call You Now.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12982 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/12 Sarah's Bridge.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/12 Sarah's Bridge.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12992 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/13 I Won't Leave.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/13 I Won't Leave.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13000 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/14 Broken.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/14 Broken.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13008 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/15 Say You'll Stick Around.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/15 Say You'll Stick Around.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13016 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/16 Meant To Be.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/16 Meant To Be.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13024 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"

```

---

### Post by RAOF on 2006-11-04
> **kloy1334 said:**
> So I tried this method and it doesn't work for me.
I would simply like to convert some mp4s to mp3s.
Below is the echo I get back from the script.

```

jeff@desktop:~/Downloads$ ./mp42mp3 m4a Denison_Witmer-Safe_Away.zip_FILES
Converting "Denison_Witmer-Safe_Away.zip_FILES/01 Steven.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/01 Steven.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12902 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/02 Breathe In This Life.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/02 Breathe In This Life.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12910 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/03 Over My Head.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/03 Over My Head.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12918 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/04 This And That.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/04 This And That.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12926 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/05 Closer To The Sun.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/05 Closer To The Sun.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12934 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/06 What Will Stay_.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/06 What Will Stay_.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12942 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/07 Miles.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/07 Miles.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12950 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/08 Dain.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/08 Dain.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12958 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/09 Los Angeles.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/09 Los Angeles.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12966 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/10 Around Everything.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/10 Around Everything.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
^[q./mp42mp3: line 28: 12974 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/11 I Would Call You Now.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/11 I Would Call You Now.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12982 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/12 Sarah's Bridge.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/12 Sarah's Bridge.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 12992 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/13 I Won't Leave.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/13 I Won't Leave.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13000 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/14 Broken.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/14 Broken.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13008 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/15 Say You'll Stick Around.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/15 Say You'll Stick Around.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13016 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"
Converting "Denison_Witmer-Safe_Away.zip_FILES/16 Meant To Be.m4a" to "Denison_Witmer-Safe_Away.zip_FILES/16 Meant To Be.mp3"
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $3 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
   $2 = 
   $1 = 
WARNING: erroneous pipeline: no element "lame"
         Trying to run anyway.
RUNNING pipeline ...
./mp42mp3: line 28: 13024 Segmentation fault      (core dumped) $GSTLAUNCH filesrc location=\"$INPUT\" ! decodebin ! $ENCODER $ENCODEOPTIONS ! filesink location=\"$OUTPUT\"

```

The script should be modified if you're running anything newer than Breezy (Ubuntu 5.10, in the official naming scheme).  Past that release, GStreamer 0.10 became the default.  You need to change **gst-launch-0.8** to **gst-launch-0.10**, and ensure that the package **gstreamer0.10-plugins-ugly-multiverse** is installed; that package contains the "lame" element.

---

### Post by Jongi on 2007-01-07
I get the following error on edgy 

```

WARNING: erroneous pipeline: no element "decodebin"
         Trying to run anyway.
RUNNING pipeline ...
Execution ended after 1048 iterations (sum 65974000 ns, average 62952 ns, min 38000 ns, max 13255000 ns
```

---

### Post by RAOF on 2007-01-08
> **Jongi said:**
> I get the following error on edgy 

```

WARNING: erroneous pipeline: no element "decodebin"
         Trying to run anyway.
RUNNING pipeline ...
Execution ended after 1048 iterations (sum 65974000 ns, average 62952 ns, min 38000 ns, max 13255000 ns
```

You haven't got gstreamer installed properly, I think.  The "decodebin" element is installed in gstreamer0.10-plugins-base, as far as I can tell.  I thought Edgy shipped with a free GStreamer stack installed by default, strange.

---

### Post by yolfer on 2007-01-17
Edit:  Nevermind, I got this figured out.


-------------------------------------------


When I try to use this script, I get an error about the "decodebin" command not being available. So I tried this:

$ which decodebin

and it's not on my system.  How do I install that?  I already have gstreamer0.10-plugins-base installed:

joe@joegoldberg2:~$ sudo apt-get install gstreamer0.10-plugins-base
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Also, same for "filesink"

Thanks,
Joe

---

### Post by bryanpaluch on 2007-02-12
Anyone have any ideas on converting m4a to mp3 and keeping id3 tags. I used that script the other week and now thats i've imported songs on to my zen they are all without id3 tags. Pretty annoying stuff since I converted over 500 songs. Would sound converter leave id3 tags. I can't try it right now since I'm at work.

---

### Post by RAOF on 2007-02-12
In order to preserve tags I **think** you could add a "! id3v2mux " to the ENCODEOPTIONS in the script.

---

### Post by CameronCalver on 2007-04-08
Ok im not sure if this thread is still alive but i just tryed this and it worked with one file i was glad then i tryed with another file and it wont work i also tryed with the original file again heres the output
```
cameron@ubuntu:~$ ./mp42mp3 m4a /home/cameron/A_New_England.m4a
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]
cameron@ubuntu:~$

```

---

### Post by visio on 2007-04-15
> **CameronCalver said:**
> Ok im not sure if this thread is still alive but i just tryed this and it worked with one file i was glad then i tryed with another file and it wont work i also tryed with the original file again heres the output
```
cameron@ubuntu:~$ ./mp42mp3 m4a /home/cameron/A_New_England.m4a
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]
cameron@ubuntu:~$

```

yea i had that same problem (Kubuntu 7.04 Feisty Fawn)
all you have to do is remove  ' -iname'  from the code
the line should read

INPUTFILES=`find $2 *.$INPUTEXTENSION -printf %p\"`

---

### Post by wardard on 2007-04-17
why not just use a program to do this and it would be much easier! Personally, I use [NoteBurner]("http://www.noteburner.com") and it is easy and stable.

---

### Post by sdowney717 on 2007-07-11
I have been using Gnormalize for this
[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

you can install lame etc... using synaptic. I have it all working except the volume normalize feature.

---

### Post by stevenstromer on 2007-07-17
Hi. I'm Fedora user sneaking into your Ubuntu forum. I'm writing a shell script that looks for new .m4a files and converts them to .mp3, but I'm encountering a problem. When executing:

gst-launch filesrc location=\"$M4A_SONG\" ! decodebin ! \ lame preset=1001 quality=0 ! filesink location=\"$MP3_SONG\" ;

I am getting the following errors:

Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
ERROR: from element /pipeline0/filesrc0: Internal data flow error.
Additional debug info:
gstbasesrc.c(1614): gst_base_src_loop (): /pipeline0/filesrc0:
streaming task paused, reason not-linked (-1)
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
FREEING pipeline ...


I have the following installed:

gstreamer.i386                           0.10.11-1.fc6          installed
gstreamer-tools.i386                     0.10.11-1.fc6          installed
gstreamer-plugins-base.i386              0.10.11-1.fc6          installed
gstreamer-plugins-good.i386              0.10.4-3.fc6           installed
gstreamer-plugins-ugly.i386              0.10.5-1.fc6.rf        installed
gstreamer-plugins-pulse.i386             0.9.4-4.fc6            installed
gstreamer-plugins-farsight.i386          0.10.2-2.fc6           installed

Note that good and ugly are being retrieved from a different repo than all of the other packages. These aren't available from Redhat's Fedora repos. This is probably due to the fact that Redhat doesn't like to touch anything that might be either unstable or potentiallly litigeous. I could see how these errors might be a result of mixing plugin packages, but I'm not sure. 

I've looked everywhere, but can't seem to find a definitive reason or a solution. Would anyone here have any ideas? Much appreciated! Once I get this script fine-tuned, I'll post it here, as it has the potential to be pretty handy.

---

### Post by stevenstromer on 2007-08-02
Figured this one out. I was missing the bad plugins package, which contains the faad decoder element, needed for quicktime alac files. Missed installing it by accident. However, it appears that the next problem is that there exists no codec for audio/x-alac files. Not fully understanding this, or how previous posters have managed to get this to work. I am researching, and will post. Any ideas or advice would be appreciated!

---

### Post by naaman on 2007-12-11
Just installed soundconverter - [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/) - working quite well

```
sudo apt-get install soundconverter
```

---

### Post by Evolution-06 on 2008-02-06
> **naaman said:**
> Just installed soundconverter - [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/) - working quite well

```
sudo apt-get install soundconverter
```

worked flawlessly and kept the tags.

---

### Post by McFugger on 2008-02-22
I can't find it in the add/remove programs list or anything like it
, will it work for 64 bit ubuntu 7.10?

Wow i am stupid never mind i found it, thanks anyway hehe

---

### Post by RoaringMuddButt on 2008-02-27
I went the SoundConverter route, only I had 900 of my 3000 songs to convert to mp3, so I ran a search for .mp4 files and dragged them over to the SoundConverter window. This was way easier than trying to run a script to find the mp4s, and SoundConverter keeps the ID3 tags!

---

### Post by rare HERO on 2008-06-28
> **fishmorg909 said:**
> Or you could go to Applications > Add Applications > Sound & Video, and add Sound Converter. It does the job.

Thanks!

---


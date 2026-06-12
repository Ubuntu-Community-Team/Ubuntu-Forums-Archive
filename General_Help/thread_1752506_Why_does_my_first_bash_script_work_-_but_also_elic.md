---
title: "Why does my first bash script work - but also elicit Kolourpaint errors?"
date: 2011-05-07
forum: General Help
---

### Post by rocksockdoc on 2011-05-07
This is my first bash script ever. I wrote it to step though a directory of hundreds of pictures, and ad-hoc add a bottom canvas and then captions in that canvas only to a select few.

Since no one ubuntu picture editor does both viewing and captioning well, I was forced to use multiple photo editing programs:

[LIST]
[*]Eye of Gnome (because it's a fast viewer ... although "feh" would probably have been as fast)
[*]KolourPaint (because it's the only Ubuntu program that does decent captions & curved arrows)
[*]ImageMagick (because it can easily add a 100-pixel canvas to the bottom of the picture)
[/LIST]
REFERENCES:
- [How to batch add 200 white canvas pixels to rotated JPEG bottom edge]("http://ubuntuforums.org/showthread.php?t=1720281")
- [How do YOU scroll through hundreds of photos & move good ones to a separate folder?]("http://ubuntuforums.org/showthread.php?t=1625745")
- [Is there an extension to "Eye of Gnome" to RENAME or DELETE pictures while viewing?]("http://ubuntuforums.org/showthread.php?t=1737710")
- [What's a good curved ARROW drawing tool in Ubuntu (similar to Paint.NET on Windoze)?]("http://ubuntuforums.org/showthread.php?t=1575505")
- [How best to rename all JPEGs in a folder by EXIF date & time stamp]("http://ubuntuforums.org/showthread.php?t=1694592")
- [What's the best (i.e., quickest and easiest) program to manually crop digital photos]("http://ubuntuforums.org/showthread.php?t=1570447")
etc.

Even though the script below works as intended, it still elicits the following error:
```

Editing this picture
Adding canvas ...
Editing caption ...
Starting KolourPaint on a 24-bit screen...
**[COLOR=DarkRed]kolourpaint(4197): couldn't create slave: "Unable to create io-slave:[/COLOR]**  <=== this is the error
**[COLOR=DarkRed]klauncher said: Unknown protocol ''.[/COLOR]**  <=== what is this error?
[COLOR=DarkRed]**" **[/COLOR]

```Can you help me identify the problem to improve this script for captioning only select pictures?
```

#!/bin/sh
# bash -x /usr/local/bin/pic.sh
# WIP Need to add the naming of the outgoing file based on EXIF time & date information
# WIP May later switch from EOG/KolourPaint to Feh (feh has a useful '--action1' capability)
############################################################################
# Designed to run in a directory containing only picture files.
# 0. Step through the files with a fast viewer (i.e., eye of gnome).
# 1. Select which pictures you would like to caption.
# 2. Add a canvas only to the selected pictures & then add the caption.
# 3. Save the newly captioned picture as a new name (preserving the original).
# 4. Move on to the next picture until done.
# Use model: Simply run "pic.sh" in a directory containing pictures.
############################################################################
sub_view() {
  echo "Viewing picture with the fastest Ubuntu viewer I can find ..."
  eog $infile
}
sub_canvas() {
  echo "Adding 100-pixel canvas to the bottom of the picture based on Ubuntu forums help ..."
  convert $infile -bordercolor white -gravity south -splice 0x100 $outfile
}
sub_caption() {
  echo "Editing caption using the best Ubuntu texting & curved-arrow editor I can find ..." 
  kolourpaint $outfile
}
############################################################################
echo "Enter photo naming prefix for outgoing file naming (e.g., my_vacation_pics")
read prefix
index=expr 0
############################################################################
 for f in *; do
   index=`expr $index + 1`
   infile=$f
   outfile=${prefix}_${index}_${infile}
   sub_view;
   echo "Do you wish to caption this picture? (y/n)"
   read answer
    if test $answer = y
     then echo "Editing this picture"
     sub_canvas;
     sub_caption;
    else echo "Skipping to next picture ... "
    fi
 done
############################################################################
echo "debug f is $f, prefix is $prefix, index = $index, infile = $infile, outfile = $outfile"
exit 0

```Any help is appreciated.

Note: I added three input test files to make your tests easier. Simply place just the three files in a directory (e.g., /tmp/testdir/{file1.jpg, file2.jpg, file3.jpg} and run the bash script from another location (e.g., /tmp/pic.sh).

---


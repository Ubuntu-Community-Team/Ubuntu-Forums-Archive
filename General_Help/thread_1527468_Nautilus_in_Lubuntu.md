---
title: "Nautilus in Lubuntu"
date: 2010-07-09
forum: General Help
---

### Post by avantgardaclue on 2010-07-09
Hi Guys did a fresh install of Lubuntu on my elderly machine and I have to say "Brilliant!"

Does pretty much everything i need it to do.

Maybe I'm pushing the boundaries a bit but I like using Imagemagick on some of my photos so this requires Nautilus to be able to run the scripts.

Downloaded nautilus and this works perfectly, except I have to launch it thru Terminal.

Admittedly not the end of the world but I would like to be able to add it thru "Accessories"

PCManFM (0.9.5) works more or less perfectly for everything else. Well except when deleting files on USB sticks. Select file and then delete. File disapears. Hit Ctrl H to display hidden files and .trash appears, PCmanFM does not appear to be able to delete that file, but Nautilus can and does.

So.... how do I add Nautilus to the menus?

Thanks

---

### Post by mcduck on 2010-07-09
First, Imagemagick is a set of command-line tools, so you definitely don't need Nautilus or any other program to use it.

Anyway, here's a thread about editing LXDE's menus: [http://ubuntuforums.org/showthread.php?t=896355]("http://ubuntuforums.org/showthread.php?t=896355")

Just make sure to use "nautilus --no-desktop" as the command, as Nautilus also handles the desktop background, menus etc. in Gnome. The "--no-desktop" option tels it to just open the fie manager window instead of starting to draw the desktop for you.

---

### Post by avantgardaclue on 2010-07-09
Thanks for your help, for some reason couldn't get it to work in the menus but have a shortcut/link on the desktop which will do for the time being or until i can be bothered to try again!!

As for imagemagick, i am sufficiently unskilled to be able to do anything with the command line so absolutely need to depend on Nautilus scripts, especially if I am doing something to a whole folder of images.

For instance the following script reduces image down to 800 pix wide, puts border round the image and copyright message in bottom right corner and renames file with today's date.

Place script in .gnome2/nautilus-scripts, ensure file can be launched as prog and right button click on all the images you want!

Well works for me!

> #!/bin/bash
## This takes one argument: the file name, with wildcards allowed.  

## A datestamp is added to all saved files.

## It creates a border around the image, and puts the copyright symbol
## at the bottom right.
##
## Example use, assuming the file is called "resize_800".
## resize_800 *.jpg
##
for i  
do
  output_filetype=jpg
  datestamp=$(date +%d%b%Y)
  output_filename_base=${i%.*}
  output_filename=$output_filename_base"_"$datestamp"."$output_filetype
  convert $i -resize 798 -quality 90 -unsharp ".1x1+0.8+0" -fill white \
    -gravity SouthEast \
    -annotate +6+6 ' © 2010 McDuck  ' \
    +raise 4x4 -bordercolor black -border 1x1  $output_filename
done
echo "All done."

---

### Post by mcduck on 2010-07-09
sure, if you want to be able to select only certain images in a directory and use the script to them, then Nautilus scripts approach is a good one.

But I usually just need to run the same script for all the images in the directory, so I can easily just use normal shell scripts to do. So I have a bunch of scripts that do that stored in ~/bin, and when I need to execute one of them I open terminal in the directory where the images I want to process are located and run the script I want.

So, you can use such scripts easily without Nautilus as long as you operate on all images in the current directory, or give the script names of all files you want to work on.

By the way, if you want even more graphical way of doing similar stuff with large amounts of images, you might want to try [Phatch]("http://photobatch.stani.be/"). While it of course doesn't have *all* the options and flexibility of Imagemagick, it does a pretty good job at providing most commonly needed options and allowing for batch processing of images fully in GUI.

---


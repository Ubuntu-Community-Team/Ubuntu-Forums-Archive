---
title: "Conky-colors: photord zooms in (photorandom)"
date: 2010-09-18
forum: General Help
---

### Post by Userata on 2010-09-18
Hello, my first post here after a long time following topics.

A few days ago i tried conky and lately conky-colors, which is alot easier to handle. I have a problem with photord (photorandom). It isnt random at all. What it does do is zooming in. So instead of picking the next photo in the folder, it zooms in the current active photo. How can i fix this? The normal version (photo) is working fine. The code:

> #############
# - PHOTO - #
#############
# For a working photo widget you need to specify a file or directory in conkyPhoto or conkyPhotoRandom script in ~/.conkycolors/bin/ folder
${voffset 4}${font Droid Sans:style=Bold:size=8}PHOTO $stippled_hr${font}
${execi 240 ~/.conkycolors/bin/conkyPhotoRandom}${image /tmp/conkyPhoto.png -s 175x120 -p 4,270}${voffset 114}

I edited the path in ./conkycolors/bin/conkyPhotoRandom and placed a few photos in a directory i made called ConkyPhotos:

> #!/bin/bash
#
# Photo in conky
# by helmuthdu and paulvictor
source="/home/MyName/Pictures/ConkyPhotos/"
photo=/tmp/conkyPhoto.png
#choose your theme: 1,2 or 3
theme=1

cd $source
number=$(ls -R | wc -l)
random=$RANDOM
random=${random}%${number}
lines=`echo ${random} + 2 | bc`
filename=`ls | head -n $lines | tail -n 1`

	cp $filename $photo

	width=`identify -format %w $photo`
	height=`identify -format %h $photo`
	picture_aspect=`echo $width - $height | bc`
	v_aligh=`echo $height / "$height / 5" | bc`

	if [ $picture_aspect -gt "0" ]; then
		convert $photo  -thumbnail 280x175 $photo
		convert $photo -gravity center -crop 175x125+0+0 +repage $photo
	else
		convert $photo  -thumbnail 175x280 $photo
		convert $photo -crop 175x125+0+$v_aligh +repage $photo
	fi

	if [ $theme = "1" ]; then
	# Theme 1
		convert $photo\
			-bordercolor snow -border 4.5\
			-bordercolor gray55 -border 1 \
			-background  black  \( +clone -shadow 40x2+1+1 \) +swap \
			-background  none -flatten \
		$photo
	elif [ $theme = "2" ]; then
	# Theme 2
		convert -page +2+2 $photo\
			-bordercolor gray10 -border 1\
			-background  black  \( +clone -shadow 40x4+2+2 \) +swap \
			-background  none -flatten \
		$photo
	elif [ $theme = "3" ]; then
	# Theme 3
		convert $photo \
			-bordercolor snow -border 4.5\
			-bordercolor gray55 -border 1 \
			-bordercolor none  -background  none \
			\( -clone 0 -rotate `convert null: -format '%[fx:rand()*30-15]' info:` \) \
			\( -clone 0 -rotate `convert null: -format '%[fx:rand()*30-15]' info:` \) \
			\( -clone 0 -rotate `convert null: -format '%[fx:rand()*30-15]' info:` \) \
			-delete 0 -border 175x125 -gravity center \
			-crop 300x185+0+0 +repage -flatten -trim +repage \
			-background black \( +clone -shadow 40x2+1+1 \) +swap \
			-background none  -flatten \
		$photo
	fi

exit 0


Why is it zooming in instead of going to the next one? Btw i tried googling the problem, but with no result. I did came across [this page](http://gnome-look.org/content/show.php?content=92328&forumpage=38&PHPSESSID=f5d6397c56ec77f356fefbcaa1c4e2aa) on Gnome-look.org. The creator of conky-colors said that he also experienced problems with photord (dont know if its about zooming in) and suggested to check if Imagemagick and bc are installed. I checked and those programs were already installed. So thats not the problem here.

---


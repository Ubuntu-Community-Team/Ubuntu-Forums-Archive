---
title: "Conky Comic of the day?"
date: 2010-12-17
forum: General Help
---

### Post by kyle6513 on 2010-12-17
G'day everyone, first off, if this is in the wrong place, someone please move it :)
Now, my main problem is I want to embed an image into conky that will be updated based on a page, something like [this]("http://www.collectedcurios.com/sequentialart.php").

Does anyone know how to do this? I assume something along the lines of a python script which downloads the comic of the day, saves it as a specific file that conky is pointed towards which I would be fine in doing, except thats a little too advanced for me. If anyone could help me in writing a script to do such a thing, then I'd be forever grateful :)

so to cut a long story short, I want to have the newest comic on my desktop.

Thanks,
kyle6513.

---

### Post by TeoBigusGeekus on 2010-12-17
Create a folder in your /home partition called comic_script.
Create a new empty text file, fill it with this code
```
#!/bin/bash
wget -O f1 http://www.collectedcurios.com/sequentialart.php
grep strip f1>f2
sed -i 's/"/\n/g' f2
grep jpg f2>f3
sed -i "1s/^/http\:\/\/www\.collectedcurios\.com\//" f3
i=$(sed -n '1p' f3)
wget -O ./comic.jpg $i
```
and save it as comic in the comic_script folder.
Open terminal and make the script executable:
```
chmod +x ~/comic_script/comic
```

Create another empty text file in the comic_script folder, fill it with this
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 1100 300
#maximum_width 170

override_utf8_locale yes

# Draw shades?
draw_shades yes

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
#font freesans -12
xftfont ubuntu:pixelsize=12
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color EBCA92

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

# stuff after 'TEXT' will be formatted on screen

TEXT
${execi 86400 ~/comic_script/comic} 
${image ~/comic_script/comic.jpg -p 200,0 -s 900x290}
```
and save it as .conkyrc.
The script searches for another comic every 24h(60*60*24=86400).
I've positioned it on the bottom center of my screen and have kept its original size - these are nice settings for my 1280x1024 display, experiment with them if they don't fit you.
Finally, run
```
conky -c ~/comic_script/.conkyrc
```
and you're done.

---

### Post by stinkeye on 2010-12-17
That's really good TeoBigusGeekus. Well done.
Now I've buttered you up, would it be possible for you to write a script to download an image from this website: [http://www.seabreeze.com.au/graphs/]("http://www.seabreeze.com.au/graphs/")
The image I want is the one attached.(The first image on the page)

I've actually already got it displaying in my conky but I use about 4 amateur
scripts to get it, because I just googled for sed and grep one liners.
The number part of the image address changes every 15 minutes or so.
 [http://www.seabreeze.com.au/images/forecast/0/PERT/rgg.png?n=](http://www.seabreeze.com.au/images/forecast/0/PERT/rgg.png?n=)[COLOR="Magenta"]1292608393000[/COLOR]
Thanks.

---

### Post by TeoBigusGeekus on 2010-12-17
Sure thing my friend.
Create folder stinkeye in your /home partition.
Create a text file in there with the following script
```
#!/bin/bash
wget -O f1 http://www.seabreeze.com.au/graphs/
grep rgg.png f1>f2
sed -i 's/"/\n/g' f2
sed -i 's/?/\n/g' f2
grep .png f2>f3
sed -i "1s/^/http\:\/\/www\.seabreeze\.com\.au/" f3
i=$(sed -n '1p' f3)
wget -O ./stinkeye.png $i
```
and save it as stinkeye.
Make it executable
```
chmod +x ~/stinkeye/stinkeye
```
Create another file in there and save it as .conkyrc:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 1100 300
#maximum_width 170

override_utf8_locale yes

# Draw shades?
draw_shades yes

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
#font freesans -12
xftfont ubuntu:pixelsize=12
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color EBCA92

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

# stuff after 'TEXT' will be formatted on screen

TEXT
${execi 900 ~/stinkeye/stinkeye} 
${image ~/stinkeye/stinkeye.png -p 350,0 -s 596x264}
```
Again the image is (almost) centered at the bottom of my screen and I have to admit that it looks a bit like crap with my wallpaper, but with a darker one I guess it will be ok. I again used the image's original size. The script updates every 900secs or 15 mins.

---

### Post by stinkeye on 2010-12-17
Thanks TeoBigusGeekus! :KS
Your script has now replaced 6 lines of dodgy code in my conky.
Much appreciated.

---

### Post by TeoBigusGeekus on 2010-12-17
You're welcome mate.
And it sure looks gorgeous on your desktop.:P

---

### Post by kyle6513 on 2010-12-17
wow thanks so much TeoBigusGeekus :)
wonder if theres a way to +rep someone...

---

### Post by TeoBigusGeekus on 2010-12-18
> **kyle6513 said:**
> wow thanks so much TeoBigusGeekus :)
wonder if theres a way to +rep someone...

A cheque would be fine...;)

---


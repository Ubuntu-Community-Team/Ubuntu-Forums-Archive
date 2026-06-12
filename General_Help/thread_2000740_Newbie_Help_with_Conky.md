---
title: "Newbie Help with Conky"
date: 2012-06-10
forum: General Help
---

### Post by Quarkrad on 2012-06-10
Apologies if this is not the right part of the forum for this question.  I've just started to play with conky and I'm going to enjoy it.  I'm starting with vinDSLs script and got part of it on my screen.  However, I'm struggling with the **openlogos** command you see in a lot of conky scripts.  I'm guessing this command points to somewhere - that I have yet to find out.  In my screenshot below (1) you can see I have a large V instead of the Ubuntu logo that is on the VinDSL script (2 below).  What am I am I missing?

VinDSL's script:

## Uncomment for hard-coded ID (static)
${voffset -33}${font OpenLogos:size=103}${color2}v${font}${voffset -76}${goto 179}${font /home/dad/.dbusUbuntuTitleBold:size=19.6}${color4}1${offset 1}2${offset 1}.${offset 0}0${offset 0}4${font}
####

---

### Post by Quarkrad on 2012-06-10
Sorry - my attachments didn't get through on the first post.

---

### Post by stinkeye on 2012-06-10
The **${font OpenLogos:size=103}${color2}v** command is calling an openlogo font represented by "v".

You need to install the [**_[COLOR="DarkRed"]openlogos[/COLOR]_**]("http://www.dafont.com/openlogos.font") font.
Unzip the download and place **openlogos.ttf** in **~/.fonts**

Install **gnome-specimen** and you can see what symbols other letters represent.
```
sudo apt-get install gnome-specimen
```

---

### Post by Quarkrad on 2012-06-10
Brilliant - many thanks.

---

### Post by Quarkrad on 2012-06-11
I have another question - probably more as I learn/play!  Is this the right place in the forum or is there a specific 'conky' thread I should go to?  There doesn't appear to be a 'conky' specific area.  Using the same VinDSL basic script I cannot resolve a Calendar probelm.  pic1 below shows what I get using this code:

[B]##################################
##             TIME             ##
##################################
${voffset 4}${font DroidSans:bold:size=8}${color4}TIME${offset 8}${color8}${voffset -2}${hr 2}${font}
${voffset -4}${font RadioSpace:size=32}${color3}${if_match ${time %l}<=9}${alignc 7}${time %l:%M%p}${else}${if_match ${time %l}>=10}${alignc -1}${time %l:%M%p}${endif}${endif}${font}
##################################
##      CALENDAR (5-Line)       ##
##################################
#next line defines DATE and line across page
${voffset 2}${font DroidSans:bold:size=8}${color4}DATE${offset 8}${color8}${voffset -2}${hr 2}${font}
#next line defines the DAY in the box and the colour
${voffset 18}${font DroidSansMono:size=7.55}${color2}${alignc 115}${time %A}${font}
#next line defines the date number in the box
${voffset -4}${font DroidSansFallback:bold:size=18}${if_match ${time %e}<=9}${color5}${alignc 65}${time %e}${font}${else}${if_match ${time %e}>=10}${color5}${alignc 115}${time %e}${endif}${endif}${font}
#next line defines the month and colour in the box
${voffset 0}${font DroidSansMono:size=7.55}${color3}${alignc 115}${time %B}${font}
#next line defines the year colour in the box
${voffset 0}${font DroidSansMono:size=7.6}${color9}${alignc 115}${time %Y}${font}
#next line defines the actual box
${voffset -80}${font CutOutsFor3DFX:size=67}${color8}${alignc 199}2${font}
####[/B]

(I've added some comments to the code so I know what they do.  I have played with some of the numbers to positon the box/text in the position I want on my screen).

When I add the following lines of code I get pic2.

[B]## Uncomment for Conky 1.8.1 (use mono fonts only)
${voffset -64}${offset 100}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}[/B]

The Su, Mo, to Fr, Sa are in a good position but no matter what I've done up to now I cannot move the numbers field so they line up, to the right, underneath the Su, Mo, Tu, We, Th, Fr, Sa set.  They are stuck under pic1.

---

### Post by stinkeye on 2012-06-11
There is a specific thread that deals with the vindsl conky.
[**_[COLOR="DarkRed"]HOWTO: VinDSL Conky Script[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1771033")

and a general conky thread...
[**_[COLOR="darkred"]Post your .conkyrc files w/ screenshots[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=281865&page=2005")

The vindsl conky looks good but can be unnecessarily complicated and hard to work with if you want to change things.

The calendar command is tricky.
Because it outputs multiple lines, when you precede it with an offset
it only offsets the first line which puts the whole calendar out of whack.
If you want to move the calendar use the other one in the config.
eg 
```
## **Uncomment for Conky 1.8.0** (use mono fonts only)
# ${voffset -68}${font DroidSansMono:size=7.55}${color3}${execpi 60 VinDSL_Cal_9=`date +%-d`; cal -h | sed -e 's/\r//g' -e 's/^/ /g' -e '1d' -e s/^/"\$\{[COLOR="Magenta"]offset 100[/COLOR]"\}/ -e 's/\<'"$VinDSL_Cal_9"'\>/${color4}&${color3}/'}
```
where the [COLOR="magenta"]offset[/COLOR] is built in to the cal command. Scroll the code box to see the [COLOR="Magenta"]highlighted[/COLOR] section.

---

### Post by Quarkrad on 2012-06-11
That did it, many many thanks.  If I should post on **HOWTO: VinDSL Conky Script** - and there is something else I need help on before I move on to the weather section, will you be able to help me there?

---

### Post by stinkeye on 2012-06-11
> **Quarkrad said:**
> That did it, many many thanks.  If I should post on **HOWTO: VinDSL Conky Script** - and there is something else I need help on before I move on to the weather section, will you be able to help me there? 
If it's specific to the VinDSL Conky, 42dorian will answer your question...or abuse you for not reading the HOWTO. :shock:
 
More than happy to help if you post in the 
**Post your .conkyrc files w/ screenshots** thread.
If I can't help there's always others who frequent that thread.

---


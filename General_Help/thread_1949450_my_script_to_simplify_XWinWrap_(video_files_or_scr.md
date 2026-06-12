---
title: "my script to simplify XWinWrap (video files or screensavers as your wallpaper)"
date: 2012-03-30
forum: General Help
---

### Post by HiImTye on 2012-03-30
I made a script to make choosing a video or screensaver to use as your wallpaper in XWinWrap easier.

note: you will need to have [these]("apt://xscreensaver,xscreensaver-gl,xscreensaver-gl-extra,xscreensaver-data-extra,xscreensaver-screensaver-bsod,electricsheep,mplayer") installed for this to work right. you also need [XWinWrap]("http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap") (it makes it actually work)

it's pretty simple, you can specify a screensaver or video file to use when you launch it via:
```
XWinWrap.sh 16
```uses the 16th screensaver. screensavers are in alphabetical order from 1-61
```
XWinWrap.sh 0
```uses a random screensaver
```
XWinWrap.sh V
```opens up the file dialog to select a video
```
XWinWrap.sh V "$HOME/Videos/MyVideoFile.avi"
```uses the video specified
```
 XWinWrap.sh
```asks you what you want to use, including random (the default option) or a video file
note: when trying to play a video, if there are spaces in the file name it seems to fail, I'm not really sure at this point how to fix that other than maybe making a symlink. this same problem occurs when you use the file selection dialog so it isn't just 'I broke it'

if you open it while xwinwrap is already running then it will act as a toggle (and close it)

you can edit it to add your own or whatever but I spent some time going through and finding ones that look nice as wallpapers. anyway, here it is

XWinWrap.sh
```
#!/bin/bash

#if xwinwrap is running then we launched this to close it, so if it is then let's
#close it and exit
 if ps -e | grep xwinwrap
 then
  killall xwinwrap
  sleep 1
  exit
 fi

#variables are fun
 TEXT="Background"
 MOVIE="Movie"
 ESHEEP="electricsheep"
 RAND1="Random"
  OPT1="atlantis"
  OPT2="atunnel"
  OPT3="blinkbox"
  OPT4="blocktube"
  OPT5="bouncingcow"
  OPT6="boxfit"
  OPT7="bsod"
  OPT8="bubble3d"
  OPT9="bumps"
 OPT10="cage"
 OPT11="carousel"
 OPT12="cube21"
 OPT13="cubenetic"
 OPT14="cubicgrid"
 OPT15="cwaves"
 OPT16="dangerball"
 OPT17="electricsheep"
 OPT18="fiberlamp"
 OPT19="fireworkx"
 OPT20="flipflop"
 OPT21="fliptext"
 OPT22="flow"
 OPT23="flurry"
 OPT24="flyingtoasters"
 OPT25="gflux"
 OPT26="glcells"
 OPT27="gleidescope"
 OPT28="glknots"
 OPT29="glmatrix"
 OPT30="glschool"
 OPT31="glslideshow"
 OPT32="glsnake"
 OPT33="hypertorus"
 OPT34="hypnowheel"
 OPT35="interaggregate"
 OPT36="intermomentary"
 OPT37="jigglypuff"
 OPT38="jigsaw"
 OPT39="julia"
 OPT40="lament"
 OPT41="lockward"
 OPT42="metaballs"
 OPT43="moebiusgears"
 OPT44="molecule"
 OPT45="morph3d"
 OPT46="noof"
 OPT47="phosphor"
 OPT48="photopile"
 OPT49="pinion"
 OPT50="popsquares"
 OPT51="ripples"
 OPT52="skytentacles"
 OPT53="slidescreen"
 OPT54="stonerview"
 OPT55="strange"
 OPT56="substrate"
 OPT57="tangram"
 OPT58="whirlwindwarp"
 OPT59="wormhole"
 OPT60="xflame"
 OPT61="xrayswarm"

#pick your poison
#if called with a number then it will use that option, i.e. if it is called with:
# XWinWrap.sh 17
#it will use OPT17 from the list above.
#to specify a movie use "V" for Video, optionally, specify a file after it
#example:
# XWinWrap.sh V "$HOME/Videos/MyMovieFile.avi"
#note, you probably don't need to use quotation marks but it's always nice just to be sure
if [ ! -z "$1" ]; then
 if [ "$1" = "0" ]; then
   SEL=$RAND1
 elif [ "$1" = "V" ]; then
   SEL=$MOVIE
   MOVIEFILE=$2
 elif [ "$1" \> "0"]; then
   eval SEL=\$OPT$1
 fi
else
 SEL="$(zenity --list --radiolist --text $TEXT --column "" --column "Choose" TRUE $RAND1 FALSE $MOVIE FALSE $OPT1 FALSE $OPT2 FALSE $OPT3 FALSE $OPT4 FALSE "$OPT5" FALSE "$OPT6" FALSE "$OPT7" FALSE "$OPT8" FALSE "$OPT9" FALSE "$OPT10" FALSE "$OPT11" FALSE "$OPT12" FALSE "$OPT13" FALSE "$OPT14" FALSE "$OPT15" FALSE "$OPT16" FALSE "$OPT17" FALSE "$OPT18" FALSE "$OPT19" FALSE "$OPT20" FALSE "$OPT21" FALSE "$OPT22" FALSE "$OPT23" FALSE "$OPT24" FALSE "$OPT25" FALSE "$OPT26" FALSE "$OPT27" FALSE "$OPT28" FALSE "$OPT29" FALSE "$OPT30" FALSE "$OPT31" FALSE "$OPT32" FALSE "$OPT33" FALSE "$OPT34" FALSE "$OPT35" FALSE "$OPT36" FALSE "$OPT37" FALSE "$OPT38" FALSE "$OPT39" FALSE "$OPT40" FALSE "$OPT41" FALSE "$OPT42" FALSE "$OPT43" FALSE "$OPT44" FALSE "$OPT45" FALSE "$OPT46" FALSE "$OPT47" FALSE "$OPT48" FALSE "$OPT49" FALSE "$OPT50" FALSE "$OPT51" FALSE "$OPT52" FALSE "$OPT53" FALSE "$OPT54" FALSE "$OPT55" FALSE "$OPT56" FALSE "$OPT57" FALSE "$OPT58" FALSE "$OPT59" FALSE "$OPT60" FALSE "$OPT61")"
fi

#if it's random, generate a random number and then select one based on that number
 if [ "$SEL" = "$RAND1" ]; then
  RAND2=$((RANDOM%61+1))
  eval SEL=\$OPT$RAND2
 fi

#exit if done, otherwise, define options for screensavers that need it, or, open up
#a file selection dialog to choose a movie
 if [ "$SEL" = "" ]; then
   sleep 1
   exit
 elif [ "$SEL" = "$MOVIE" ]; then
  if [ -z "$MOVIEFILE" ]; then
   MOVIEFILE="$(zenity --file-selection --filename $HOME/Videos/)"
  fi
  elif [ "$SEL" = "$OPT2" ]; then
   OPTIONS="-light"
 elif [ "$SEL" = "$OPT3" ]; then
   OPTIONS="-boxsize 4 -dissolve"
 elif [ "$SEL" = "$OPT7" ]; then
   OPTIONS="-atari -bsd -sparclinux"
 elif [ "$SEL" = "$OPT11" ]; then
   OPTIONS="-count 10 -no-titles"
 elif [ "$SEL" = "$OPT14" ]; then
   OPTIONS="-no-bigdots"
 elif [ "$SEL" = "$OPT17" ]; then
   OPTIONS="--root 1 2> /dev/null"
 elif [ "$SEL" = "$OPT19" ]; then
   OPTIONS="-no-flash -no-glow"
 elif [ "$SEL" = "$OPT20" ]; then
   OPTIONS="-texture"
 elif [ "$SEL" = "$OPT22" ]; then
   OPTIONS="-no-box"
 elif [ "$SEL" = "$OPT25" ]; then
   OPTIONS="-speed 0.05"
 elif [ "$SEL" = "$OPT30" ]; then
   OPTIONS="-drawgoal"
 elif [ "$SEL" = "$OPT34" ]; then
   OPTIONS="-wander -symmetric"
 elif [ "$SEL" = "$OPT36" ]; then
   OPTIONS="-num-discs 400"
 elif [ "$SEL" = "$OPT37" ]; then
   OPTIONS="-no-random"
 elif [ "$SEL" = "$OPT38" ]; then
   OPTIONS="-complexity 1.5227 -resolution 200"
 elif [ "$SEL" = "$OPT47" ]; then
   OPTIONS="-scale 4"
 elif [ "$SEL" = "$OPT48" ]; then
   OPTIONS="-count 11 -duration 2"
 elif [ "$SEL" = "$OPT49" ]; then
   OPTIONS="-spin 1.8773"
 elif [ "$SEL" = "$OPT51" ]; then
   OPTIONS="-rate 1 -fluidity 6"
 elif [ "$SEL" = "$OPT52" ]; then
   OPTIONS="-count 11 -length 13.3788 -thickness 0.5826 -flexibility 0.5091 -wiggliness 0.2364 -no-texture"
 elif [ "$SEL" = "$OPT53" ]; then
   OPTIONS="-grid-size 75"
 elif [ "$SEL" = "$OPT57" ]; then
   OPTIONS="-no-labels"
 elif [ "$SEL" = "$OPT59" ]; then
   OPTIONS="-zspeed 22 -stars 100"
 elif [ "$SEL" = "$OPT60" ]; then
   OPTIONS="-no-bloom"
 fi

#Meat n pooptatoes
 if [ "$SEL" = "$MOVIE" ]; then
   xwinwrap -b -fs -sp -nf -ov -- mplayer -wid WID -quiet $MOVIEFILE
 elif [ "$SEL" = "$OPT17" ]; then
   xwinwrap -b -fs -sp -nf -ov -- electricsheep -window-id WID $OPTIONS
 else
   xwinwrap -b -fs -sp -nf -ov -- /usr/lib/xscreensaver/$SEL -window-id WID -root $OPTIONS
 fi
sleep 1
exit
```

---

### Post by HiImTye on 2012-03-30
I made a preview video in 1080p, in case anyone is interested in how it actually looks
[http://www.youtube.com/watch?v=8lSPNijXSME](http://www.youtube.com/watch?v=8lSPNijXSME)
as you can see, desktop icons disappear but that is a small sacrafice I think

---


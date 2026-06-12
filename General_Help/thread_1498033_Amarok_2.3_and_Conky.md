---
title: "Amarok 2.3 and Conky"
date: 2010-05-31
forum: General Help
---

### Post by chowanec on 2010-05-31
Hey all -- I got desperate myself and scoured the web for some more information on this. I wanted to get my coverart and relevant now-playing information from Amarok into Conky. 

That said, I found some shell scripts from [http://www.larryni.me.uk/blog/2009/10/18/display-amarok-album-art-in-conky/]("http://www.larryni.me.uk/blog/2009/10/18/display-amarok-album-art-in-conky/") that started me going -- thing is, these scripts only work for 1.4 (i.e. not Amarok 2.0+)

So -- where to go from here:
[LIST=1]
[*]I have a folder for all my scripts ~/Scripts/conky
[*]Download the attached file
[*]edit askamarok
[**]I force lowercase as much as possible on my desktop for aesthetic reasons.  If you want standard upper/lower, remove the | tr '[A-Z]' '[a-z]' 
[*]edit getcover
[**]Modify the tempdir variable to set your own path to the scripts
[*]edit nocover.png if you want a different "no artwork" image
[*]edit conkyCover
[*]edit conkyCover2
[**]This will place it on the upper right part of your screen.  Modify away.
[*]I went and chmod 777 getcover, askamarok, nocover.png and (after it got created) cover.png
[**]I realize this will freak people out.  You may not need to do this, but I'm still new enough to linux that it was the only solution I could think of.  Otherwise I got errors when the scripts ran.
[/LIST]

It's not perfect, but it works well enough for me.  Here's what it looks like in action.

---

### Post by fireandfuel on 2010-06-18
Your scripts doesn't run with amarok 2.3, because it uses dbus instead of dcop.

This  is the updated getcover script:
```
#!/bin/bash
# get Amarok cover art  of current track and transform into an album stack
# copypasta from  http://www.imagemagick.org/Usage/thumbnails/#polaroid
# thanks to  eightmillion for completely rewriting the script
# http://ubuntuforums.org/showpost.php?p=8117609&postcount=9846

# edited by fireandfuel                   
# requires: amarok >= 2.0, dbus, libqt4-dbus, perl

# Temp directory must be full path.
tempdir="$HOME/.conky/"
tempfile="${tempdir}nowplaying"

[ -d "$tempdir" ] || mkdir -p "$tempdir"  #test if $tempdir exists, if  not create it.
[ -e "$tempfile" ] || touch "$tempfile"

cover="$(qdbus org.kde.amarok /Player GetMetadata | grep arturl: | cut -c 16- | perl -MURI::Escape -lne 'print uri_unescape($_)')"
if  [[ -z "$cover" ]]; then #test if $cover was set, if not copy nocover.png to cover.png .

    hash=0

     read oldhash < "$tempfile"

    cover="${tempdir}nocover.png"

     if [ "$oldhash" == "$hash" ];then
        :
    else
         cp "${cover}" "${tempdir}cover.png"

        echo 0 >  "$tempfile"
    fi
else

    hash=$(echo "$cover" | md5sum |  cut -d" " -f 1) #Generate hash for current song.

    read  oldhash < "$tempfile"

    if [ "$oldhash" == "$hash" ];then
             :
    else
        convert "${cover}" -resize 100x100  "${tempdir}cover.png"
    
            echo $hash > "$tempfile"
     fi
    
fi
exit
```If you want a larger cover in conky, you 'll edit the line "convert ${cover} ..." and resize your nocover picture.

PS: A script to get the  metadata at amarok2.X:  [http://wiki.ubuntuusers.de/_attachment?target=Conky%2Famarok-skript.txt]("http://wiki.ubuntuusers.de/_attachment?target=Conky%2Famarok-skript.txt")

PPS: Sry, English is not my native language. :p

UPDATE: Sry, I forgot to convert the URI to a path - now that's fixed!

---


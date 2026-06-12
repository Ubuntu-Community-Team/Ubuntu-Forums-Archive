---
title: "sed / awk substitution help"
date: 2010-10-01
forum: General Help
---

### Post by fatbastard spice on 2010-10-01
I'm currently ripping all my cds to flac. The issue i'm hitting is when i want rhythmbox to recognise the flac as a replacement of the mp3, which it quite reasonably doesn't (reason for this is to keep playcounts and ratings which drive my playlists). So i've been manually hacking rhythmbox's xml file to replace the mp3 extension with flac for each album i rip in a text editor. I'm sure there's a way to do this with a single sed/awk type command, but so far it's defeated me.

So it needs to substitute flac for mp3 if the appropriate album string is present in the line

So say for mp3s in the folder 2002 - Mr. Forky the before and after are:

Before
    <location>file:///media/audio/albums/Mr.%20Forky/2002%20-%20Mr.%20Forky/07%20-%2010%20Years.mp3</location>

After
    <location>file:///media/audio/albums/Mr.%20Forky/2002%20-%20Mr.%20Forky/07%20-%2010%20Years.flac</location>

Anyone able to help out?

---

### Post by DaithiF on 2010-10-03
Hi,
the complication here is the urlencoding of the album names in the xml, so you in order to match an album you need to urlencode your album name first.  (for example replacing spaces with %20).

heres an awk script that might give you a start:
```
awk -v album="2002 - Mr. Forky" '      
BEGIN { gsub(" ", "%20", album ) }
{ if (index($0, album) > 0) { gsub(".mp3", ".flac", $0); count++ ; }}
{ print }
END { printf "%d substitutions made", count > "/dev/stderr" }
' file.xml
```
as you can see the only character it does urlencoding for is the space character.  Depending on your input data you may need to do more substitutions here to cater for other characters.  Or you could look at a more comprehensive urlencoding solution (e.g. [http://www.shelldorado.com/scripts/cmds/urlencode](http://www.shelldorado.com/scripts/cmds/urlencode))

This outputs to the screen, to actually make changes redirect output to a (new) file and then rename it if happy with the outcome.

A (somewhat) complete solution, assuming you have a file listing the converted album names might look something like this:

```
while read album
do
echo "Processing $album..."
awk -v album="$album" '      
BEGIN { gsub(" ", "%20", album ) }
{ if (index($0, album) > 0) { gsub(".mp3", ".flac", $0); count++ ; }}
{ print }
END { printf "%d substitutions made", count > "/dev/stderr" }
' file.xml > temp.xml && mv {temp,file}.xml
done < filewithalbumnames

```

---


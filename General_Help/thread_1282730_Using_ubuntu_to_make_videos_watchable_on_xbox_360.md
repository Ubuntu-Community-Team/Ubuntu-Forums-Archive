---
title: "Using ubuntu to make videos watchable on xbox 360"
date: 2009-10-04
forum: General Help
---

### Post by sponsoredwalk on 2009-10-04
Hello, I have over 200 .flv files downloaded from youtube and I would like to put them onto a usb to watch on an xbox 360 so my little brother can learn a lot of college level material before he finishes high school (which based on the quality of these lectures i guarantee [www.khanacademy.org](www.khanacademy.org)) 

But I have problems. I am pretty sure there's no way to watch flv on an xbox 360 unless some amazing person has figured it out. So perhaps there is a way to get mp4 files to work but before i go ahead and download 200 files AGAIN from youtube (with a bigger size than .flv) I am wondering if there is a way to make it work, from ubuntu. All my googling resulted in people using windows software to stream/convert and I don't understand any of it. 

Would anybody be able to help me and my brother, I think it's really important he learns this stuff right, his school (my old one) isn't fit for the task...

---

### Post by Jose Catre-Vandis on 2009-10-04
Yep, encode them all to a suitable container using ffmpeg

For example, to convert from flv to avi:
```
ffmpeg -i input.flv output.avi
```

This is a very simple example, there are loads of options you can add to tweak and improve your encode, and you may need to install additional codecs and libraries to get everything working.

A simple batch script would take care of all you files in one hit :)

---

### Post by mtate5000 on 2009-10-04
If you're looking for something more gui based, Handbrake is a great program for ripping dvds and video encoding. You need to have vlc installed, as handbrake uses vlc's codec library and dvd decryption. If vlc can play it (which I haven't come across a format that it couldn't) then handbrake can rip/encode it.

---

### Post by sponsoredwalk on 2009-10-04
I really like the idea of a batch script (whatever it is) taking care of all the files in one go!!! How would I do that? Maybe if I give you some information you could give me an exact terminal sentence to copy and paste into terminal.

Say I put all the files into a folder located at /home/zxcv/dvd/ and had them named like so - 01.flv 02.flv 03.flv all the way to 50 (we'll do fifty at a time or is that too much? Whatever you suggest.) maybe the location could go to /home/zxcv/finish/ or the original folder, whatever.

Now if .flv is not a good idea to use as the source file I can re-download the youtube video's in .mp4 format - but if it's at all possible to avoid please do so! There's a lot of them!!

From the xbox site it says that these are the compatible kinds of files;

[http://support.xbox.com/support/en/us/xbox/search.aspx?keyword=wmv](http://support.xbox.com/support/en/us/xbox/search.aspx?keyword=wmv)

[http://support.xbox.com/support/en/us/xbox360/gamesandmedia/movies/videofaq/viewvideoplaybackfaq.aspx](http://support.xbox.com/support/en/us/xbox360/gamesandmedia/movies/videofaq/viewvideoplaybackfaq.aspx)

> The Xbox 360 console supports the following for AVI:

    * File extensions: .avi, .divx
    * Containers: AVI
    * Video profiles: MPEG-4 Part 2 (Simple Profile and Advanced Simple Profile)
    * Video bit rate: 5 Mbps with resolutions of 1280 × 720 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: Dolby® Digital (2 channel and 5.1 channel), MP3             

These are the parameters that need to be followed as I put some files onto a usb before and they didn't play while others did... I really haven't the first clue what a codec is either, so I'm really shooting in the dark anytime I do anything, I can't configure the parameters myself - nor understand them :(

Seriously, if this is possible it is just amazing, it will really do my little brother more than the world of good! :guitar:

---

### Post by Jose Catre-Vandis on 2009-10-05
The script should be fairly straight forward. I use something like this to deal with batches of files:
```

#!/bin/bash
# flvconvert.sh

####LOOP FOR EACH SELECTED FILE#######

FILES="*.flv"

for f in $FILES

do

ffmpeg -i $f $f.avi

done
```

Make the script executable and run it from the directory containing flv files

---


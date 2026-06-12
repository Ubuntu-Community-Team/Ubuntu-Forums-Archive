---
title: "How do I print a playlist?"
date: 2010-10-22
forum: General Help
---

### Post by Preserved Killick on 2010-10-22
Hi folks.  I have a playlist (.m3u) of nearly 900 songs.  Programs like Rhythmbox can show me the entire playlist-- Title, Artist, Album, Time for each track.  But I can't see how to print it out.  

I know printing is old-fashioned, but when I'm updating the playlist, it would be easier to have a printed paper to refer to as I add to it.  

Opening the playlist as a text file works, but it's loaded with distractions (e.g. absolute path to the file) from the information I really want-- title, artist.

Anyone know how to do this?

Thanks,

Killick

---

### Post by cgroza on 2010-10-22
You could search for a script or program that deletes the lines that contain "/home/" and dumps the new version into another one. I can make one in python I think. Just back up your playlist.

I assume all your music is in the home directory and the paths in that file have /home/ in their lines.

---

### Post by ivarn on 2010-10-22
Winamp (under wine) can convert it to a html text document.
But if you don't like using Wine, idk.

---

### Post by cgroza on 2010-10-22
I have the script done. It is done in a hurry so if you give a bad path it will crash. If you give a good one it will run and it will eliminate all the lines that contain /home/ in them. 

Is your music some place else? If no here is your script.

First you must mark it as executable. Double click it and go for run in terminal.

---

### Post by Preserved Killick on 2010-10-22
The script idea is a good one, and thanks for writing one, but the line between the data of interest and the cruft is not a line break.  I know zero about scripting, but I'm going to play with your script to see if I can bend it to my needs.  (Can't learn without trying, can I?)  Here's the first several lines of my playlist file:

&#65279;#CURTRACK 0
#EXTM3U
#EXTINF:159,I Fought The Law
/mnt/disk2/mp3s/Clash/I Fought The Law.mp3
#EXTINF:169,Someday, Someway (Remastered LP Version)
/mnt/disk2/mp3s/marshall_crenshaw/Someday Someway.mp3
#EXTINF:202,Paint It, Black
/mnt/disk2/mp3s/Rolling_Stones/09 - Paint It Black.mp3
#EXTINF:270,Gimme Shelter
/mnt/disk2/mp3s/Rolling_Stones/Gimme Shelter.mp3
#EXTINF:231,Winter Windows (Album)
/mnt/disk2/mp3s/sea_wolf/Winter Windows.mp3
#EXTINF:227,Black Dirt
/mnt/disk2/mp3s/sea_wolf/black_dirt.mp3
#EXTINF:260,Statesboro Blues
/mnt/disk2/mp3s/Allman_Brothers/The Allman Brothers Band at Fillmore East/0 - 00 - The Allman Brothers - Statesboro Blues.mp3

In fact, now that I think about it, some of the data I want to see in a printout is in the file tags.  I generally (but not always) put my songs into an artist folder inside /mnt/disk2/mp3s, but if I don't, the artist info is in the file tags.  

Does anyone know of a Linux program that will print out a playlist?

Thanks,

-- Killick

---

### Post by Preserved Killick on 2010-10-22
OK, I looked at your script and decided alter it to strip out lines starting with #EXTINF instead of /home.  I ran it.

Once that was done, I opened emacs and replaced /mnt/disk2/mp3s/ with nothing.  This left me with very nearly what I wanted.  I have most of the artists names and the track names in a .txt file.

It's not pretty but I can live with this.  I'd still like to just open a music player program, open the playlist and press 'print' but I don't need to wait for that to happen.

Thanks for your help, and your script!

-- Damon

---

### Post by cgroza on 2010-10-23
It left a line between? Explain please. I made it in a hurry so its not perfect.

---

### Post by Preserved Killick on 2010-10-23
Your script would remove lines that start with /home.  Here is what the lines in my playlist look like, with 2 lines per track:

#EXTINF:270,Gimme Shelter
/mnt/disk2/mp3s/Rolling_Stones/Gimme Shelter.mp3

I modified your script to remove the lines beginning #EXTINF.

Then, I used emacs to search replace /mnt/disk2/mp3s/ with nothing.

In this example, I'm left with "Rolling_Stones/Gimme Shelter.mp3"

This works out OK, even though some lines would also have Artist/Album/Track.mp3.

There is probably also a way to remove the lines beginning #EXTINF with emacs, but I don't know what it is.

---

### Post by cgroza on 2010-10-24
That is an easy fix. In that line there is something like :
    ```
if "/home/" in line:
```Replace with: ```
if "/YOUR CRITERIA HERE/" or "THE OTHER CRITERIA" in line:  
```EDIT: I get it now. The ALBUM/ARTIS/TRACK is part of a  line that indicates the path?
You could use the .split to separate it. Tell me if you are still intrested. I could make another one. Don't use the above line. It will leave you with a blank file.

---

### Post by Preserved Killick on 2010-11-28
I just tried installing the Opera browser.  It too cannot play sounds.  I am pretty sure this is a flash issue.  Anyone have an idea how to fix this?

---


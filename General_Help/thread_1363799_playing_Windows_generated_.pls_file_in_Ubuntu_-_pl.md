---
title: "playing Windows generated .pls file in Ubuntu - playing Ubuntu playlist in Windows"
date: 2009-12-24
forum: General Help
---

### Post by iMisspell on 2009-12-24
I have a .pls file with a list of movies in it which was created in Windows (im pretty sure it was created with PowerDVD).

In ubuntu...
Tried to play it with *VLC (v1.0.2)* and nothing, no error messages no movie. Tried it with *mPLayer 2:1.0 rc2*, nothing, no error, no movie.  Tried it with *Totem Movie Player 2.26.1 - GStreamer 0.10.22* received an error:  "**An error occurred - Could not determine type of stream.**".

If i play an avi from the play list directly, they play fine with all media players.

Tried creating a blank file (right-click - Create Document - Empty file) copying over (using Geany) the contents from the windows created file to the empty-ubuntu-file, VLC = nothing mPlayer = nothing, Totem Movie Player = error "**GstDecodeBin: This appears to be a text file**".

Tried to create a play list file with VLC and for some reason it will not save a play list (tried to save the list to desktop and also to network drive), tried the same with mPLayer and Totem Movie Player but could not figure out how to save play lists with ether of them programs.

If i open the windows created file with VI it displays (snppit)```
^@l^@o^@s^@t^@5^@\^@L^@o^@s^@t^@.^@S^@0^@5^@E^@0^@0^@.^@a^@v^@i^@^M^@
^@l^@o^@s^@t^@5^@\^@L^@o^@s^@t^@.^@S^@0^@5^@E^@0^@1^@.^@a^@v^@i^@^M^@

```

If i open the "empty-ubuntu-file" which i copied the content over, VI displays:```
lost5\Lost.S05E00.avi
lost5\Lost.S05E01.avi
```

Through the testing i tried to play the empty-ubuntu-file (with the copied over content) in windows with PowerDVD and nothing, no error no movie.

If i open the windows file with VI and save the file under a different name and try to open that newly VI created file under windows with powerDVD, nothing happens, no error no movie.

If i reopen that "VI saved" file with VI, the content looks ```
^@l^@o^@s^@t^@5^@\^@L^@o^@s^@t^@.^@S^@0^@5^@E^@0^@0^@.^@a^@v^@i^@^M^@
^@l^@o^@s^@t^@5^@\^@L^@o^@s^@t^@.^@S^@0^@5^@E^@0^@1^@.^@a^@v^@i^@^M^@

```

Two questions...

Is there a way around this with out having to have two play list files with the same content, one for Linux, one for windows ?

* How do you create a play list file in Ubuntu so its readable/playable in Windows ? 
If the second question requires some scripting, could you please point me in the right direction. i have no problem working with command-line stuff or scripting if needed.


_

---

### Post by ju2wheels on 2009-12-24
Well you have a dual issue in my opinion. I havent used playlists in a while, and there are many different formats, but Ill assume the one you choose is just a list of paths to the files in the playlist.

So the issues you will come across are:

1. Use of absolute vs relative file paths.
2. Use *nix (/path/to/file) vs Windows (C:\path\to file) file paths.

Thus in short, my recommendation is, always create your playlists in Linux first using relative file paths (preferrably in a folder to where both OS have access if possible) and it should work fine in both OS. In this manner you avoid having to decide on which Windows drive to append to file names and you dont have to replace Windows backslashes in a path with forwardslashes for use in Linux.

---

### Post by iMisspell on 2009-12-24
> **ju2wheels said:**
> ...but Ill assume the one you choose is just a list of paths to the files in the playlist....
Correct


> **ju2wheels said:**
> 1. Use of absolute vs relative file paths.
2. Use *nix (/path/to/file) vs Windows (C:\path\to file) file paths.

Paths are relative for the reason you stated. All files are sitting on a ubuntu 8.04 server.
Server path (really dont matter for this, but...)
/media/hd/watch/tv/lost/lost5/*.avi's

Windows path:
w:\watch\tv\lost\lost5\*.avi's

Ubuntu desktop:
/mymounts/userver/watch/tv/lost/lost5/*.avi's

I would really like to keep the play list files in /lost/ but as you pointed out (and which didnt acure to me) was the forward and backward slash's between windows and linux.

* I just moved the play list files to the same dir which the avi's are in, edited the play list files so they only listed the avi file names - with out paths and the same results as in my first post.

In the end i would like to create the playlist in ubuntu and that play list be used in windows.

I have a Popcorn Hour which i mainly use for watching stuff so the play list files are not used there, but from time to time i'll fire up a windows xp box connected to a different TV which i would like to use the play list with. 


I would really like to find a way to do this.
In time the XP box will be a dual boot, but for now its gonna be XP only.

_

---

### Post by ju2wheels on 2009-12-24
One other issue I can think which may be an issue is the handling of spaces in the paths or file names, or the acceptable characters in a file name (remember that Linux accepts some characters in path/file name which Windows does not).

As stated before keeping the path with forwardslashes makes it simpler, however when you throw a space in the path, im not sure if Windows will like the escaped space or whether it prefers a quoted path. 

For example on Linux spaces are escaped:

/path\ with\ spaces/to/file

However I havent used Windows in so long to know if the above path will trip it up, in which case Windows may want the path in this format (and which is aslo acceptable under Linux):

"/path with spaces/to/file"

---

### Post by iMisspell on 2009-12-25
Thanks for tring to help me out here...

The paths i posted above are real, so as you can see no spaces (or odd charictors).
Just before my last post here, i tried to create a playlist with no paths at-all, only the avi file names; this playlist (withonly file names) was saved in the save folder as the avi's.

The playlist created in windows would only work in windows - the play list created in ubuntu would *not* work in windows.

Gonna do alittle more digging around now.
I was hopping this was something simple i was overlooking (like the foward/backwrad slashs) ;)

Thanks again.

_

---

### Post by ju2wheels on 2009-12-25
That same applies to spaces in the file name btw not just the path, dont know about your movies but mines tend to have a lot spaces in them ;-) .

Sorry I couldnt help much otherwise.

---

### Post by iMisspell on 2009-12-25
> **ju2wheels said:**
> Sorry I couldnt help much otherwise.
The slash's was a big help, thanks.

While toying around i just rename the extension to .m3u and bingo, found some cross-platform ability.

Play list file created with ubuntu is now playable in windows (unfortunately for me, PowerDVD will not play it, but other windows media players are, gonna have to dig around powerdvd's settings and see if it will play .m3u files).

With windows (or should i say Winamp) not being too strict, was able to use a /linux/file/path/ to the sub folder, so that's nice.

Anyway, thought i would post back about the play lists file extension being the key in this case.

Thanks again for trying.

_

---


---
title: "move files without subdirectory structure"
date: 2009-11-12
forum: General Help
---

### Post by nick200 on 2009-11-12
Hi, I just changed to Ubuntu and I'm trying to import a large music collection. I'm using easytag to organize my files and music, and I have a question. How can I copy all the files in order to keep only the last two subdirectories in the folder structure?

For example, I have a structure music/new music/folder a/folder b/artist/album/song.mp3
and would want to copy it into the folder music/artist/album/song.mp3. And do this for ALL the files in the music folder (some subdirectory structures are longer, but I just want to keep the last two that show artist and album).

Is this possible? If not, how could I move the files leaving no subdirectory at all? That is, copy every single file in every single subdirectory in the music folder into the music folder (without the subdirectories structure). 

 I'm not used to linux, so I would have to copy and paste the advice you give me. Thanks!

---

### Post by lswb on 2009-11-12
I don't have a quick answer for your first question though I'm sure it is possible with the right command line or a script. If I can puzzle it out I will post again or more likely someone else will before I do. However, if you can't wait, this will work for copying all files from all subdirectories of SourceDirectory into TargetDirectory. In a terminal:
```

find -L SourceDirectory -type f -exec cp '{}' TargetDirectory \;

```

You can try it first into an arbitrarily named directory, and if it does what you want, rename the directory to Music or whatever with

```

mv TargetDirectory Music

```
Note that if a directory named Music already exists, the mv command will fail. You will need to rename (or delete) the existing Music directory first.

---

### Post by mo.reina on 2009-11-12
this code will find all your mp3 files and strip everything off except the file name of the songs.  i'm not quite sure how to retrieve the 2 subdirectories before that.

```
 find /. -name *.mp3 | sed 's/^\/.*\///
```

---

### Post by mobilediesel on 2009-11-12
[MusicBrainz Picard]("http://musicbrainz.org/doc/Picard_Tagger") can do that. The interface is a little weird at first but you can tell it to arrange the music into folders however you want it.

---

### Post by fluffman86 on 2009-11-12
Use ExFalso instead.  Well, this may work in EasyTag, but I've never really liked easytag, so :P

There are two ways to go about this.  First, let's assume that none of your mp3 files are properly tagged, but they are mostly in the right folder.

In the Folders area of the top left, filter down through your new music until you start getting to the folder that is just above the artist/album/song part.

In the top right panel, click Tags From Path, then the drop down arrow, then Edit Saved Values.  In the new window, give this a name, like "reorganizer" and for value, enter:
<artist>/<album>/<tracknumber> <title>
(I do my own because I don't like the dot after the number) :P
Then click Add and it should show up on the drop down listing.

Click one of the songs in the bottom left, then press ctrl+a to get all of them, then Preview up in the top right next to your drop down box.  Choose your options below the preview window (they're pretty self-explanatory), and click Save.  

*This will take a long time* -- it's adding data to *EVERY* song.  Just give it time.  As long as you hear your hard drive working, you don't need to shut down, even if your computer becomes unresponsive.

Do that for each of your upper level folders until everything has a tag.

Once everything has a tag, or if it already had a tag to begin with, we can now shift things around to where we want them.

Go to the Rename Files tab at the top, and edit the saved values again.  This time, enter:
~/Music/<artist>/<album>/<tracknumber> <title>
and click Add.

Now, you can choose your highest level Music folder, click a song, ctrl+a to highlight them all, Preview, choose your options, and Save again.  This will move everything around the way you want it. :)

---

### Post by nick200 on 2009-11-14
Thanks, this worked just fine!

---


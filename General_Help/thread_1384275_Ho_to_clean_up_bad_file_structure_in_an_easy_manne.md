---
title: "Ho to clean up bad file structure in an easy manner?"
date: 2010-01-18
forum: General Help
---

### Post by Rotehue on 2010-01-18
Over time I have lost total control over the filestructure in my fileserver. My goal now is to re gain control and have a sensible folder structure that will make it easier to use.

I have a media folder with extremly many subfolders.
The subfolders contain either movies, music, photos etc.
One of my problems is that there is no 100 % accuracy when it comes to subfolder content. What I mean is ie.  that a subfolder that contains the discography of a band spread around even more folders will not only contain FLAC files. There will also be cover art, and might even be meta data.

The same goes for all movies as well. Even if the main files in a subfolder will be of certain formats there might be cover arts, metadata or subtitle-files in that subfolder.

Because of the high number of subfolders I feel the task is too overwhelming to be doing manually and hence I have been putting it off for ages, resulting in even more data and more caos. I would like the caos to stop now.

Is there a softwaresolution I can use that will help me move those subfolders with all containing data into smarter folders, like moveis, music, photos etc.?

I will even use commercial version that cost money if no other free solution is available.

With all the scripting going on in the Linux world, would this be possible to solve using a smart script?

I hope the good people here at ubuntu forums are able to help me out or to point me in the right direction.

---

### Post by Rotehue on 2010-01-18
I got a tips about freecommander, but it turns out that freecommander will only owrk for windows. Is there any that might have other tips for me?

Surely I can not be the only person that has this problem?

---

### Post by Rotehue on 2010-01-19
Several tips have been given but I not sure they are all that I need.

[http://www.scarabee-software.net/en/siren_pres.html](http://www.scarabee-software.net/en/siren_pres.html)

[http://www3.telus.net/pfrank/](http://www3.telus.net/pfrank/)

I am still open for tips on how to solve my problem in the easiest way.

---

### Post by vamega on 2010-01-19
I'd first like to check if you realize that moving album art out of the folder in which the music is in could possibly result in the album art not showing up correctly in the music.

Secondly I'd say its better to keep a movie, and it's subtitle files together, rather than in seperate directories, as it is easier to find the subtitle file of a movie in this manner.

However if you are sure you want to go ahead with this, i think your problem can easily be solved with a bash script. I'm no bash expert, so i can't give you all the commands, but a little googling should help. I'm a java and C++ programmer, so I can give you psuedocode, hopefully someone with more bash/csh/some other shell will give you the right commands.

```

Some code to get list of all subdirectories of the root folder of your file server

if filename ends with .wmv|.avi|.mpg|.flv
 cp current_location /movies

if filename ends with .mp3|.ogg.acc|.wmv
 cp current_location /music

```

you get the idea. Sorry that I couldn't be of more help, but from what I understand of your needs, it seems perfectly likely that this could be done using a script.

Vamega

---

### Post by blackened on 2010-01-19
Using a script will likely leave alot of cruft and/or end up causing more of a mess.

Personally, I would follow this list of priorities:

[LIST=1]
[*]Plan how you want the new filesystem to be laid out, then put the folders in place so that you can move things to them.

[*]Now that you've established your new filesystem, make sure that you abide by the organization plan when adding new media to your machine.

[*]Work one folder at a time and clear it up completely to the point that you can delete it when you're finished. By the time you've gone through every folder you should have deleted all of the old filesystem and be left with only the new and organized one.
[/LIST]

---

### Post by Rotehue on 2010-01-19
> **vamega said:**
> I'd first like to check if you realize that moving album art out of the folder in which the music is in could possibly result in the album art not showing up correctly in the music.

Secondly I'd say its better to keep a movie, and it's subtitle files together, rather than in seperate directories, as it is easier to find the subtitle file of a movie in this manner.

Vamega

Maybe I was unclear in the overall goal for this project. I will outline one more time.

The goal here is to keep all subfolders just the way they are today, so that any metadata, subtitles cover arts etc stays in its original folder. 

What I whish for is to be able to move all subfolders containing FLAC into a (parent?)folder named MUSIC. Ie: In my media folder I have a subfolder called MUSE. MUSE contains one subfolder for each album I have ripped by MUSE. So MUSE folder would look like this:
```

Muse 

    * Muse_Showbiz (1999)
    * Muse_Origin of Symmetry (2001)
    * Muse_Absolution (2003)
    * Muse_Black Holes and Revelations (2006)
    * Muse_The Resistance (2009)

```

In details the folder MUSE contains 5 subfolders. Each subolder contains of course the album related to folder name in FLAC, cover art and it even might be metadata.

What I need to do is to move the folder MUSE along with all 5 subfolders and all containing data into the new folder named MUSIC.

Then I would would do this also for all movies. Each DVD I have ripped is ripped into a folder that holds a folder-name that relates to the title of DVD. The content can be ISO, TS etc + metadata+ coverart. Like the example above the folder and the data inside needs to be removed to a new folder called MOVIES.

So I have a folder named "The Terminator". That folder contains The Terminator.iso + subtitle + cover art. I would like to move folder "The Terminator" and all containing data into new folder named MOVIES, so The Terminator will then become a subfolder of MOVIES.

So I do not intend to take any data out of the folder where data resides today. Rather I wishes to move folder and ALL data.

And that is the reasson I can not use any of the tips I have listed earlier in the thread.

Hope thing is more understanable now. If not let me know and I will continue to explaain. English is not my native tongue so it is hard for me to express myself correctly in english.

---


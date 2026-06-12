---
title: "album list creater tool thingie???"
date: 2009-10-21
forum: General Help
---

### Post by stinger30au on 2009-10-21
i have a *TON* of music cds i have bought over the years and i have converted a few to mp3 format to play round with

when i converted the files i saved them in a directory and the name of the directory was the name of the album

in the directory i saved all the mp3 files and they are all saved as song title and artist


when i point rythym box at the handfull of directorys i have created rather then get the names of the albums as i hoped for, i just get songs and artists instead

is here some kind of special song creator program type tool that i must run that reads the directory and saves a special file in the directory that rythym box reads abd has the album name on it or what do i do to fix this??

thanks

---

### Post by DeMus on 2009-10-21
> **stinger30au said:**
> i have a *TON* of music cds i have bought over the years and i have converted a few to mp3 format to play round with

when i converted the files i saved them in a directory and the name of the directory was the name of the album

in the directory i saved all the mp3 files and they are all saved as song title and artist


when i point rythym box at the handfull of directorys i have created rather then get the names of the albums as i hoped for, i just get songs and artists instead

is here some kind of special song creator program type tool that i must run that reads the directory and saves a special file in the directory that rythym box reads abd has the album name on it or what do i do to fix this??

thanks

In my Rythmbox I see:
Track nr, Title, Genre, Artist, Album, Time.
All the info I need to see. Don't you see this?

---

### Post by stinger30au on 2009-10-21
> **DeMus said:**
> In my Rythmbox I see:
Track nr, Title, Genre, Artist, Album, Time.
All the info I need to see. Don't you see this?

ah ha

i went hunting

i had to put a tick in the box that says album

*BUT*

its still not right

i dont know why but for some reason rythym box is ignorning the name of the directory as the album name

perhaps it is supposed to do this, i dunno

the music i have got im experimenting with is a few cds from years ago that are mixxed compilation albums with music from all over the place

looks like rythym box has connected to the net and got the album names from there instead

the music names and artist names are fine, but the albums it has got listed is definately not what i have got

what i was expecting is for there to be on the right hand side where it says "album" for it to show each directory name

each directory name i have is labelled as the correct album name i ripped the songs from

perhaps im wrong in my thinking??

---

### Post by egalvan on 2009-10-21
Look at the ID3 tags on the mp3 files.

This is where the information should be stored.

---

### Post by stinger30au on 2009-10-21
ah ha

more looking and i found a tick box that says location

from its location i can now tel what album im looking at, the location is the full path location on my hdd to the files

this helps me out, but not what i was expecting

surely there has to be a better method then this

---

### Post by stinger30au on 2009-10-21
> **egalvan said:**
> Look at the ID3 tags on the mp3 files.

This is where the information should be stored.

ok, how do i do this?

---

### Post by stinger30au on 2009-10-21
ah ha!!

more reading and googling

i found this

[http://en.wikipedia.org/wiki/M3U](http://en.wikipedia.org/wiki/M3U)

looks like if i make a M3U file and shove it in the directory with the music that should do what i want

i believe that rythym box can read these files and understand them

now all i need to find is how to make these M3U files

---

### Post by egalvan on 2009-10-21
More googling, more wiki

[http://en.wikipedia.org/wiki/Id3](http://en.wikipedia.org/wiki/Id3)

:)

Seriously, check the menus for ID3 tags stuff.

i don't use these programs much (rhythmbox), sorry.

---

### Post by egalvan on 2009-10-21
I believe rhythmbox has a menu entry for creating playlists (m3u, to you)

Also, go into Synaptic and search for ID3, you will find several ID3 editors.

---

### Post by stinger30au on 2009-10-21
> **egalvan said:**
> More googling, more wiki

[http://en.wikipedia.org/wiki/Id3](http://en.wikipedia.org/wiki/Id3)

:)

Seriously, check the menus for ID3 tags stuff.

i don't use these programs much (rhythmbox), sorry.

cool, thanks for the info, it is a very interesting read and i have learnt form it

but how the heck to i check this in ubuntu???

having said that i have found if i create a new playlist in rythym box and then open up nautilus and open the album up and select all and drop the files in to the play list it will save the album and songs together how i expected them to be

surely there has to be a better way

im sure the id3 tags is the way to go

but how to do it is the secret im yet to discover

thanks

---

### Post by stinger30au on 2009-10-21
ah ha!!

the secret to it is to create anew play list

open nautilus

select all files

drag and drop the files to rythum box

then save the playlist file as a m3u back in to the directory where the music is

that way it will all ways be there and if ubuntu on this hdd gets replaced with a new ubuntu rythym box will read the m3u file and all is good!

YIPPE!!

all sorted!!

YEE-HAW!!

ROCK ON UBUNTU!!:guitar:

---

### Post by egalvan on 2009-10-21
OK, just for you, I installed the latest rhythmbox, and easytag.

here are three screen-shots. Notice the information given for the chosen song.

This information is in the ID3 tags.

Easytag is but one program that can read and write these tags.
there are others, try one or more, see which one you like best.
i would suggest you try these on a small sub-set of your collection.
make a copy of the songs, in case you don't lke the results,
or in case of "whoopsies"

---

### Post by egalvan on 2009-10-21
gotta go work my shift at the firehouse.
i'll be back in 24.

hopefully you will have made even more progress.

ErnestG

---

### Post by stinger30au on 2009-10-21
thanks guys for your feedback

i went hunting thru synaptic and i found "amarok" and i installed it

it does exactly what i wanted and more that i was looking for from rythym box

yippie!

i wont bother with rythym box any more

but i have learnt a lot though

thank you!

---


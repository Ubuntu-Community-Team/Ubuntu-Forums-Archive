---
title: "comparing multiple files in shell script"
date: 2010-06-13
forum: General Help
---

### Post by chowanec on 2010-06-13
All -- I've got an interesting challenge for the shell scripting wizards here. I've got a mySQL dump of three files for my amarok database with the intention of copying some files to my media server (cover art) so that I can keep the server the server and not rely on my local machine.

Step 1: Identify any cover art files on my local machine.

I did this with:
```

mysql -u amarok -p amarok -e "SELECT * FROM images WHERE path like '%.kde%'" > cover_art.txt

```

Output looks like this:
```

id	path
1450	/home/chow/.kde/share/apps/amarok/albumcovers/large/bea89379af055edf01a227f783eb1eb4
1451	/home/chow/.kde/share/apps/amarok/albumcovers/large/f71f21a84e7fec0da740b689c7b0bb8e
1452	/home/chow/.kde/share/apps/amarok/albumcovers/large/b8b47514c4741797c5552754f4c137cd

..

```

Here's what I have -- IDs for the local image files that are the odd-men out compared to the rest of my database.  My intention, eventually, is to copy these as folder.* to the proper folder on my network.

Step 2: Query the entire album database (this is, after all, coverart)

Another mySQL query:
```

mysql -u amarok -p amarok -e "SELECT name,artist,image FROM albums" > albums.txt

```

It's output looks like this:
```

name	artist	image
!!!	1	1
Louden Up Now	1	1681

..

```

What I have here now is the ENTIRE album list in my collection -- and something to compare the IDs in Step 1 against.  I'm going to stop here and will update the thread as I get past this stumbling block. "ID" in cover_art.txt = "image" in albums.txt... straightforward enough, right?

So the question is this: how do I create a simple shell script that will loop through the IDs in cover_art.txt (i.e. characters 0 -> 4 -- it will always be a 4 digit ID) and then search for that ID in the Albums.txt file. 

Shell/Bash scripting is entirely new to me... (can you tell?) :)

Any guidance is appreciated.

Thanks.

-Chow

---

### Post by john newbuntu on 2010-06-13
This is easier done in a join query in SQL than in script.
As I understand it, you need IDs in cover_art along with their matching album details.  So:
```
select images.id, albums.name, albums.artist, images.path
from albums, images
where albums.image = images.id
and images.path like "%.kde%"
```should give you what you need unless I misunderstood you. You could also do it an an outer join for missing ids, although I'll leave it to you as an exercise.
If you need a script, just wrap it in a shebang bin bash and add necessary mysql decorations to it.

---

### Post by chowanec on 2010-06-13
Wow -- that is awesome -- thank you so much.  Does exactly what I needed for step 1 and 2.  If you can continue to indulge me... :)  Here's what I need to figure out next.

Now that I have output that looks like what you've queried:
```

id	name			artist	path
1681	Louden Up Now		1	/home/chow/.kde/share/apps/amarok/albumcovers/large/3c46cb1e1868630b67b9cb79c8033a35
2115	Let's Build a Fire	2	/home/chow/.kde/share/apps/amarok/albumcovers/large/da0e4ead5c79e9f818876cbc8b96402f

```

And now I want to map that to the directories the music is stored in (on the Network server).  Thankfully Amarok has a directories table in its database.  Regrettably it does not map 1:1 with the album list.  There are more records in directories than their are in albums.  They are storing every directory like below:

```


id	dir
1	./home/chow/Network/Music/
2	./home/chow/Network/Music/!!!/
3	./home/chow/Network/Music/!!!/!!!/
4	./home/chow/Network/Music/!!!/Louden Up Now/
5	./home/chow/Network/Music/+_- {Plus_Minus}/
6	./home/chow/Network/Music/+_- {Plus_Minus}/Let's Build a Fire/

```

While "Louden Up Now" for instance is teh final directory for that album, amarok stores the path leading up to that as its own record in the directory table.

So NOW the question becomes -- is it possible either in mySQL or Bash to now associate the directories.dir with albums.name somehow?

Thanks again -- I really do appreciate it.

Cheers,

Chow

---

### Post by john newbuntu on 2010-06-14
You could try this for a start, but without knowing the actual amarok datamodel, it has hard to come up with the correct query:

```
select images.id, albums.name, albums.artist, images.path, directories.dir
from albums, images, directories
where albums.image = images.id
and directories.id = images.id
and images.path like "%.kde%"
and directories.dir not like "%!!!/"
```

---


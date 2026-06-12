---
title: "Searching for MP3's on my HDD"
date: 2011-11-30
forum: General Help
---

### Post by kr651129 on 2011-11-30
No idea where I would put this question, so I placed it here.  MODs please move if you see fit.

I don't do a lot of bash scripting so I need some help.  Basiclly I want to write a script that will search my HDD for any mp3, flac, wav, files etc and then place the location of each file in a text document (I'd prefer a SQL database but one step at a time here :) )

What I'm trying to do eventually is I want to build a database with the location and ID3 tags of these files so I can quickly search for my music.  I know amarok does this but I have a headless ubuntu server that holds all my music and if I can build a database then I can write an html5 page that displays and plays any music that is selected that was i can access this on my droid devices, ios devices, and others.

But like I said, one step at a time and the first step is finding a way to get the location and ID3's of all mp3's

---

### Post by nothingspecial on 2011-11-30
> **kr651129 said:**
> No idea where I would put this question, so I placed it here.  MODs please move if you see fit.

Putting it in tutorials and tips means only staff and yourself can see it.

Moved to General Help.

---

### Post by dave0109 on 2011-11-30
The command 'find' is going to be your friend here.  Look at the man page because there are lots of options which you can tailor to suit your requirements.  Notably you'll want -name and -print.

If you need further help, don't hesitate to ask.  I'm not sure if you want to work it out yourself or not. :)

---

### Post by kr651129 on 2011-11-30
So if I used find in a bash script how will the results be passed back to me?

---

### Post by kr651129 on 2011-11-30
Ok so 

```

find *.mp3 /media/samba

```

Works, but when I

```

find *.mp3 /media/samba > ./mp3.txt

```

I get

find: `*.mp3': No such file or directory

thoughts?

---

### Post by mutley89 on 2011-11-30
Do you have any reason to create a new db?  The 'locate' program does exactly what I think you are asking.  Try:
```

locate *.mp3

```This will show all files ending in '.mp3'.  It uses a database that is updated by a daily cron job.  Running 'updatedb' will update it again.

Also when using find you need to specify the path to search in first, then specify a globbed pattern with -name.  I think this is what you are trying to do?:
```

find /media/samba -name *.mp3 > mp3.txt

```

---

### Post by kr651129 on 2011-11-30
Thank you!

```

find /media/samba -name *.mp3 > mp3.txt

```

Did exactly what I needed.

Then to add it to a the table I went into phpmyadmin and imported it as a cvs.  I changed all of the character breaks to characters that weren't used in the txt file except for the new line.

Now, I need to figure out how to automatically read the id3 tags from the files in the db and add them to the db.

The reason I want to create a new db is so I can make a searchable database from my drupal install and play them from my html5 player

---


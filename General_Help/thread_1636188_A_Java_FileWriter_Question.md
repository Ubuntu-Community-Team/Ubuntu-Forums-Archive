---
title: "A Java FileWriter Question"
date: 2010-12-02
forum: General Help
---

### Post by Taliathion on 2010-12-02
Hey there, not sure if this is in the right forum, let alone the right site, but Ubuntu forums is one of my favorite communities, so I thought I'd ask here first.

My question is about the FileWriter capabilities of Java. I've been using Java in my spare time to develop simple apps that I feel are easier done in it rather than C or Python, but I'm unsure of it's ability to do what I need it to in this case.

I know Java can write to text files, and append data on the end, but what the main issue is here is that I need to know if it can re-write data over and over (i.e. export various values of variables to a file, be able to import them and have them replace the ones prior to the import [export value 1 to file, value 1 changes to value 2 in program, import from file, value 2 becomes value 1 again,] and be able to rewrite the data in the file [export value 1, value 1 changes to value 2 in program, export value 2 to file, in file value 2 becomes value 1])

Sorry if that sounded confusing, but regardless, if java CAN do this for me, how would I do so?

                       Thanks Muchly,
                                  Taliathion

---

### Post by idi0tf0wl on 2010-12-02
Java can totally do this, but it really kind of depends on your own creativity. One of the easiest ways I know to do this is to work with xml files or databases for the storing/retrieving/overwriting specific elements aspect. Or you can write to reg'lar ol' text files and delimit certain elements by different non-letter characters, then use Regex and Pattern objects to manipulate them from there. Maybe use a StringBuffer to collect the changes, and then overwrite with that. You can use lots of these different techniques in combination with one another to accomplish your specific ends - that's the brilliant thing about Java!

Cheers

---

### Post by Taliathion on 2010-12-02
That sounds plausible, but I shy from the database system. I want this to be easily distributed to the friends of mine that work with java, so I would much rather have it export to a file over anything else. Also, unfortunately, I am far better versed with other languages than Java, so I am unclear on ways to do the other things you have mentioned. If you would care to explain further I would be much obliged. Regardless, thanks muchly!

Anyone else have ideas they would like to share?

~Edit, that is to say, the actual methods you have mentioned, I understand that you can't explain for my exact situation, as the variables I want to export are over 500 lines into the code and get changed VERY often.

As this is most likely my last post for tonight, I'll put out as much extra information I can right now.

I want to export a set of public integers, doubles, and I think one string. These values change often in various methods of the code, but the main "hub" of the user interaction where all commands are executed, and where these values must be exported from, is itself a method, being executed from the main. E.G.:

Main -> Hub -> Method -> Method2 -> Method3 -> Hub -> Export

The values could change in ANY of the methods but the main and hubs, if that's important.

Thanks so much in advanced!

---

### Post by idi0tf0wl on 2010-12-03
Again, allow me to recommend xml. I use it a lot for various data management work, and java is very good at it. FileWriter can export to whatever filename you choose, and as long as you're careful (coder's credo, right?) with the way you build your String (that is, the very first one. From there you can just swap elements from one file), you should find it more than capable and fairly easy to learn how to do.

Note: as you'll be needing to access, manipulate, and write objects other than Strings, familiarize yourself with with methods like parseFloat(), toString() and the like, as ultimately you'll need to pull and write **text** at the beginning and end of each exchange (the only way around that is a database). Tutorials for this kind of thing (including all the xml stuff) is pretty readily available. Within reason, pm me with problems you can't seem to work through. Sometimes another look at your logic makes all the difference!

---


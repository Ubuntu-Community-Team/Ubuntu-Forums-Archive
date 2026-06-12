---
title: "Making more use of my server.. help/suggestions please!"
date: 2010-09-26
forum: General Help
---

### Post by Saidear on 2010-09-26
I'm running relatively overpowered server right now, that all it really does is host files and download movies/music that I might enjoy.  I'm just seeking to expand it's capabilities to make life in the house more simple.

The first thing I'd like to do is create a kind of automatic grocery list generator concept.  Here's how I envision it working.
We create a list of recipes for meals we enjoy, specifically an ingredient list.  From this list, we create bi-monthly meal lists; what do we want to have for the next two weeks.  The server chews through the two lists, compiles a list of ingredients and how much of each we'd need.. and emails this off to our smart phones for us to refer to while shopping.

What equipment do I have?  I have a headless Ubuntu server running 10.04 and administered via a GUI and NX Client.  Two blackberries (both 9700 Bolds) as portable smart clients that would need to at least receive the list, tho ability to add in would be great.

Home network is a mix of wired and wireless, so no issues there for connectivity. 

So why post this here?  Because I'm at a loss as to the software/configuration part.  Doing an automated email daemon is easy to send the list out.  And a list of recipes or such is easy to get (dozens of cookbooks in the house, plus a small army of them available online).. the issue I'm having with is how to create/manage the database.  I'm not familiar with SQL or any database programming at all.

Is there something akin to this already in the repositories? Or is there someone who could point me in the right direction so I can do this? 

(Once this project is sufficiently going, I'll list my other ideas and see what can be done for them.. =) Thanks in advance for any pointers!)

---

### Post by Absolom on 2010-12-18
There is a firefox add on that seems to do exactly what you are talking about called grocery list generator

---

### Post by hoooootz82 on 2010-12-19
You could also make it a print server, which any ***puter on the network would be able to print to. I re***mend hp printers for linux.

I know you mentioned you dont know sql, but if you get a lamp (linux, apache, mysql, php) setup, you could set up joomla or something like it, which is relatively easy, and get some sort of recipe thing cooked up there. There should be very little code/html/mysql editing to set this up.

Also, have not tried this myself, but you may be interested in setting up a squid server. I do not know what that requires, how much space it needs, or if it's worth it, but it sound like a cool idea.

---


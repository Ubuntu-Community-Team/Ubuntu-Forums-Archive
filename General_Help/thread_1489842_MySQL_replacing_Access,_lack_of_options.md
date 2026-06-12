---
title: "MySQL replacing Access, lack of options"
date: 2010-05-21
forum: General Help
---

### Post by NertSkull on 2010-05-21
So, I've read thousands of posts now on this, and before I make the plunge, I wanted to make sure I'm not missing something.

I've been using linux for the past year and LOVE it.  There are two things that tie me to windows still.  Webcam chat in gmail to keep in touch with family (yeah, I can get the webchat in linux, but I get really bad feedback).

And two.  Access.  I have a relatively large Access database I started making years and years ago that I keep all my financial records and budgets in.  It keeps me organized and I can't lose it.  But I want to get out of windows so I've been looking at moving to MySQL (I also looked at postgre, but it seemed to be a coin toss between the two).

Open office base is nice, but it just can't cut it for my needs it appears.  I've played around with it for a week now, and nothing is going great.

So, I'm down to building everything with PHP and HTML and MySQL, or just sticking with access.  I have super limited time (I'm a grad student in a non-computer field) so I was hoping for something not involving hours of php writing.  But I just can't find it.

So am I missing something?  Or is PHP the way to go?  I don't need this to have access to the web, I wouldn't dare put all my finance stuff anywhere other than encrypted on my computer.  

I'm relatively new to non-access databases still, so any guidance would be appreciated.  Really I just need something that will access the MySQL database, and allow me to create forms and reports so I can input multiple records of data at once (easily) and then print out a report.

Ideas on where I should go/look?  Or am I correct to start making the move to PHP?


Thanks all!

---

### Post by wojox on 2010-05-21
Sure Apache, Php, amd MySql are great whether your using them locally or remotely.

If your comfortable with Access, then MySql should be a breeze.

Have a look here [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") 

I'd also recommend [W3Schools]("http://www.w3schools.com/")

---

### Post by oldfred on 2010-05-21
Some more databases to look at - none seem to fully match Access. 

MDB Viewer
[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)
[http://www.knoda.org/](http://www.knoda.org/)
[http://www.gnome-db.org/](http://www.gnome-db.org/)


I was able to use kexi and with an addin convert an old access db.But only the data. queries, forms and reports all were gone. I have not tried knoda yet, but have been learning python which is an alternative to PHP and has lots of already built modules to handle data.

---


---
title: "Azureus: too many open files | too many files open"
date: 2006-03-17
forum: General Help
---

### Post by DonQuixote on 2006-03-17
Hello all,

I'm running in to an interesting issue here with Azureus throwing an error of there beeing too many files open.

Is there some way of changing some setting that will allow unlimited, or at least, such a high number of connections (I'm assuming a connection is considered an open file) that I may never reach it?

John

---

### Post by drewnoakes on 2006-11-14
I guess no one replied.  I'm having this same trouble on Ubuntu 6.10, though I'm using the distro's JVM and not the Sun one.

I've read this on a different forum:

[INDENT]I have the same problem.

It is because there are too many open files, just like the error says .
I read somewhere that the standard limit is about 1024 open files. And since in linux everything is considered as file, also network connections and **** it isn't weird you can get this error in Azureus. Azureus uses quite a lot connections.

The workaround: sudo sh -c 'ulimit -n 8192; sudo -u username ./azureus'
(This assumes you want Az to run via the user 'username'. It also assumes that you are in the right directory. Edit it to match local reality.)

Now I want to change this limit globally. Therefore I need to change a certain file but I have no idea which one that would be in Slackware. I took this information from [http://azureus.sourceforge.net/wiki/...oManyOpenFiles](http://azureus.sourceforge.net/wiki/...oManyOpenFiles) and the author there talks about a file called: /etc/sysctl.conf . Unfortunately I don't have that file in Slackware so I suppose I can find it somewhere else. If anyone would point this out for me . ?[/INDENT]

Quote from Mikeya at: [http://www.linuxquestions.org/questions/showthread.php?t=172388]("http://www.linuxquestions.org/questions/showthread.php?t=172388")

Still not a complete answer, but it might get us closer.  I don't suppose you're still following this as it's been quite a while for you.

---

### Post by drewnoakes on 2006-11-14
There's some more info here:

[http://www.azureuswiki.com/index.php/Too_many_open_files](http://www.azureuswiki.com/index.php/Too_many_open_files)

---

### Post by DonQuixote on 2006-11-14
Thanks for the reply.

I think I read about that workaround you are talking about.  It's been so long since I got it to work again I have forgotten what it was that I did.  But maybe someone else can use this thread.

---

### Post by drewnoakes on 2006-11-14
Yes, I hope someone else can make use of this thread.  Perhaps someone knows of a less heavy-handed approach.  Regardless, this thread came up quite high on my search so I thought I'd contribute here.

---

### Post by webjames on 2007-04-11
i am having the same problem. did anyone find the solution?

---

### Post by j3cakes on 2007-05-02
which is the 'right' directory? is it the azureus one?

where are you supposed to run this command?

---

### Post by johnc3 on 2007-07-28
whereis azureus returns

azureus: /usr/bin/azureus /usr/X11R6/bin/azureus /usr/bin/X11/azureus

so you should go in the directory /usr/bin
and the paste the command below

sudo bash -c 'ulimit -n 8192; sudo -u username ./azureus'

it worked for me

---

### Post by brephophagist on 2007-09-11
the file you want to edit to change the number of files permanently is probably /etc/security/limits.conf. (for PAM-enabled systems) see [http://confluence.atlassian.com/display/DOC/Fix+'Too+many+open+files'+error+on+Linux+by+increasing+filehandles](http://confluence.atlassian.com/display/DOC/Fix+'Too+many+open+files'+error+on+Linux+by+increasing+filehandles)

---

### Post by -GC- on 2007-11-29
How would i go about doing this with freeloader?

---

### Post by Slippy Lane on 2008-04-16
Well fellas, yes it did help someone else. Whilst downloading a collection of free eBooks, I encountered the "too many open files" error. A quick search pointed me at this thread.

Rather than mucking about with global file limits, I replaced the link residing at /usr/bin/azureus (which obviously points to the Az executable) with a quick bash script, containing the "sudo sh -c" line quoted above, and which calls the Az executable directly.

The Ubuntu community forum has had the answers to almost every question I've had since installing Ubuntu, and most of those answers have not even required me to ask the question. Thanks guys

---


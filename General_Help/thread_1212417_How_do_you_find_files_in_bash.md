---
title: "How do you find files in bash?"
date: 2009-07-13
forum: General Help
---

### Post by Patrick Snyder on 2009-07-13
Hi,

In bash, how do you find the paths of files, when you don't know where they are?
For example, if something tells me to "modify foo.ini", and I don't know where in the filesystem foo.ini is, what are the ways to find it?

---

### Post by doas777 on 2009-07-13
I usually google it. 
config files are usually in /etc or in ~/.<appname>. most apps are in /usr/bin. if your looking for a command, you can use 'which <cmdname>' to get the path(s) that it exists at.

---

### Post by bodhi.zazen on 2009-07-13
1. locate

```
locate foo
```

2. find

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

find has a number of nifty options, lots of geek points.

---

### Post by andrew.46 on 2009-08-21
Hi bodhi.zazen,

> **bodhi.zazen said:**
> 
2. find

[http://content.hccfl.edu/pollock/Unix/FindCmd.htm](http://content.hccfl.edu/pollock/Unix/FindCmd.htm)

find has a number of nifty options, lots of geek points.

I see that a hard-working (and good-looking) member of the Beginners Team has just finished substantially renovating  the Ubuntu Community page for find:

find - Ubuntu Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

Still a little polishing to go but this might be well worth a look as well :-).

Andrew

---

### Post by bodhi.zazen on 2009-08-21
Nice find

Bookmarked.

---

### Post by rifak on 2009-08-21
one thing to keep in mind when using the locate command is that the database isnt updated automatically after changing, removing, or moving files or directories around. so you'll find yourself locating files that are non-existent. an easy way around this is to alias locate to include the updatedb command:

alias locate='sudo updatedb; locate '

the only downside to doing this is that if the database hasn't been updated in a while and you have added/changed a ton of files, the newly aliased locate command will be on like a 5 second delay...so when you do 'locate test.txt' it'll ask for your password, then sit there for a second, then list the output of locate. this is the easiest way ive found to be able to consistently keep the locate command showing true and accurate results.

if there is an easier, or better, way of doing this let us know.

---


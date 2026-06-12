---
title: "Help Me Use the Terminal to...."
date: 2010-05-14
forum: General Help
---

### Post by Crowder on 2010-05-14
...clean up my music collection!

Here's the deal guys:

As I've tagged and re-tagged things from banshee, it has moved them around into either newly created or existing folders, and left a trail of empty ones in its wake. A flaw with Banshee, clearly, but it would really help to just get rid of all of the remaining empty folders.

So... can anyone devise a command or series of commands that would:
[LIST]
[*]Search ~/Music/ for empty directories, recursively
[*]remove the empty folders
[/LIST]

I have a fairly good handle on using the terminal, but I just can't figure out how to get this done as I'm really no comp sci whiz. If somebody can think of a way for this to be done easily, I would greatly appreciate it if you could just write up a script for me real quick. Thanks in advance.

---

### Post by kaibob on 2010-05-14
The following command will find all empty directories within /target/directory:

```
find /target/directory -type d -empty
```

You can combine this with the exec option and rmdir as shown at:

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by Crowder on 2010-05-14
Thank you sir

Much obliged t' yee

---


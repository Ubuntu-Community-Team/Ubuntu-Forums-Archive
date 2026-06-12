---
title: "challenged by qmv"
date: 2011-05-25
forum: General Help
---

### Post by engine on 2011-05-25
Trying to use the qmv utility to help me rename a couple of thousand files. I get the parallel list of file-names, make the required changes to the second column in the list, save the file &#8210; using vim as the editor &#8210; and close the editor.

Do I get a stack of renamed files? nah, just an incomprehensible message :-{

```
[prompt] qmv ec*

&#8230; here I see the file-list in vim, edit it, save it and close the editor session &#8230;

qmv: premature end of /tmp/qmvm0VYPa looking for /tmp/qmvm0VYPa
Entering interactive mode.
qmv >
```

Any tips on getting this promising option to work? Thanks in advance!

---

### Post by webofunni on 2011-05-25
Did you try removing /tmp/qmv* ?

---

### Post by coldraven on 2011-05-25
Don't know about qmv but I just tried krename and it is very powerful. It has plugins for PDF and media metadata etc.
Run it standalone or use it via [Krusader]("http://www.krusader.org/") (two pane file manager)
Install from Synaptic and read about it [here]("http://www.krename.net").

---

### Post by zapaces on 2012-02-28
Hi there,
I just discovered **qmv** and I'm having a great time with it.

First, I would ask you ... how are you finishing your edit in Vim... for me **:wq** works great. Also, are you, by any chance deleting one column?

Second... I find the **-f "destination-only"** option to be really nice. It's easier (you get only one column, hence aligned) and you don't get "false" ideas, ie. you change one directory or file and then you think you're changing something else... and you only get errors.

I use this tool a lot (specially after having MusicBrainz Picard duplicate many folders. I used the following call:

```
qmv -f "destination-only" -R music
```

Great tool. Hope this helps you.

---


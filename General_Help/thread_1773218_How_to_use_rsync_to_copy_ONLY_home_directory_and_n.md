---
title: "How to use rsync to copy ONLY home directory and no files?"
date: 2011-06-01
forum: General Help
---

### Post by quickk on 2011-06-01
Hi everyone, 

    I know that this isn't the right place to ask, but I figured that someone might know the answer, so here goes.

How can I use rsync to copy ONLY the my home folder (and nothing inside of it, just the folder name) to another machine.

I've tried things like 
```

rsync -av  /path/to/src /path/to/dest/
```

or 

```
rsync -av -f"+ */" -f"- *" /path/to/src /path/to/dest/
```

This last option recursively (through the -a switch) copies only folders, including all subfolders.   If I try 


```
rsync -v -f"+ */" -f"- *" /path/to/src /path/to/dest/
```

nothing is copied (not even my home folder.   What gives?

---

### Post by Rubi1200 on 2011-06-02
Definitely not an rsync expert here, but what about this as a solution:

```
rsync -d /path/to/src /path/to/dest
```

---

### Post by seawolf167 on 2011-06-02
I'm thinking along the same lines as Rubi, drop the -a switch, since it implies recursion and you don't want recursion, then add the -d switch to only copy directories.

---

### Post by jamesisin on 2011-06-02
Let's just ask "what are you trying to accomplish?" because if all you want to do is create a folder with the same name on a different system this is all silly extra work.  So what are you really trying to do?

---

### Post by quickk on 2011-06-03
Thank you Rubi1200 and seawolf167!  I did

```
rsync  -dptgov  /home/myusername  node1:/home

```

and it worked perfectly.  I don't know why I didn't see the -d option before.  The extra flags were to keep the permissions and ownership intact, and node1 is where I am copying the home directory to.

To answer your question jamesisin, I have a small computing cluster that I am trying to learn how to set-up and manage.  There are about 20 nodes, and so I am trying to learn how to do things efficiently instead of manually making the changes on each node.   

So to copy my home to all nodes I did a loop like so:

```
for i in {1..20}
do
  rsync  -dptgov  /home/myusername node$i:/home        
done

```

Thanks again for the help.   I am always astounded by the knowledge of people on this board!

---

### Post by Rubi1200 on 2011-06-03
> **quickk said:**
> Than
Um, wel :-)

So, did my suggestion work or seawolf167's  as far as achieving what you wanted?

Good to know for future reference when faced with a similar question.

And, if the problem is resolved please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by quickk on 2011-06-03
Sorry... I hit the reply button too soon!

---

### Post by Rubi1200 on 2011-06-03
> **quickk said:**
> Sorry... I hit the reply button too soon!
No problem and you are more than welcome :-)

Good luck with your project, it sounds interesting.

---

### Post by HotForLinux on 2011-06-03
I think that 

rsync -dr /path/to/src /path/to/dest

should  _only_ copy all the subdirs in the /src/ dir

What's the use of having:

rsync -dr
rsync -r 
[FONT=monospace]
[/FONT]do the same thing? It makes things more confusing and difficult. Don't you think so?

---

### Post by quickk on 2011-06-03
As far as I can tell, "rsync -dr" and "rsync -r" do exactly the same thing.  I've tried both out and the result is that all subdirectories AND files are copied over.    

To copy only the folders, you need something like: 

```
rsync -av -f"+ */" -f"- *" /path/to/src /path/to/dest/
```

And yes!  It is confusing!

---

### Post by HotForLinux on 2011-06-03
> **quickk said:**
> As far as I can tell, "rsync -dr" and "rsync -r" do exactly the same thing.  I've tried both out and the result is that all subdirectories AND files are copied over.    

To copy only the folders, you need something like: 

```
rsync -av -f"+ */" -f"- *" /path/to/src /path/to/dest/
```And yes!  It is confusing!

Yes. In my view, that is stupid. Another of the many little things that nobody ever fixes or polishes and makes things complicated.

---

### Post by jamesisin on 2011-06-03
Just to be complete, it may be important to note that these two lines will (potentially) return different results:

```
rsync  -dptgov  /home/myusername node$i:/home

v

rsync  -dptgov  /home/myusername/ node$i:/home/
```

---

### Post by jamesisin on 2011-06-03
The -r --recursive argument is for file recursion.  The -d --dirs argument claims to be for a directory.

> -d, --dirs
              Tell  the  sending  side to include any directories that are encountered.  Unlike --recursive, a directory’s contents are not copied unless the directory
              name specified is "." or ends with a trailing slash (e.g. ".", "dir/.", "dir/", etc.).  Without this option or the --recursive option,  rsync  will  skip
              all  directories  it encounters (and output a message to that effect for each one).  If you specify both --dirs and --recursive, --recursive takes prece&#8208;
              dence.

So, quickk, yes -r and -dr will behave the same; and no, HotForLinux, this does not appear to be a bug.  Though it may be a bug that -d won't recurse for directories (that is less clear to me).

I'm still unclear what possible benefit would come from copying an empty folder hierarchy.

If all you want to do is copy an empty folder hierarchy it might be easier to use find -d and (s)cp.  Or if you are keen on using rsync I suppose you could create an include list using find -d and then use --include-from=.  (It may be possible to write an include pattern for directories? and then use --include=.)

But seriously, somebody please help me understand why it would be useful to copy an empty folder hierarchy.

---

### Post by quickk on 2011-06-21
> **jamesisin said:**
> 
But seriously, somebody please help me understand why it would be useful to copy an empty folder hierarchy.

I have a cluster with 29 slave nodes + 1 master node.   When I create a new user on the master node, I also want home folders to be created on each slave node so that when a user ssh's into these nodes, they will have a home directory.   I could manually ssh into each node and create the home directory, but this is tedious.

---

### Post by silverglade00 on 2011-06-21
> **quickk said:**
> I have a cluster with 29 slave nodes + 1 master node.   When I create a new user on the master node, I also want home folders to be created on each slave node so that when a user ssh's into these nodes, they will have a home directory.   I could manually ssh into each node and create the home directory, but this is tedious.

You could also set up an NFS share of the master's /home and have the slaves automount it. That way you don't even have to copy anything. You also won't run into problems with multiple versions of files in home directories.

---

### Post by quickk on 2011-06-23
In my particular situation, I do want different home directories on each node because each node will be responsible for solving a small chunk of a much larger problem.   Each node will require some local storage, and thus the need for separate home directories (and since there will be multiple users, I don't want the local storage to get mixed up).

Thanks for the suggestion though!

---


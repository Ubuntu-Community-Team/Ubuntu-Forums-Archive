---
title: "Picture organizer"
date: 2011-12-03
forum: General Help
---

### Post by aneblanc on 2011-12-03
I am looking for an application that would let me view all my pictures that I have in so many folders in only one folder in chronological order.

It would also be able to detect duplicates in order to delete them.

Any suggestion?

---

### Post by MG&amp;TL on 2011-12-03
There are lots of photo organizers for Ubuntu-I use shotwell, but search for picture organizer in Ubuntu Software Centre and there should be a lot of hits. IDK if any one will do what you want. Shotwell and F-Spot are the most comprehensive IMO.

Try those first, if they don't work, report back. Some information about your directory structure would also be helpful.

---

### Post by aneblanc on 2011-12-03
Thanks for the fast answer. I had done a search in the software center and got one reply: Mapivi.

I use Shotwell but it does not seem to do what I want: I just need a program that would temporarily remove the sub-directories and allow me to see all the pictures (or files) in a single directory.

I used to use X-Tree in '86-'88 under DOS. It did just this:
quote: ***Even in its earliest version XTree contained features like listing all files of a branch including subdirectories, listing of all files on a disk,***

My pictures are organized in dated sub-directories (or folders), 8 years of pictures, 120 folders, 3000 pictures. I could remove the sub-directories by hand but I would lose the organisation already in place.

More suggestions please?

---

### Post by MG&amp;TL on 2011-12-03
If I am right (and correct me if I am not), you could import your photos batch by batch into shotwell, and that should order them nicely. Could be wrong, though.

Alternative : (nice-ish) There is a batch renaming/editing/moving program I have used at one point that worked nicely; I can't remember what it was called, though. Googling. I think you could probably use that to view.

Alternative 2 : (okay)

1. open a terminal and type:

```
sudo apt-get install tree
```

And enter your password.

then wait for the text to stop scrolling.

2. Type 

```
cd <folder containing all the pics and subdirs>
tree | less
```

I imagine that is similiar to Xtree.


All due respect; what's wrong with shotwell and/or a file browser?

---

### Post by aneblanc on 2011-12-03
> **MG&TL said:**
> If I am right (and correct me if I am not), you could import your photos batch by batch into shotwell, and that should order them nicely. Could be wrong, though.

I have the pictures on a 8GB memory stick. They use 3.8GB. My free room on the SSHD is 2.7GB. Importing means copying, right? I use a Dell mini netbook. Or can I use Shotwell to sort the pictures right on the stick? How?

---

### Post by oldtimer7777 on 2011-12-03
> **aneblanc said:**
> I am looking for an application that would let me view all my pictures that I have in so many folders in only one folder in chronological order.

It would also be able to detect duplicates in order to delete them.

Any suggestion?

I personally love Google Picasa. And it has lots of simple but useful features included too.

It is about 1/2 the way down the following list to install it on your system:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Just install the PPA and you should be good to go.

---

### Post by aneblanc on 2011-12-03
> **oldtimer7777 said:**
> PPA ?

What does PPA it stand for?

Can I put put all my pictures in the cloud? Or do I still have to have them on the computer/stick?

---

### Post by oldtimer7777 on 2011-12-03
> **aneblanc said:**
> What does PPA it stand for?

Can I put put all my pictures in the cloud? Or do I still have to have them on the computer/stick?

If you want them in the cloud I would probably use something like Flickr instead.

A PPA is a way to add a repository from the command line in Ubuntu.  It is an instruction in the link I provided you above.

---

### Post by aneblanc on 2011-12-03
> **MG&TL said:**
> If I am right (and correct me if I am not), you could import your photos batch by batch into shotwell, and that should order them nicely. Could be wrong, though.


No you are right, it seems to do what I want, I have imported the 3000 pictures and can now see them in the order they were taken on one very long page.
I just did not know how to use Shotwell.
Thanks

---

### Post by c.cobb on 2011-12-03
> **oldtimer7777 said:**
> I personally love Google Picasa. And it has lots of simple but useful features included too.

Does it have the face recognition "feature" enabled by default as it does (or used to) on Windows? If so, can you easily disable that?

Several months before I switched over to Ubuntu, I upgraded to Picasa 3.something on WinXP, and it blew me away. I went out for a bit and, when I got back to my PC, I wondered why it was running so sluggishly. A new automatic face recognition feature had been running for five *hours* and had parsed about 2/3 of close to 30,000 photos -- there was no indication during the upgrade that this would happen, it was very difficult to figure out how to turn it off, and even more difficult to delete the generated "face galleries." 

There were half a dozen threads in the Picasa forums with users asking how to disable this and remove the face galleries, and no one had bothered to respond to any of their increasingly frustrated queries. Soon after this I removed Picasa, and haven't been back since.

---


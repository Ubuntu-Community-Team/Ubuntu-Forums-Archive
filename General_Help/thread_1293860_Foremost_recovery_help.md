---
title: "Foremost recovery help"
date: 2009-10-17
forum: General Help
---

### Post by acerunner on 2009-10-17
I am using Foremost to recover accidentally deleted data from a 2TB raid0 drive (of which, there is only 300GB used).

I dont know exactly what types of files were deleted so I can't specify ole, jpg, exe, etc. But I do know in what directory the files were deleted from.

Is there a way to specify in Foremost which directory to look in? Right now, it is scanning everything, and it is taking too long.

Also, are the outputted files EVERYTHING that it finds, or just stuff that was deleted, that NEEDED recovering? Right now looks like theres a lot of files being generated, and I think its more files than what was deleted at some point.

---

### Post by kidders on 2009-10-18
Hi there,

> **acerunner said:**
> But I do know in what directory the files were deleted from.That won't really help you, I'm afraid. Foremost is a forensic data recovery utility ... all it does is scan the surface of your disk for data that seems like the internal structures of certain well-defined file types that are easy to spot. As a result, some of what it recovers may well be nothing more than frankensteined chunks of old & new data that just happened to overlap in such a way as to seem like coherent files.

Foremost doesn't make any attempt to determine whether a file it spots has been deleted, where it belongs in the directory structure, or what it might be called.

Suppose you'd deleted a whole pile of JPEGs. One straightforward (but extremely time-consuming) way to determine which recovered files to keep, and which to toss away, would be to compute MD5 hashes of every JPEG on your system & compare them to the recovered files, deleting any matches. You'd be left with a set of images (or at least "potential" images) that don't currently exist. You could then perhaps try to construct decent filenames for them based on embedded EXIF information, leaving you with as little manual work as possible to do at the end.

I hope that helps.

---

### Post by acerunner on 2009-10-18
thanks for the info. Is there any alternative applications that would do a better job of recover the files in my situation, ie specify directory, and look for deleted files, or even just look for ALL files in one directory?

---

### Post by kidders on 2009-10-19
Off the top of my head I don't know of anything, so I did a little googling. There are a few references lying around to an undelete utility for Ext2 (by Lunetix), but I wasn't able to find the source code. Of course you might be using JFS or something ... in which case this reply is *doubly* useless to you!

Sorry I can't be more help. How much of your data is Foremost likely to recover, do you think?

---

### Post by acerunner on 2009-10-20
> **kidders said:**
> Off the top of my head I don't know of anything, so I did a little googling. There are a few references lying around to an undelete utility for Ext2 (by Lunetix), but I wasn't able to find the source code. Of course you might be using JFS or something ... in which case this reply is *doubly* useless to you!

Sorry I can't be more help. How much of your data is Foremost likely to recover, do you think?

it is ext3, so yes, there is journaling.

well, I have 300gb of data total. What was deleted was probably only about 10Mb, probably less. Foremost had started finding ALL the files before I realized that that's what it was doing. At that rate, I would have A LOT of files to sort through to find only 10Mb of files, especially when the resulting files aren't named with anything sensible.

---

### Post by kidders on 2009-10-20
Yep... sounds like using foremost would be inordinately time-consuming. That said, if you really need the stuff back, the sooner you do *something* the better, since the more you use your filesystem, the more likely it is that the space originally occupied by your deleted data will be overwritten by something else.

It's **miles** from ideal, but my best suggestion is to generate a gargantuan list of hashes of every file you'd expect foremost to find, run foremost & delete everything it recovers that matches something in your list. As I mentioned before, in theory you'd be left with nothing but deleted data ... or at least whatever percentage of it foremost was able to recover. With any luck, there wouldn't be very much to sort through.

In practice, you may find much of what you're left with is worthless (ie you deleted it on purpose months ago) or corrupt (because it's since been partially overwritten). Of course, all of this is academic if you don't have a spare 300GB disk to lying around. I suppose it all boils down to how many hours of your time the data is worth :-(

---

### Post by acerunner on 2009-10-20
I made sure to remove the drives from use as soon as the data was deleted. So nothing new was written. However, I did read a bunch of data and saved to another drive because I knew I would have to take this one off line until I recovered the data.

Can you tell me how to generate hash and have foremost match it?
Thanks!

---

### Post by kidders on 2009-10-20
I suppose you'd want to go for something reasonably wide (eg an SHA1 hash), to reduce the chance of a collision. Suppose you wanted to hash all your JPEGs. Something like this ought to do the trick ...```
find /path/to/raid/array -type f -iname "*.jpg" -exec sha1sum {} \; > hashes
```

Then, once you'd run foremost, you could try something like this to get rid of files you're not interested in ...```
for f in /path/to/recovered/jpegs/*; do grep "`sha1sum "$f" | cut -d" " -f1`" hashes > /dev/null && rm "$f"; done
```

Be careful though ... You'll probably have to run all this as root, so mistakes with quoting/etc. could be disastrous!

Once you were done, you could perhaps try constructing informative names for some of the files based on their metadata (eg embedded EXIF or ID3 data, etc). Even though you may only succeed 50% of the time (or less!), in your shoes, I'd try pretty much anything to avoid having to open file after file, just to see if what's in them looks worth keeping.

Is that any help?

---

### Post by acerunner on 2009-10-22
im a newb to linux. Can you explain what those two commands do exactly?

Also, how long does foremost take to scan 2TB? There's no % indication, it just listed files or "*******". Its been over 24hrs and still going.

---

### Post by kidders on 2009-10-22
> **acerunner said:**
> how long does foremost take to scan 2TB?I imagine how long it takes is down to disk performance. 24 hours is *much* longer than I would've guessed, though. If it doesn't finish pretty soon, you may have to start worrying about damaging the lifespan of your disks. :-(

> **acerunner said:**
> Can you explain what those two commands do exactly?The purpose of the first command is to generate SHA1 hashes of all your JPEGs ... it's just a quick example of the sort of thing I would do in your shoes. All the hashes are dumped into a file called "hashes". The man page for "find" will give you details on other options you might find useful.

My second example is more complicated ...

[LIST]
[*]**for f in /path/to/recovered/jpegs/*; do **- Begin a loop over all JPEGs recovered by foremost, using 'f' as a placeholder for the name of each file.
[*]**sha1sum "$f" | cut -d" " -f1 **- Compute the SHA1 hash of $f (a recovered file) and cut out the specific part of the output that contains the answer.
[*]**grep " ... ... " hashes **- Now that we have the hash of a recovered file, look through the giant list generated by my first example for a match.
[*]**> /dev/null **- Don't bother outputting anything unless an error occurs.
[*]**&& **- If the "grep" command does not successfully find a match, stop here.
[*]**rm "$f"** - Delete the recovered file.
[*]**; done** - End the loop.
[/LIST]
It's pretty long-winded, but seemed like a reasonably reliable way of re-deleting recovered data you are unlikely to be interested in.

---

### Post by acerunner on 2009-10-23
so after the 24+ hrs, turns out only ~100gb was read. Not a very good solution. So after some more research, seems there's a program called ext3grep that might do better recovering data. [http://code.google.com/p/ext3grep/](http://code.google.com/p/ext3grep/)

I'm gonna give that a shot, but I can't figure out how to take the tar, build and install it.

---

### Post by kidders on 2009-10-23
Yikes... that's a fraction of the speed I'm used to getting out of Foremost! There's little point in carrying on, I'd say.

I've never used ext3grep, so I don't know much about it. From what I've read, it's at least worth a shot! What's the problem with the version in Ubuntu's repos? Is it buggy?

---

### Post by az on 2009-10-23
> **acerunner said:**
> I am using Foremost to recover accidentally deleted data from a 2TB raid0 drive (of which, there is only 300GB used).


Photorec is another file carver.  It can use some information from your filesystem to help get back files.  For example, it can handle some fragmentation.

It can also restrict itself to looking only in the unallocated spots of your filesystem.

Since the deleted files you are looking for are in the unallocated space, that's what you want to use.  It's curses and menu driven.  One of the last questions it asks before searching is whether you want to search the whole filesystem or just the unallocated space:

(see image)

---

### Post by acerunner on 2009-10-27
> **kidders said:**
> Yikes... that's a fraction of the speed I'm used to getting out of Foremost! There's little point in carrying on, I'd say.

I've never used ext3grep, so I don't know much about it. From what I've read, it's at least worth a shot! What's the problem with the version in Ubuntu's repos? Is it buggy?

i was unable to install using ubuntu repositories.
i used "sudo apt-get install ext3grep", but i get "Couldn't find package ext3grep".
i tried enabling universe and multiverse repositories too, same results.
i tried the synaptic package manager, but ext3grep was not found.

is there anywhere else i should be looking?
btw, i'm running off a live CD version of ubuntu 8.04 lts.

---

### Post by acerunner on 2009-10-27
> **az said:**
> Photorec is another file carver.  It can use some information from your filesystem to help get back files.  For example, it can handle some fragmentation.

It can also restrict itself to looking only in the unallocated spots of your filesystem.

Since the deleted files you are looking for are in the unallocated space, that's what you want to use.  It's curses and menu driven.  One of the last questions it asks before searching is whether you want to search the whole filesystem or just the unallocated space:

(see image)

does that software search for more than just photos?
nevermind, found the answer. it does.

i'm trying it now, but photorec doesn't show the md raid drive, just sda and sdb. I do have the raid assembled. same results whether mounted or not.

---

### Post by kidders on 2009-10-31
> **acerunner said:**
> i'm running off a live CD version of ubuntu 8.04 lts.That explains it ... ext3grep is [only available in Jaunty & Karmic]("http://packages.ubuntu.com/search?keywords=ext3grep&searchon=names&suite=all&section=all"). Building from source is probably your best option, if you want to use it.

> **acerunner said:**
> photorec doesn't show the md raid drive, just sda and sdb.Weird... it ought to... maybe az can help you there.

---

### Post by NCLI on 2009-10-31
> **kidders said:**
> Yikes... that's a fraction of the speed I'm used to getting out of Foremost! There's little point in carrying on, I'd say.

I've never used ext3grep, so I don't know much about it. From what I've read, it's at least worth a shot! What's the problem with the version in Ubuntu's repos? Is it buggy?
ext3grep is great, I highly recommend it.

---

### Post by Beachside on 2009-11-11
> **acerunner said:**
> I am using Foremost to recover accidentally deleted data from a 2TB raid0 drive (of which, there is only 300GB used).

I dont know exactly what types of files were deleted so I can't specify ole, jpg, exe, etc. But I do know in what directory the files were deleted from.


Try googling "Data Recovery on Linux and ext3".  My top hit was an article written by Abe Getchell.  You can use debugfs (included in Ubuntu) and ls -d (once you're in debugfs and in the dreaded directory) to view deleted files.  I deleted a couple files and following Abe's instructions was able to view them and the location (inode) you can then carve them specifically with the other tools mentioned.  I have not continued to the carving yet...

WARNING: I'm an amateur in ubuntu and you'll be playing with root, so be careful.  And apologies to the Ubuntu god if I'm not supposed to share other sites.  But this seems to be a common pain in the @#$.  Smack me if you must.  Cheers!

---


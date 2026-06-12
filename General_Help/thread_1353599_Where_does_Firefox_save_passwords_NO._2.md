---
title: "Where does Firefox save passwords? NO. 2"
date: 2009-12-12
forum: General Help
---

### Post by Silvernail on 2009-12-12
There is another thread by this name. I did at he had done. When I got to Edit > Preferences > Security, Stored Password is empty.

When I dig down to the signons3.txt file:

-rw------- 1 dafy dafy    27939 2009-12-12 22:16 signons3.txt
-rw------- 1 dafy dafy      771 2009-12-12 22:15 signons3.txt.backup
The one I copied over is larger than the backup.

In Edit > Preferences > Security, Import passwords did not work.

If I do a 'cat' on 'signon3.txt' I get a screen full of garbage which is correct because  it is encoded.

I did not change any permissions on this.... Are they involved?

I had the same problem trying to bring bookmarks over to the new installation. Not successful on those either.

Anyone got another direction I can go?

Thanks in advance for any help you can offer.
Dave

---

### Post by sgosnell on 2009-12-13
What version of firefox?  For 3.0, you have the right file.  For 3.5 and up, it's in signons.sqlite.  It also requires key3.db in order to work, for either version.  I don't know the details of that.

If you want to get your passwords from one installation to another, xmarks is a good way to do that, as well as your bookmarks.  Xmarks will sync both, and you can sync them back to any other firefox installation you like.

---

### Post by Silvernail on 2009-12-13
I will try  your suggestion.

I may have run across the problem elsewhere.

Thunderbird is giving me the same problem. Show the file is copied but will not display.

I just went to Open Office to read a email address and it would not let me copy it.

I got an email that I wanted to forward. Normally the text is displayed. This time not, the attachment showed.

It appears that some flay got set during installation that will not let me do these things.

These are just some thoughts. Any comments.
Dave

---

### Post by Silvernail on 2009-12-13
> **sgosnell said:**
> What version of firefox?   3  > It also requires key3.db in order to work, for either version.

I am going from 8.04 with all the upgrades to 9.04 with all 266 upgrades.
Will the 9.04 key3.db work or do I need to bring the 8.04 one along?

---

### Post by Silvernail on 2009-12-13
Moving along on this.  I use the command line 'ncftp' to moves stuff to my website server. Now I can not connect.

Command line: ncftp tff
```
tff,www.texasflyfishers.org,example,*encoded*example,I,21,\
219768477,1,1,-1,1,67.15.213.8,,,,,,S,-1
```use to work  just fine.

I wanted to read  the configure file '.ncftp' with 'gedit', 'cd' to directory, 'gedit bookmark', error permissions error. Never happened before.

When I made the new installation/upgrade last week I copied my entire home directory to an external hard drive and have been copied back what I wanted/needed. This config directory was such an item.

This is beginning to look like a 'read' problem in the OS. Several places the data is there and can be verified by size of file and 'cat' on the content. Does not display/read via a GUI.

---

### Post by sgosnell on 2009-12-14
> Will the 9.04 key3.db work or do I need to bring the 8.04 one along?
I don't know.  I've never tried to do what you're trying to do.  I got the information from a Google search, especially [this page]("http://kb.mozillazine.org/Profile_folder_-_Firefox").

---


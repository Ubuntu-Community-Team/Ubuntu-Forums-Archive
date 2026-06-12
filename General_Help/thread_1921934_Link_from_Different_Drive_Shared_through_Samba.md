---
title: "Link from Different Drive Shared through Samba"
date: 2012-02-07
forum: General Help
---

### Post by jamesisin on 2012-02-07
I have a server for my music and whatever else not with a pair of 1.5 TB drives as the storage.  One of those drives is essentially the music.  On that drive is a share (let's call it Music) with all of my music.  I've run out of space and my idea was to create a folder on the other drive where I could house some of the music and merely link to it from the Music (shared) folder.

This of course doesn't work (the links appear in the share but are broken).

What's the right way to do this?

Here is the basic setup:

/media/DriveA/ & /media/DriveB/
/media/DriveA/Music/ which contains folders we'll call A, B, C, and D with links E and F
/media/DriveB/OtherMusic/ which contains E and F

(DriveB does contain other stuff but in different directories.)

In the end I would want to be able to connect to Music (through Samba) and have access to A through F.

---

### Post by jamesisin on 2012-02-08
I know you're looking.  Any suggestions?  Best practice...

---

### Post by jamesisin on 2012-02-08
Maybe even just telling me what this is called so I can run a more focused search?

---

### Post by jamesisin on 2012-02-08
Help?

---

### Post by HiImTye on 2012-02-08
you need to enable symlinks
```
gksudo gedit /etc/samba/smb.conf
```
somewhere after where it says [Global], add:
```
    unix extensions = no
    wide links = yes
```
then restart samba
```
sudo restart smbd
```

---

### Post by jamesisin on 2012-02-08
Thanks.  Took a couple tries to get the placement correct but it's working perfectly.

The links=yes makes sense, but what does the UNIX=no do?

For those interested, as stated it goes below Global.  I tried putting right above the shares I had created at the bottom of the file and that didn't seem to work.  So I put at what I surmise is the bottom of the Global section (right before ;[HOMES]) and that worked.

---

### Post by HiImTye on 2012-02-08
> **jamesisin said:**
> The links=yes makes sense, but what does the UNIX=no do?
it closes a security hole introduced by enabling wide links

---

### Post by jamesisin on 2012-02-10
This one?

[http://bugs.contribs.org/show_bug.cgi?id=4164](http://bugs.contribs.org/show_bug.cgi?id=4164)

---

### Post by capscrew on 2012-02-10
> **jamesisin said:**
> This one?

[http://bugs.contribs.org/show_bug.cgi?id=4164](http://bugs.contribs.org/show_bug.cgi?id=4164)

No, but it seems to have helped there too.

---


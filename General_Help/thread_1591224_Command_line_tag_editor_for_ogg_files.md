---
title: "Command line tag editor for ogg files"
date: 2010-10-08
forum: General Help
---

### Post by oldmankit on 2010-10-08
I had a great system going with a bash script to update all of my mp3 files' genre tags.

Now that my music collection is ogg, id3v2 doesn't work.

Can anyone recommend a command line tool to edit tags for ogg files please?

---

### Post by oldmankit on 2010-11-02
The question:

Can anyone recommend a command line tool to edit tags for ogg files please?

*bump*

---

### Post by Vaphell on 2010-11-03
google returns lltag and vorbiscomment (vorbis-tools package)

```

apt-cache search lltag
lltag - Automatic command-line mp3/ogg/flac file tagger and renamer

apt-cache search vorbiscomment
vorbis-tools - several Ogg Vorbis tools

```

---

### Post by luigi_mb on 2010-11-03
> **oldmankit said:**
> I had a great system going with a bash script to update all of my mp3 files' genre tags.

Now that my music collection is ogg, id3v2 doesn't work.

Can anyone recommend a command line tool to edit tags for ogg files please?

Get extm3u.pl from

[http://www.splitbrain.org/projects/extm3u](http://www.splitbrain.org/projects/extm3u)

Read the documentation, and make sure you install first the perl modules required. 

/luigi

---

### Post by oldmankit on 2010-11-04
> **Vaphell said:**
> google returns lltag and vorbiscomment (vorbis-tools package)

```

apt-cache search lltag
lltag - Automatic command-line mp3/ogg/flac file tagger and renamer

apt-cache search vorbiscomment
vorbis-tools - several Ogg Vorbis tools

```

You must be better with google than me.  Thanks!

Currently I can find no way to simply replace one tag without any confirmations.  I cannot confirm each time I want to tag a file when I have thousands of files to tag in one go.

I have put a request on the lltag homepage to see what they can do.

---

### Post by Vaphell on 2010-11-04
```

**lltag --help**
some stuff
[b]--yes                  Tag without asking for confirmation when guessing
                       Rename without asking for confirmation[/b]
some stuff

```

armed with that knowledge try
```
lltag -a MY_ARTIST_NAME --yes *.ogg
```

---

### Post by oldmankit on 2010-11-05
> **Vaphell said:**
> ```

**lltag --help**
some stuff
[B]--yes                  Tag without asking for confirmation when guessing
                       Rename without asking for confirmation[/B]
some stuff

```armed with that knowledge try
```
lltag -a MY_ARTIST_NAME --yes *.ogg
```

Well what do you know, that worked!

I spent about half an hour going through the man stuff but couldn't get it to work.  I was using

```
lltag -E -g alternative --yes 01-hope\ there\'s\ someone.ogg
```which requires confirmation.  When I got rid of -E, it didn't ask for confirmation.  I'm not sure why, but at least it works now.

---


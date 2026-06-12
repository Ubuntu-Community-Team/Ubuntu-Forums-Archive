---
title: "Banshee Library Problem"
date: 2011-07-23
forum: General Help
---

### Post by jamesisin on 2011-07-23
I am moving to Banshee on all of my 10.04 systems (anticipating the future of Ubu).  Banshee has been doing something I don't understand and which seems very wrong (and which is actually causing some problems, if minor).

First let me explain the arrangement.

I have a server with a music share we'll call server:/tunes.

On all of the machines and for all the users there is a mount (/media/tunes/) for said share.  Additionally so that all users have the same transparent experience, each user has a shortcut at ~/Music/tunes (which points to /media/tunes/).

Through this I don't need to alter the default library location and all of the music on the server is automagically part of every library (and all library content and playlists have the same paths).

However, Banshee has decided for some files to do one of three things:

1. It points (correctly) to only ~/Music/tunes/path/to/song.flac
2. It points (wrongly) to only /media/tunes/path/to/song/flac
3. It points to both and there is a duplicate entry

I have not knowingly given Banshee the path /media/tunes/anything.

What is going on and how might I correct this?

---

### Post by jamesisin on 2011-07-24
Calling all Banshee experts...

---

### Post by jamesisin on 2011-07-24
Well on one machine it's all /media/tunes...

How is Banshee doing this?  Working backward from the link?  This seems odd behavior to me.

---

### Post by jamesisin on 2011-07-25
Anybody?

---

### Post by jamesisin on 2011-07-28
Clearly the default behavior of Banshee is to parse the link (though this does seem odd behavior), but why is it creating these random duplicate entries?  And why aren't *all* files represented with the cross-linked path?

Does anyone but me care about this?

---

### Post by jamesisin on 2011-08-04
I don't know if they are related but I'm also having trouble with imported playlists:

[http://ubuntuforums.org/showthread.php?p=11118553](http://ubuntuforums.org/showthread.php?p=11118553)

---

### Post by dniMretsaM on 2011-08-04
Are your settings in Edit -> Preferences -> Source Specific all correct?

---

### Post by jamesisin on 2011-08-04
Yes they are.  They are the default.  I merely add a shortcut (pointing to /media/[share]/) into the ~/Music folder.  It's set like this on all machines.

I don't understand why it's parsing the shortcut in most cases.

This laptop I am on currently seems to show all tracks as /media/[share]/... while I would think it should show them all as ~/Music/[share]/....

(The machine which shows the combinations and duplicates is the machine I am trying to make the playlists import.)

---

### Post by jamesisin on 2011-08-04
I believe I have sorted out the matter:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/08/banshee-its-library-and-importing-playlists/](http://jamesisin.com/a_high-tech_blech/index.php/2011/08/banshee-its-library-and-importing-playlists/)

I would still like to understand *why* Banshee parses the link though.  If anyone knows please pass that on to me.

---


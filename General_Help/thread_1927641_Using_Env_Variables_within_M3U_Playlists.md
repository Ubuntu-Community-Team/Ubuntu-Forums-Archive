---
title: "Using Env Variables within M3U Playlists"
date: 2012-02-18
forum: General Help
---

### Post by jamesisin on 2012-02-18
I wanted to set up some playlists along with the music on my server that would be usable by all users on the network.  All users have a path to the music thus:

```
/home/[username]/Music/[share]/...
```

My idea was to use this in the playlists:

```
$HOME/Music/[share]/...
```

I also tried using this:

```
/home/$USER/Music/[share]/...
```

I guess this is because only the shell could interpret those variables and Movie Player isn't passing that variable to the shell (instead trying to find that location itself).

Is this not possible or is my method just out of alignment?

(I also tried using ~/ and using VLC, GNOME Mplayer, Brasero, and Rhythmbox none of which could parse any of the three methods.)

---

### Post by jamesisin on 2012-02-18
Ok, that took a bit but I have it sorted now.

I have my playlist files in the same directory as the music; they are in a subfolder once removed from the root of the music share.  In other words if I rise two directories I can use relative paths to all the music on the share.

The proper format is thus:

```
../../path/to/each/song.flac
```

Here is a decent if Windows centric discussion of building these playlist files:

[http://en.wikipedia.org/wiki/M3U](http://en.wikipedia.org/wiki/M3U)

I'll probably write something up on my blog at some point.

---


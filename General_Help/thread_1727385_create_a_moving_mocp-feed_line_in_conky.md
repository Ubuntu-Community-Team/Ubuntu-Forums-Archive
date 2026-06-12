---
title: "create a moving mocp-feed line in conky"
date: 2011-04-12
forum: General Help
---

### Post by debd on 2011-04-12
Please read on till the end before you think where's the damn problem and get angry on me :).

I've been using the command line music player moc for some time now & am in love with it. So, I thought it'd be nice if I can add a current track info feed to my conky display. Therefore, I have this smple script that gets the track info from mocp -i .

```
#!/bin/sh

  TITLE="`mocp -i | grep 'Title:' | sed -e 's/^.*: //'`";
  if [ "$TITLE" != "" ]; then
    ARTIST="`mocp -i | grep 'Artist:' | sed -e 's/^.*: //'`";
    SONGTITLE="`mocp -i | grep 'SongTitle:' | sed -e 's/^.*: //'`";
    ALBUM="`mocp -i | grep 'Album:' | sed -e 's/^.*: //'`";
    if [ "$ARTIST" != "" ]; then ARTIST="$ARTIST - "; fi
    if [ "$ALBUM" != "" ]; then ALBUM="($ALBUM)"; fi
    echo $ARTIST $SONGTITLE $ALBUM
  else echo MOC not running
  fi
```

You can saved this sh-script as mocp.sh in your home folder and add the following line in your .conkyrc file:

${execi 10 ~/mocp.sh | fold -w55 -s}

But here comes the point. The way the track info is shown feels kind of blunt. I was wondering if something can be done either in the script or in conkyrc so that the track info is shown in a single line, moving backward at a constant speed; like you know, news channels show news strips at the bottom of the screen ;).

If any solution's possible please suggest.

Thank you.

---

### Post by debd on 2011-04-12
Anyone? 
I believe there are  many conky and shell  gurus out there :)

---

### Post by SabreWolfy on 2012-06-04
I think that would be very complicated to do. You would have to call a script every second and it would have to know which letters are currently being shown in order to know which letters to show next.

FWIW, instead of your "sed" complications above, what about:

```

mocp -Q %title

```

to get the title? :)

**Edit:** Despite the documentation indicating that "%title" returns the title, this in fact seems to return the album, artist and track number as well. "%t" returns the title.

**Edit:** For information [here]("http://crunchbanglinux.org/forums/post/228131/#p228131").

You can also use 'pidof' to determine if mocp is running. Check the exit status of 'pidof mocp' for example.

---


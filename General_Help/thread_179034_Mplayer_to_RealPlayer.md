---
title: "Mplayer to RealPlayer"
date: 2006-05-18
forum: General Help
---

### Post by majkmil on 2006-05-18
After a dapper upgrade streaming video works on some sites in firefox but not in others, ie. NFL.com. Ithink I would like to use RealPlayer 10 for streaming, can someone please show me how to change from Mplaye to RealPlayer in firefox.   Thanks

---

### Post by badrinarayan on 2006-05-19
You can turn off the realplayer emulation in mozilla-mplayer by changing the options. To do so, go to a web site that plays streaming video through your mplayer (like say, Apple Trailers), right click on the embedded player and click on "Configure" on the context menu. You can turn off Realmedia/SMIL/Helix emulation in the dialog box that pops up. I have attached a screenshot

**Alternative Method:** I must add that you can also edit a text file to accomplish the same.
```
gedit .mplayer/mplayerplug-in.conf
```

Now change the lines
```

enable-rm=1
enable-smil=1
enable-helix=1
```

to 

```

enable-rm=0
enable-smil=0
enable-helix=0
```

Why is this in the Warty Forum if it is a Dapper Question?

---

### Post by majkmil on 2006-05-19
Thanks, When I go to nfl.com and right click on the emdeded player I changed the video option to (vo). It works now with realplayer. When I went back to cnn I had to change it back to xv I think. Do some site just require realplayer because I am sure mplayer worked at nfl.com in breezy. Sorry I thought I was in video threads not warty.

---


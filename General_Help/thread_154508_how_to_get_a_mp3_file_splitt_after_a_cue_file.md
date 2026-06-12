---
title: "how to get a mp3 file splitt after a cue file?"
date: 2006-04-03
forum: General Help
---

### Post by syklitengutt on 2006-04-03
I have a mp3 file and I have a cue file.
Is it possible to split the mp3 file after what the cue file is
saying without burning it...

---

### Post by syklitengutt on 2006-04-03
I found one prog, but it depended on some newer libs than what I had...
Any ideas people?
I really dont wonna burn the cds and then rip them.

Have to be a faster way.....

---

### Post by Tiede on 2006-04-03
DELETED - Wrong info given... Sorry.

-- Try cdemu, maybe...

---

### Post by lcg on 2006-04-03
[QUOTE=syklitengutt]I have a mp3 file and I have a cue file.
Is it possible to split the mp3 file after what the cue file is
saying without burning it...[/QUOTE]
Ever heard of Google? It's been around for a while and it's a really great tool! ;)
Google "linux mp3 split", first result: [http://mp3splt.sourceforge.net/](http://mp3splt.sourceforge.net/)

The program is even available in the repositories:
```
[lars@localhost] ~ > apt-cache search mp3splt
mp3splt - Splits MP3 and Ogg Vorbis files without reencoding
```

HTH,
Lars

---

### Post by syklitengutt on 2006-04-04
yes Ive heared about google, and I have tried to isntall that.
But for having a gui it depends on some other stuff wich I have a lower version
off...

---

### Post by lcg on 2006-04-04
> **syklitengutt]yes Ive heared about google, and I have tried to isntall that.[/QUOTE]
The Google remark wasn't meant to offend you (that's why it had a  said:**
> But for having a gui it depends on some other stuff wich I have a lower version off...
OK, you asked for a tool to split MP3s, not for a GUI. But just out of curiosity, is there a reason why you don't use a command line tool? The usage is pretty simple (assuming that both the MP3 and the CUE file are in ~/music):
```
cd ~/music
mp3splt -c album.cue album.mp3
```
Judging from the screenshot on the site, it probably takes quite a bit longer to reach the same goal with the mouse.

HTH,
Lars

---

### Post by syklitengutt on 2006-04-05
tnx lcg...
That worked...
I didnt understand out of the howto to use the cue file....
Took 15 secs.... nothing more....
Im not converted from win to linux yet... Still a gui sucker....

---

### Post by lcg on 2006-04-06
[QUOTE=syklitengutt]tnx lcg...
That worked...
I didnt understand out of the howto to use the cue file....[/QUOTE]
Yes, reading man pages takes a bit of practice. They usually contain so much information that finding what you're looking for can be difficult at times. 'man bash' is the best (worst?) example for that.

Two tips:
[LIST=1]
[*]When reading a man page (e.g. 'man mp3splt'), you can search for a word (e.g. 'cue') by hitting /
[*]When working with a modern shell (like bash, zsh, ...), make excessive use of tab completion, i.e. whenever you have typed part of a command or filename, hit tab. The shell will then complete for you as much as possible.
[/LIST]

[QUOTE=syklitengutt]Took 15 secs.... nothing more....[/QUOTE]
Splitting MP3s shouldn't be too hard. The tool just writes frames to different files sequentially and adds the necessary headers.

[QUOTE=syklitengutt]Im not converted from win to linux yet... Still a gui sucker....[/QUOTE]
If you want my advice: don't cling to GUI tools for the GUI's sake. Use the best tool for a job (i.e. it gets the job done in the shortest time and with the least possible effort on your end).
Computers are tools, helping us to get work done, and an operating system is basically just a layer between the software you need to get something done and the hardware you have. Lots of people forget that when they are starting a flame war of Linux vs. Windows vs. whatever.

HTH,
Lars

---


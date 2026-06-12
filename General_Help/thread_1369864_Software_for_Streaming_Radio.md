---
title: "Software for Streaming Radio"
date: 2010-01-01
forum: General Help
---

### Post by aV Echelon on 2010-01-01
Is t here any app in Ubuntu that is equivalent to Mac's [Radioshift]("http://www.rogueamoeba.com/radioshift/")?

---

### Post by HiImTye on 2010-01-01
you can listen to webradio in most players. exaile lets you record if you add streamripper from the repositories
```
sudo apt-get install streamripper
```

---

### Post by ajgreeny on 2010-01-01
Realplayer streams such as the BBC radio uses, can not be recorded, however, with streamripper, or at least I have never managed to do so.  You can use mplayer to do it however, quite easily.
```
mplayer -cache 2048 mplayer -playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram -vc null -vo null -ao pcm:fast:waveheader:file=outfile.wav
``` saves real or other stream as file outfile.wav. Just watch out for the possible need to add **-playlist <URL>** instead of just **<URL>** in the command.  It depends on exactly how the stream is sent from the site.  The BBC certainly needs it.

Mplayer will also record mp3 streams with ```
mplayer <URL> -dumpstream -dumpfile stream.mp3
``` and I use gnome-mplayer to listen to mp3 streams as well with ```
gnome-mplayer <URL>
```as a shell script.  Much simpler than running a web-browser just to listen to radio.  This also works for the realplayer streams with ```
gnome-mplayer --playlist http://www.bbc.co.uk/radio2/realmedia/fmg2.ram
```Note the need again for the **--playlist** (two -- for gnome-mplayer, as opposed to just one - for mplayer itself.

---

### Post by aV Echelon on 2010-01-04
Ahh, perfect. =]

Would you guys happen to know where I would find the url for the streams?

---

### Post by ajgreeny on 2010-01-04
Sorry, but that's a rather silly question.  There are thousands and thousands of streams available in the world of broadcasting and we have no idea what you want to listen to or record.

Try **streamtuner** for a start and you may find something useful and to your taste.

---


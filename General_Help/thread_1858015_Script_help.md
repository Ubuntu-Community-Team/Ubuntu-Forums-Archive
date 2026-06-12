---
title: "Script help"
date: 2011-10-11
forum: General Help
---

### Post by layzie on 2011-10-11
Hello folks!

I'm pretty much an abosulute beginner when it comes to using the linux terminal. I am converting my videocameras .MTS files into .avi files with the following command:

$ mencoder 00001.MTS -o 1.avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720

But I have over 200 videos to convert and it's super slow doing it one by one, changing the .MTS file and .avi file name every single time...

So I was wondering if anyone could help me by writing some kind of simple script. Just to convert 00001.MTS -> 1.avi, 00002.MTS -> 2.avi etc. with one command so I could just leave the computer to do it during the night.

Thank you so much!

---

### Post by AlphaLexman on 2011-10-11
```
for FILE in *.MTS; do OUTFILE=$(echo "${FILE}" | sed 's/\.MTS$/.avi/g'); mencoder ${FILE} -o ${OUTFILE} -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720; done
```

---

### Post by Vaphell on 2011-10-11
slightly too late but very similar and more compact
```
for f in *.MTS; do **echo** mencoder "$f" -o $((10#${f%.*})).avi -oac copy -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=10000 -fps 50 -vf scale=1280:720; done
```

at first it will print out the commands to run to make sure you get what you want, if you want to actually run it, remove echo in bold font

edit: i think ${FILENAME} should be ${FILE} in AlhpaLexman's command - as it stands FILENAME is not defined anywhere

---

### Post by layzie on 2011-10-11
Thank you guys!

---


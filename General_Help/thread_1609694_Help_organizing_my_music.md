---
title: "Help organizing my music?"
date: 2010-10-30
forum: General Help
---

### Post by ispy on 2010-10-30
My music collection has gotten rather out of hand lately, and I'm interested in organizing from scratch from the bare mp3s. I figured the best way to do this would be to just cp all the files out of the rat's nest of directories and use banshee or something to organize them in a more sensible manner. But, cp does not have the ability to recursively copy files, only directories. So the question I ask you is this: How do I rescue my music, from the command line, if possible.

Note: Tried FSLint, it took way to much time, and I have about 20 gigs of music to organize with several of those being duplicates.
I'm using CrunchBang, if it matters.

---

### Post by blueridgedog on 2010-10-31
```
find /home/USER/Music -iname "*.mp3" -exec mv {} /home/USER/NewMusicFolder \;
```

Where USER is your user name and NewMusicFolder is where you want to put the files.  Be certain that the path in the find command does not contain the new destination for the files our you could get a loop that would be bad.

For more info:

[http://www.cyberciti.biz/tips/howto-linux-unix-find-move-all-mp3-file.html](http://www.cyberciti.biz/tips/howto-linux-unix-find-move-all-mp3-file.html)

Note that you could use songbird or easytag to manage your files as well.

See these results for more information:

[http://www.google.com/search?aq=f&sourceid=chrome&ie=UTF-8&q=site:ubuntuforums.org+mp3+find#sclient=psy&hl=en&source=hp&q=site:ubuntuforums.org+mp3+organize&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=ddfbf15c2e2f4021](http://www.google.com/search?aq=f&sourceid=chrome&ie=UTF-8&q=site:ubuntuforums.org+mp3+find#sclient=psy&hl=en&source=hp&q=site:ubuntuforums.org+mp3+organize&aq=f&aqi=&aql=&oq=&gs_rfai=&pbx=1&fp=ddfbf15c2e2f4021)

---


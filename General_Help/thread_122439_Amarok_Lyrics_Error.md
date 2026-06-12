---
title: "Amarok Lyrics Error"
date: 2006-01-27
forum: General Help
---

### Post by Downtown on 2006-01-27
Hey folks.  I'm using Amarok 1.4 to play my mp3 library, but I can't view the lyrics.  When I click on the lyrics tab, this shows instead of the lyrics...

"Sorry, no lyrics script running.

Available Lyrics Scripts:
lyrics_astraweb.rb
lyrics_lyrc.rb

Click on one of the scripts to run it, or use the Script Manager, to be able to see all the scripts, and download new ones from the Web."

I run the Script Manager to force the scripts to run, but I get an error that says...

"The script 'lyrics_lyrc.rb' exited with error code: 127

Details:
/usr/bin/env: ruby: No such file or directory"

I know nothing about scripting, so I don't know where to start.

Any help?

---

### Post by Neo Ex on 2006-01-27
amaroK 1.4?
The latest amaroK release is 1.3.8 :confused: 
I'm using this one and I have no problem seeing lyrics. I hadn't to download and install any lyrics script (in the Script Manager I don't have any lyrics script, but I can see them anyway).

---

### Post by Downtown on 2006-01-27
I double-checked.  It's 1.4SVN.  Is that a different version?  From what I've read while researching to try to fix it myself, the newer versions are gonna depend more on scripts.

---

### Post by Lord Illidan on 2006-01-27
You are using an unstable development version... which is bleeding edge. The latest stable is 1.38

Now, about your problem. All you need is ruby... just do 

```
sudo apt-get install ruby
```

Cheers!

---

### Post by Downtown on 2006-01-27
Sweet!!! Thanks a bunch.

---


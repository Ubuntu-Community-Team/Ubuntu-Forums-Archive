---
title: "Help running a .sh file"
date: 2009-11-25
forum: General Help
---

### Post by stevedub40 on 2009-11-25
Hello guys, I am sure you hear this quite often, I am very new to Linux and Unbuntu.  I have been playing around with using the command line and have been slowly progessing.  I have managed to download PS3 media server and have extracted the tar to the user/local/src folder.  I am having trouble running the PMS.sh file.  I first did a chmod +x PMS.sh, but that did not seem to work.  I then tried sh PMS.sh and it says I can't open the PMS.sh file, so I am assuming I need to change the permissions.  Any help would be greatly appreciated and I would like to say thanks for such a great community.

---

### Post by BenAshton24 on 2009-11-25
**sudo** chmod +x PMS.sh
**sudo** ./PMS.sh

---

### Post by stevedub40 on 2009-11-25
I think I have figured it out. I needed to add one more layer in the path /usr/local/src/pms-linux-1.10.5, after moving to this cd I was able to run the PMS.sh.  I think I am getting the hang of this stuff!

---

### Post by stevedub40 on 2009-11-25
Ok, now my next task this is taken from the readme:

Transcoding on Linux: HOWTO 
=========================== 
 
You just need to have mplayer, mencoder and ffmpeg binaries on your path (the more recent, the better). 

I am not sure what is meant by this or how to include the binaries on my path.  Any suggestions?

---


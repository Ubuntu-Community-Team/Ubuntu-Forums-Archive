---
title: "add/remove program"
date: 2010-06-20
forum: General Help
---

### Post by Hakuna Matata on 2010-06-20
Hello I am a complete newbie to Ubuntu :)
Anyhow i downloade google chrome from the google chrome website, and now would like to delete it. However it doesn't appear in the ubuntu software center, and i have no idea how to delete it. Please help

---

### Post by Pollox on 2010-06-20
You downloaded it, but did you actually install it?  It should appear in Add/Remove if you type in chrome and look for the entry with a green check mark.  You can also remove it via Synaptic Package Manager, or in terminal by using the command "sudo apt-get remove google-chrome-stable".

---

### Post by gdonwallace on 2010-06-20
My first question would be was the download a .deb file?  If it was, then You should be able to find it in synaptic package manager.

If it was a zip file, then the unzipped program will be in whatever directory you did that in.  The other option is that there was an install program in the zip file.  If that is the case, then it is likely that the program "installed" in /opt.  If so, check /opt for a Chrome directory and remove it. (sudo rm -r <dir name>)

---


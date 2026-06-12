---
title: "Creating a button to execute script"
date: 2009-10-06
forum: General Help
---

### Post by supahamster on 2009-10-06
I am new to Ubuntu (about 3-4 weeks). So far it's been great, except that when I plug in headphones, the speakers continue playing. I have solved this problem by manually muting the front speaker, but I would like to (for learning as well as ease of access) create a button to execute a macro to change these settings.

Most tutorials I have found have been either too simple or way above my head. Can anyone point me towards some good tutorials or give any advice about how to start doing this?

I know that I need to find where the settings for alsamixer are stored, but mainly what I want to know is how to go about creating a custom button to execute some shell on the panel.

---

### Post by yeeeev on 2009-10-06
First check out the following post: [http://ubuntuforums.org/archive/index.php/t-1113779.html](http://ubuntuforums.org/archive/index.php/t-1113779.html)
If you still want to create a script launcher, you need to create a script that mutes the front speaker, make it executable.
Right-click on the panel and add a "custom application launcher", and use it to run a script.

---

### Post by supahamster on 2009-10-07
Thanks, but your link wasn't very helpful (I have already done a lot of research about this). Anyways, even if I solve this, I want to figure out how to execute a script to become more familiar with ubuntu ;)
What are the advantages to using .exe over executing a text file?

---

### Post by yeeeev on 2009-10-08
I wasn't talking about ".exe" at all. Sorry if you misunderstood me.
What I'm suggesting is:
* Create a bin directory under your home directory and put all your scripts there. It is usually added automatically to the system's path when you log in. You may have to logout and login for that to take effect, not sure.
* Create a script in that directory. Simply run "gedit ~/bin/scriptname.sh" (or any other text editor) and then make sure the first line is "#!/bin/bash" followed by the actual bash script.
* The give the script execution permissions by running "chmod +x ~/bin/scriptname.sh"
* Then you can run it by typing "scriptname.sh"

I hope now I'm clearer...

---


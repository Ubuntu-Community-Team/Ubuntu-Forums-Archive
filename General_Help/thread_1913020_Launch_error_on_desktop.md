---
title: "Launch error on desktop"
date: 2012-01-21
forum: General Help
---

### Post by geovino on 2012-01-21
I installed Xubuntu 11.10 64bit this morning and when trying to open the Home or File System icon on the desktop it takes a while and then I get this error:

The folder could not be opened
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Then they finally open. Never seen this before. How can I fix this problem?

---

### Post by imachavel on 2012-01-21
so you try and open home, then it gets that error? Then it finally opens? Well if it opens I don't know.

could be some malformed code thinking the system is trying to do something else besides open the folder. If it opens then it fixes itself. Please open terminal = ctrl+alt+t and then type

sudo apt-get install update

I don't know if that will fix it. I wish the error was more detailed then that. Are you trying to open home from the host, or from another computer on the network?

---

### Post by Claus7 on 2012-01-21
Hello,

have you seen if you accidentally have changed something on the command that you can find under properties of the icons?

Just a thought.

Regards!

---

### Post by geovino on 2012-01-21
who knows what it was.... but its working now.

---

### Post by geovino on 2012-01-22
Today its doing the same thing again. Clicking on Home or File System icon and it takes 30 seconds to open.

I don't know what could be hanging it up?

Any clues?

---

### Post by Claus7 on 2012-01-22
Hello,

make a new icon and see if it does the same. 

I remember that I had some ...conflicts when I had upgraded my system and I had to fix the paths or so (it is long ago). Yet, this was happening all the time if I recall correctly. Have you made an upgrade to your system or fresh install?

Regards!

---

### Post by LewisTM on 2012-01-23
This is a Thunar bug that some people experience.
Here is a [forum entry]("http://ubuntuforums.org/showthread.php?t=1816298") about the details and a fix.

Cheers!

---


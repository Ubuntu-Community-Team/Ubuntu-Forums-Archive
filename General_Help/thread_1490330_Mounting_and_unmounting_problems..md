---
title: "Mounting and unmounting problems."
date: 2010-05-22
forum: General Help
---

### Post by oopsie on 2010-05-22
A week ago, the way my ubuntu behaves changed.

Normally in the "places" menu, there was a list of my drives I can click on to mount and open. That's missing now. I can click on "computer" and mount them there though.

But, when I try to unmount a drive, I get an error message saying "umount: /media/New Volume is not in the fstab (and you are not root)"

It never used to say that before.

---

### Post by oopsie on 2010-05-22
I mean, I'm sorry. But I've asked this question multiple times on various forums and on the Ubuntu IRC channel, and I never get much of a response.

Has what I said not made any sense? Do I need to give more info?

---

### Post by Lucky. on 2010-05-22
Are you unmounting from the terminal/command prompt, or are you using the graphical user interface to do so?

I ask because the "You're not in root" message usually comes to me in the terminal, and I can fix it by simply using the sudo command.

sudo umount '/media/New Volume'

But if you're getting something like in the GUI, I'm stumped.

PS:  I added the apostrophes around '/media/New Volume' because I think it's required for file/folder names with spaces in them.

---

### Post by oopsie on 2010-05-23
Thanks for replying. Yeah, it's from the GUI

---

### Post by Jakiejake on 2010-05-23
I know this may be stupid but try logging as root and Unmounting from there
You need to setup root just search "How To Setup Root On Ubuntu"
Also try a different USB port
P.S. What are you trying to mount/unmount

---

### Post by Jakiejake on 2010-05-24
Bump :)

---


---
title: "Login PW - Good. Unlock PW - Incorrect. Uhh??"
date: 2010-09-24
forum: General Help
---

### Post by Roasted on 2010-09-24
My problem is simple:

I log in to my account with my password on a fresh boot. Things are good.
I lock my computer, move the mouse to bring up the password screen, not so good.

I'm using the same password in each instance.

Ideas?

---

### Post by sikander3786 on 2010-09-24
Just a thought. I've read somewhere that permissions on /etc/shadow might effect when unlocking the screen. They need to be set to 640 I think. Not sure.

**[COLOR="Red"]EDIT:[/COLOR]** I found the page I was referring to.

[http://ubuntuforums.org/showthread.php?t=1006366](http://ubuntuforums.org/showthread.php?t=1006366)

---

### Post by Roasted on 2010-09-24
I forget how to calculate octal rights offhand, besides the obvious 777 being full blown rights.

Here:

-rw-r-----  1 root    root      1586 2010-09-23 22:49 shadow


I copied /etc group+shadow+passwd from my old install to my new install (I got new hard drives and did a fresh install of 10.04) so I think that may be why.

For what it's worth, the old install was 10.04 64 bit, new one is 10.04 64 bit, and in both instances I used the same username and same password.

Ideas?

---

### Post by sikander3786 on 2010-09-24
Octal permissions on my etc/shadow are 100640. Means I was correct about that :-) Don't know how to calculate octal values, I use Octal column in Nautilus whenever needed.

---

### Post by Roasted on 2010-09-25
Well we're definitely on 640 perms for the shadow file. No idea what else it could be. Tried resetting my password, etc... No dice...

---

### Post by CharlesA on 2010-09-25
How did you reset the password? I've heard that if you don't use the GUI to do that (use the terminal instead) that it doesn't change yer keyring passwd, and that screws up stuff.

---

### Post by Roasted on 2010-09-25
> **CharlesA said:**
> How did you reset the password? I've heard that if you don't use the GUI to do that (use the terminal instead) that it doesn't change yer keyring passwd, and that screws up stuff.

GUI and terminal.

I also created a new account named "admin" and deleted my user account (but kept the files) then re-added my account. No dice.

I won't lie - this is one of the more ridiculous problems I've ran into. Gahh!

---

### Post by CharlesA on 2010-09-25
Understandable. 

Is it only the screensaver that is giving you problems?

I found this [ancient thread]("http://ubuntuforums.org/showthread.php?t=945350"), but I don't know if that actually works or not.

---

### Post by Roasted on 2010-09-25
Thanks bro, but I fixed it literally 30 seconds ago on a thread I dug up via google.

My /etc/shadow file was 640 perms as needed, but it was owned by root:root.

[http://ubuntuforums.org/showpost.php?p=9422076&postcount=12](http://ubuntuforums.org/showpost.php?p=9422076&postcount=12)

That thread said to change ownership to root:shadow. It works now. Nice! :guitar:

Guess I shoulda just ran ls -l in my /etc directory on my laptop with 10.04 and I would have noticed it. Doh!

---

### Post by CharlesA on 2010-09-25
Glad you got it working. I wonder how or why the permissions changed on that file.

---

### Post by Roasted on 2010-09-25
> **CharlesA said:**
> Glad you got it working. I wonder how or why the permissions changed on that file.

Well, when you look at what I did, it makes sense.

I fired up gksudo nautilus, so I was running nautilus as root. I used dual pane mode (view - extra pane) and was using 1 side as my drive, 1 side as my old drive. I copied the files from my old drive, pasted to new drive.

And there lies the problem... when I'm in as root with nautilus, that is the user mode I mimic. I am no longer jason, I am root. Therefore when I paste the file over, I am "creating" the shadow file. In turn, it brought on root:root perms, not root:shadow as the file was originally in.

---


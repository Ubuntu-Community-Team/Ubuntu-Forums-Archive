---
title: "thinkfinger installed, fingerprint acquired, but nothing works"
date: 2009-08-30
forum: General Help
---

### Post by LifeEnemy on 2009-08-30
I have a dell XPS m1530, and I've been trying to get the fingerprint scanner to work. I've followed the instructions on these pages:

[http://www.thinkwiki.org/wiki/How_to...kFinger#Jaunty]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Jaunty")

[https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

I have installed all the libraries and such, and successfully acquired and verified my print. I tried to edit the common-auth file to add the two lines they say, but whenever I did that I couldn't start Synaptic (used to test it). Changing the file back made it work fine, although I had to put in my password. I'm usuing 9.04, so I also tried using the 'enable' command instead of editing that file, but it still doesn't work. I have also tried the '--acquire $USERNAME' from thinkwiki. I am at a point where my print works if I use the verify command, but whenever I am prompted for a password (ex: starting synaptic) I can't use my finger to log in. Is there something I am missing to link my fingerprint with my password?

---

### Post by LifeEnemy on 2009-09-03
bump

---

### Post by LifeEnemy on 2009-09-06
I need help with this, please!

---

### Post by LifeEnemy on 2009-09-20
Come on! Hasn't *somebody* gotten this to work?

---

### Post by camper365 on 2009-09-20
I think that thinkfinger is designed for Thinkpads, which a Dell is not. However, I do not know very well. I have a thinkpad t43 with a fingerprint reader, but because of what I believe to be hardware issues, it doesn't work (I got the computer used, so I have no clue what happened to it before I got it).

---

### Post by ashwinhgtx on 2009-09-20
[http://itsanimesh.com/2009/01/11/dell-xps-m1530-fingerprint-reader-in-linux/](http://itsanimesh.com/2009/01/11/dell-xps-m1530-fingerprint-reader-in-linux/)

Try this link. It's for Hardy but it should work for Jaunty as well if you change the sources. Give it a try.

---

### Post by LifeEnemy on 2009-09-20
I was directed to ThinkFinger by a few different webpages about Ubuntu on the Dell XPS M1530 (including the Ubuntu wiki article "Installing Ubuntu on a Dell XPS M1530"). Also, the Ubuntu wiki article on ThinkFinger says that it is a driver for "SGS Thomson Microelectronics fingerprint reader that you can find on most Lenovo/Thinkpad, Dell and Toshiba." I would think that it would work, especially since I was able to install it and register my fingerprint. My only problem is getting the driver to associate with the password prompts.

Is there any way to find out exactly what model fingerprint reader I have on my computer?

EDIT: Sorry, Ash. Didn't see your post before I typed this one out. By changing the sources would you mean just change the word "intrepid" to "jaunty" for the first step?

---

### Post by LifeEnemy on 2009-09-22
> **ashwinhgtx said:**
> [http://itsanimesh.com/2009/01/11/dell-xps-m1530-fingerprint-reader-in-linux/](http://itsanimesh.com/2009/01/11/dell-xps-m1530-fingerprint-reader-in-linux/)

Try this link. It's for Hardy but it should work for Jaunty as well if you change the sources. Give it a try.

I used that guide and it works great now. Thanks!

---


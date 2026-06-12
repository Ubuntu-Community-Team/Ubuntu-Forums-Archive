---
title: "Change MOTD - what edits it?"
date: 2010-09-08
forum: General Help
---

### Post by Alexander D. Gray on 2010-09-08
Hi all,

I have kubuntu 10.04 installed on my system and want to change the message of the day (MOTD) that you see after you login with a text based login prompt.

I have edited /etc/motd, looked at and changed /etc/update-motd.d/00-header and ~/10-help-text and to my knowledge I don't have a /etc/motd.tail and the command 'update-motd' doesn't work.

As you can see, it appears a lot of things edit, or used to edit, the motd.

Now, with all the changes I've made and tinkering I've done, I get the message I want to display, but it's followed by:

The programs included with the Ubuntu system are free software;
[...]
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

I want to get rid of this message about ubuntu, but for the life of me I can't find the file that's plugging it into the motd. Does anyone know how to get rid of this portion of the message?

Thanks in advance,

---

### Post by Rhubarb on 2010-09-08
That is a little weird.

I've followed what you would've done (edited / deleted some files in /etc/update-motd.d).

Without modifying my system (Ubuntu 10.04.1 64bit Desktop) I don't get these parts:
> The programs included with the Ubuntu system are free software;

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

I'm unable to check my server to see if that's the same, because It instantly launches into byobu upon login via terminal.

So I'm afraid I can't be of much help without doing further searching for possible solutions on the internet.

---

### Post by Alexander D. Gray on 2010-09-08
Hey,

Thanks for trying. I've done this before on my ubuntu setup and it worked fine. The only difference in what I did here was that it was a kubuntu setup using the alternate install disc to setup lvm encryption. I don't even know if that matters....

Funny thing is is that I can find this warranty reference anywhere. In no motd files in /update-motd.d/ or var/run or anywhere else I could think of. There's only a couple of references to this paragraph online, with solutions typically being to update /etc/motd, which I've done, but to no avail.

Is it possible to search files for this phrase? Perhaps if i could do that I could find what file is contributing to the motd.

Thanks for trying to recreate the issue.

---

### Post by pbrane on 2010-09-08
Have you looked at the contents of */etc/issue* or */etc/issue.net*? If you find that file has the disclaimer text you should be able to stop it from being appended by editing */etc/pam.d/login*. Look for this line:
**auth       required   pam_issue.so issue=/etc/issue** and comment it out

another way to do this, I think, is to create a */etc/motd.static*, edit to your liking, remove */etc/motd*, then link */etc/motd.static* to */etc/motd*. This should bypass the normal motd updating.

```

gksudo gedit /etc/motd.static <== edit and save
sudo rm /etc/motd
sudo ln -s /etc/motd.static /etc/motd

```

I would try to find the offending test first though.

---

### Post by Alexander D. Gray on 2010-09-10
Thanks for your help pbrane.

It turns out that /etc/issue is the file that contributes the message you see at the login prompt, this is before you login. The message I want to edit is after the login prompt, once you've successfully logged in.

You're second recommendation for changing the motd file to a motd.static file unfortunately did not remove this paragraph in question. I'm still trying to figure out what's contributing to it, as so far as I could see the other files you referred to do not.

Any other ideas?

Cheers.

---

### Post by pbrane on 2010-09-10
try **/etc/legal**. I don't know how it gets appended, the file exists on my server but it is not displayed. Thats one reason it took so long for me to find.

---

### Post by Rhubarb on 2010-09-12
> **pbrane said:**
> try **/etc/legal**. I don't know how it gets appended, the file exists on my server but it is not displayed. Thats one reason it took so long for me to find.

Good point, I never thought to do a full text search for the disclaimer in /etc

With any luck pbrane has got it ;)

---

### Post by Alexander D. Gray on 2010-09-16
> **pbrane said:**
> try **/etc/legal**. I don't know how it gets appended, the file exists on my server but it is not displayed. Thats one reason it took so long for me to find.


Woo! This worked! Thank you pbrane, I don't know if I would have ever found this file. You've been a great help. 

I'm also not sure how this is appended, as on my other ubuntu setup, it's not displayed. I didn't delete the file, but instead removed the contents of it, which has solved the problem.

Thanks for all the troubleshooting.

Cheers.

---


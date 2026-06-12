---
title: "Help accessing gnome-keyring from cron"
date: 2011-01-19
forum: General Help
---

### Post by Morrad on 2011-01-19
Hello all,

A few days ago, I decided to setup my emailing applications (I use mutt, with offlineimap, imapfilter, and msmtp) to use gnome-keyring rather than have my email passwords stored in plain text inside these application's respective configuration files [1].  I am successfully able to run them from the command line myself, but looking up the passwords from gnome-keyring fails when running from cron.

Searching on Google for help with the problem, I came across a person calling svn with a cron job and authenticating via gnome-keyring [2].  I've tried to adapt his solution, but I don't think I'm doing it right.  I've made a comment on the blog author's post, but am still waiting to hear back.

Does anyone know how I'm supposed to incorporate the bash function from that author's post to give cron the correct environmental variables?

[1]:[http://jason.the-graham.com/2011/01/16/gnome_keyring_with_msmtp_imapfilter_offlineimap/](http://jason.the-graham.com/2011/01/16/gnome_keyring_with_msmtp_imapfilter_offlineimap/)
[2]:[http://mud-slide.blogspot.com/2010/12/subversion-and-gnome-keyring.html](http://mud-slide.blogspot.com/2010/12/subversion-and-gnome-keyring.html)

EDIT: Took me a while, but I did figure it out.  See [http://jason.the-graham.com/2011/01/16/gnome_keyring_with_msmtp_imapfilter_offlineimap/#cron](http://jason.the-graham.com/2011/01/16/gnome_keyring_with_msmtp_imapfilter_offlineimap/#cron)

---

### Post by Morrad on 2011-01-20
Bumping for new eyes.

---

### Post by Morrad on 2011-01-20
EDIT: Ack, I blame the forum for the double post

---

### Post by Morrad on 2011-01-21
Another bump.

---

### Post by Morrad on 2011-01-28
Wanted to note to any subscribed to the thread that I did figure it out, and edited my original post.

---


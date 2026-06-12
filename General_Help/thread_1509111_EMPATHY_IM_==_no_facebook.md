---
title: "EMPATHY IM == no facebook"
date: 2010-06-13
forum: General Help
---

### Post by chrisj26 on 2010-06-13
I've been using Empathy on lucid and i can't get facebook chat to connect. The only way I can use it is if setup my account on kopete and have empathy simultaneously running, login on kopete, i get logged into both and then log out of kopete. the only reason i use kopete is for the yahoo messenger webcam support.

---

### Post by cojoda on 2010-06-14
I am having the same problem.  When I attempt to connect the Empathy authentication fails.  I'm running on lucid.  It seems to be either a problem with my Empathy setup or a problem with the Facebook setup itself.  And Tomboy Notes seems to sync up just fine.

---

### Post by rmvasuki on 2010-06-14
um..I'm guessing you could use Pidgin Internet Messenger..Its got a facebook plugin!

---

### Post by nutznboltz on 2010-06-19
I'm guessing that XMPP (jabber) support for facebook was revoked.

They never used SSL which is super-crummy since you had to send your password unencrypted over the Internet.

[http://blogote.com/2010/ideas/facebook-pidgin-plugin-chat-from-your-facebook-account-in-pidgin.html](http://blogote.com/2010/ideas/facebook-pidgin-plugin-chat-from-your-facebook-account-in-pidgin.html)

Running this:

sudo aptitude install pidgin-facebookchat

Then using pidgin worked for me.

---

### Post by Linuxforall on 2010-06-19
Facebook working fine here on Empathy.

---

### Post by asif_1088119 on 2010-06-19
i cannot connect to anything

---

### Post by harto on 2010-06-22
There is a simple workaround for the failing authentication. You need to log out of facebook for it to pass.

---


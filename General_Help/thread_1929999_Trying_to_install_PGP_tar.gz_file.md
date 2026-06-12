---
title: "Trying to install PGP tar.gz file"
date: 2012-02-22
forum: General Help
---

### Post by Conscript on 2012-02-22
Good day, I am trying to install the file "PGPcmdln_6.5.8_Lnx_FW.tar.gz" but I haven't the foggiest idea of how to do it to my shame.  Still a new ubuntu user.  Prowled google but didn't find much there.  I was hoping the Ubuntu Gods would rescue me.

It is a PGP security program which I am trying to get to work with Sylpheed (an email client) which supports PGP and PGP encryption.

If any can assist, it would be greatly appreciated.

BTW I am running Ubuntu 11.10 Oneiric Ocelot.  But I did the Gnome fallback session because I despise Unity with every fiber of my being.

---

### Post by Gremlinzzz on 2012-02-23
This site might help
[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)

---

### Post by surfer on 2012-02-23
i'm sure you are aware of it, but just in case: thunderbird with enigmail handles gpg signed/encrypted mails perfectly!

---

### Post by ottosykora on 2012-02-23
not sure, but is sylpheed not also able to use gpg which is in its cli form on the ubuntu installed?

---

### Post by oldos2er on 2012-02-23
> **Conscript said:**
> Good day, I am trying to install the file "PGPcmdln_6.5.8_Lnx_FW.tar.gz" 

That program is 12 years old, kinda doubtful that it would work in Ubuntu. Like ottosykora said, there are basic gpg tools already installed in Ubuntu, I'd look into using them with Sylpheed.

---

### Post by Conscript on 2012-02-23
Well, I gave up on the tar.gz file.  Don't know why but it just wasn't going.  After a while at the terminal I just decided to download thunderbird and the associated pgp package.

Strangely enough, pgp started to work with sylpheed afterwards.  But not the encryption aspect, only the signing.  

*Boggled*

Looks like evolution is going to take a hike afterall.  If evolution had a pgp sign/encryption package I would keep it.

---

### Post by Conscript on 2012-02-23
> **ottosykora said:**
> not sure, but is sylpheed not also able to use gpg which is in its cli form on the ubuntu installed?

Not sure, I have no idea the "gli" is.  Pretty new to ubuntu still.  I switched because my hatred of windows was complete.

---

### Post by qamelian on 2012-02-23
> **Conscript said:**
> 
Looks like evolution is going to take a hike afterall. If evolution had a pgp sign/encryption package I would keep it.
Evolution handles PGP signing and encryption. I've been using it for years. Here's a link to a HowTo:
 
[http://support.real-time.com/linux/email/client/evolutionpgp.html](http://support.real-time.com/linux/email/client/evolutionpgp.html)

---

### Post by Conscript on 2012-02-23
> **qamelian said:**
> Evolution handles PGP signing and encryption. I've been using it for years. Here's a link to a HowTo:
 
[http://support.real-time.com/linux/email/client/evolutionpgp.html](http://support.real-time.com/linux/email/client/evolutionpgp.html)

I feel like a wee simpleton surrounded by titans of intellect.  Thank you my Canadian friend.

---

### Post by oldos2er on 2012-02-23
CLI = command line interface, programs meant to be run in a terminal. Use Ctrl-Alt-t to open a terminal, then run ```
man gpg
``` to get started.

---

### Post by Conscript on 2012-02-23
Problem solved,  Got it to work in both thunderbird and evolution, Sylpheed will encrypt it and sign it, but won't decrypt it.

Either way the problem is solved, thanks for all your help guys.  Just saved us a huge head ache and money shipping documents via snail mail.

---

### Post by qamelian on 2012-02-23
> **Conscript said:**
> I feel like a wee simpleton surrounded by titans of intellect. Thank you my Canadian friend.
 No problem. :)

---


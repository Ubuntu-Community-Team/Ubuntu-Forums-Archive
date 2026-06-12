---
title: "Thunderbird &amp; Enigmail"
date: 2006-05-25
forum: General Help
---

### Post by joedunn on 2006-05-25
This might be a dumb question but I'll ask anyway.

My ibook died, but I did a full backup the day before :). So while I wait for my new macbook pro to show up I installed Dapper on a old computer. I put thunderbird on it and enigmail on it. The one issue I am having is getting my personal gpg key from my backup imported into enigmail.

I have it imported into kgpg easily enough, is there any turtials on how to do this, or am I missing something really easy?

Thank you in advance for your help.

Joe

PS I used thunderbird with enigmail on my mac and used gpg to export my personal key.

---

### Post by gborzi on 2006-05-25
If thunderbird-enigmail works as mozilla-enigmail you don't have to import anything. In fact, I only installed mozilla-enigmail and copied my ~/.gnupg directory to the notebook from the desktop to have a working mozilla mail + enigmail setup.

---

### Post by joedunn on 2006-05-25
Thank you so much! Worked great... So if I may ask, how did you figure that out? I would have figured you would have to import your key.

Thanks again

Joe

---

### Post by gborzi on 2006-05-25
[QUOTE=joedunn]Thank you so much! Worked great... So if I may ask, how did you figure that out? I would have figured you would have to import your key.

Thanks again

Joe[/QUOTE]
Some times ago I wanted to submit some packages to REVU, and I asked on the irc channel about the whole procedure. To submit packages I had to send a signed email to REVU, so someone on the irc channel pointed me to a pdf tutorial on mozilla-mail + enigmail. I simply followed the tutorial. I had not used gpg before, so I didn't noticed the absence of an import step.

---


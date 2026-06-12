---
title: "Kmail GPG Issues"
date: 2012-02-09
forum: General Help
---

### Post by drmrgd on 2012-02-09
I've been trying to figure out how to get Kmail working with OpenGPG (actually I'm just trying to set up a launchpad account).  I can't seem to get this working, though.  I was able to setup pgp-agent, generate a key and a passphrase and what not, and I seem to be able to import it into Kmail OK.  However, when I try to compose a message, digitally sign it, and send it, I get a bad passphrase error.  Also, when I try to decrypt a signed message (actually launchpad's Confirm Your OpenPGP Key email), I get this error:

> You just entered an invalid passphrase.
Do you want to try again, or cancel and view the message undecrypted?

But, I never get a dialogue box to actually type a passphrase in.  I just keeps giving me an error without a way to actually type it in.  

From some advice around the net, I installed kgpg, made sure that my gpg.conf file had "use gpg-agent" uncommented, and created a gpg-agent.conf file with the following:

> pinentry-program /usr/bin/pinentry-qt4
default-cache-ttl 3600
allow-mark-trusted
debug-level basic

From what I read, the system can have a hard time finding the pinentry program and this file is needed to fix it.  However, after both restarting the system and manually killing then restarting gpg-agent, I'm still getting the error.  

I also found some information about changing some settings under Kmail's Settings -> Configure KMail -> Security tab -> Crypto Backends from [this guide]("http://userbase.kde.org/KMail/PGP_MIME").  But, I don't seem to have a "Crypto Backends" tab in my settings.  

I really don't like Kmail and am going to replace it when I have the time to migrate everything over.  For now, though, does anyone have a solution for me to get this up and running?

---

### Post by drmrgd on 2012-02-10
Well, I think I may have fixed this.  It looks like something was preventing pinentry from appropriately running, in addition to, gpg using the wrong socket.  I created a new socket, pointed GPG to it, and rebooted, and it seems that Kmail is now giving me a passphrase entry box.  Still a little fuzzy on just how this thing falls together and how I fixed it....but, it's enough to mark the thread as solved :)

---


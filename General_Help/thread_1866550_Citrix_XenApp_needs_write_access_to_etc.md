---
title: "Citrix XenApp needs write access to /etc"
date: 2011-10-21
forum: General Help
---

### Post by Danners on 2011-10-21
Hi,

I'm trying to get CitrixICAClient and CitrixXenAppPlugin working on Ubuntu 11.10 64bit.

I've pretty much got it all working (I've set it up before OK on Windows), except when the Secure Application Manager launches it displays an error saying "You do not have permission to change the hosts file. Please verify that you have write permissions in the /etc directory."

Now obviously my user does not have access to modify files in /etc and the solution seems pretty obvious to me - give my user write access, but I don't feel comfortable doing that.

I've tried "sudo chmod 666 /etc/hosts*" but the error persists, I'm not sure exactly what it's trying to do or whether I need to change the permission on /etc too.

Appreciate this issue may be a bit niche, can't seem to find any info on it online, has anyone come across any situations similar to this before?

Many thanks.

---

### Post by gsmanners on 2011-10-21
First thing, undo what you just did:

```
sudo chmod 644 /etc/hosts*
```

Because changing the permissions on those isn't going to fix anything and who knows what could happen.

Have you tried contacting Citrix? This is a commercial app we're talking about, and they seem to offer support from where I'm sitting.

---

### Post by Danners on 2011-10-21
> **gsmanners said:**
> First thing, undo what you just did:

```
sudo chmod 644 /etc/hosts*
```

Because changing the permissions on those isn't going to fix anything and who knows what could happen.

Have you tried contacting Citrix? This is a commercial app we're talking about, and they seem to offer support from where I'm sitting.

Yeah, I undid it straight away, I just wanted to prove/disprove a theory. I haven't yet contacted Citrix, that will be my next port of call.

Thanks.

---

### Post by ioda006 on 2011-11-16
Did anyone find a solution for this?  I have the same issue with a Juniper program.

---

### Post by cryomax12 on 2011-12-26
Any updates on this? 
I am getting the same issue with ICA Client 12.0 on Ubuntu 11.10

---


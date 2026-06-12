---
title: "Synaptic Freezes when I click the Reload button."
date: 2009-09-23
forum: General Help
---

### Post by Mike_IronFist on 2009-09-23
Hey, this is a weird problem I've got. I tried to install the repositories for another program, some kind of rsync frontend program, I forgot what it was called. I added the source, used the necessary commands to add the authentication key, and then proceeded on over to Synaptic.

I clicked "reload" on Synaptic. It froze. So I opened a terminal, typed a command to kill it. And tried again. It froze upon clicking reload, once again. I removed the authentication key for it and also the repo. Then I tried again. Synaptic still froze up on me. So I killed it via terminal once more and tried to re-install it through itself. Still no luck, and it bugged me about the installation of synaptic not being "authenticated" before proceeding with installation. What? I tried installing a random program and got the same message. My authentication keys are misbehaving.

So then I restarted. And tried again. And repeated this several times. Of course, each time, it still froze (and still does) when I click "reload".

Can anyone help me figure out what's up with this? I need to be able to upgrade when Karmic comes out, and I can't do that if Synaptic can't update its software sources.

EDIT: A reminder, I'm running 64-bit Jaunty. Also, a full reinstallation is a last resort for me, so if your suggestion is to reinstall Jaunty, unless you can prove there's no alternative, I might have to ignore your option.

---

### Post by Mike_IronFist on 2009-09-23
Bump.

Please, someone respond!

---

### Post by oboedad55 on 2009-09-23
> **Mike_IronFist said:**
> Bump.

Please, someone respond!

You need to edit your sources.list and remove the offending lines. Then run synaptic and reload your repositories.

---

### Post by Mike_IronFist on 2009-09-23
> **oboedad55 said:**
> You need to edit your sources.list and remove the offending lines. Then run synaptic and reload your repositories.

I don't think you read my original post correctly. I said:
> I removed the authentication key for it and also the repo

So yeah, it has NOTHING to do with my sources list. Synaptic freezes and becomes a zombie process seconds after I click the reload button. It doesn't just return an error because the repo's aren't listed right.

There are no "offendling lines" in my sources.lst file - only the original Ubuntu repos.

It's freezing before it even accesses any repos!

---


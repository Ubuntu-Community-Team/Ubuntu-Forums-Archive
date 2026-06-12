---
title: "PATH gets reset on reboot"
date: 2012-01-07
forum: General Help
---

### Post by shashanksingh on 2012-01-07
My PATH env variable gets reset to default on every boot.

How can I make a permanent change?

---

### Post by MG&amp;TL on 2012-01-07
> **shashanksingh said:**
> My PATH env variable gets reset to default on every boot.

How can I make a permanent change?

Depends on what you modify it for. I'd put it in ~/.bashrc.

---

### Post by shashanksingh on 2012-01-07
> **MG&TL said:**
> Depends on what you modify it for. I'd put it in ~/.bashrc.

I just want to add my android-sdk-linux/tools and platform folders to the path.

I just realized env variables are "variables", i.e , temporary.
:o

Thanks.
I think .bashrc should do it.

Just curious, what does rc stand for in bashrc?
Is it the most convenient way to initialize things?

---

### Post by MG&amp;TL on 2012-01-07
> **shashanksingh said:**
> I just want to add my android-sdk-linux/tools and platform folders to the path.

I just realized env variables are "variables", i.e , temporary.
:o

Thanks.
I think .bashrc should do it.

Just curious, what does rc stand for in bashrc?
Is it the most convenient way to initialize things?

IDK, but rc seems to be the default suffix for a lot of stuff. Conky, for example.

---

### Post by WorMzy on 2012-01-07
"[Run commands]("http://en.wikipedia.org/wiki/Run_commands")"

---


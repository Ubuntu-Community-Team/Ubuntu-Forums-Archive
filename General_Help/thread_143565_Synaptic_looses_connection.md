---
title: "Synaptic looses connection"
date: 2006-03-12
forum: General Help
---

### Post by Mike Wilson on 2006-03-12
Probably because I'm using a satellite ISP with ugly latency (i.e. all is well on a wired DSL connection that I use elsewhere), Synaptic is a real dog at dropping transfer connection after moving only a few KB. Is there any way to make it resume transfers more reliably?

---

### Post by skymt on 2006-03-12
The short answer is no. The long answer is sort of, but it's a lot of work. You can use wget (it's designed for bad connections) to download directly from the repositories, then dpkg -i each package. I don't know any way to improve reliability of apt-get update, though.

---


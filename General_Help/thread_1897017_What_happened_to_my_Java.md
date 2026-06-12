---
title: "What happened to my Java?"
date: 2011-12-18
forum: General Help
---

### Post by ebasa on 2011-12-18
Running 10.04 after the last java update I have lost my java plugin for firefox. Any idea to get it back? None of the fixes posted seem to work.

Never mind I just restored my backup AND EVERYTHING IS FINE NOW.

---

### Post by ottosykora on 2011-12-18
I managed to get the plugin back, but it will not work anyway.
It seems that the plugin was kind of deliberately removed and you have still the icedtea plugin and this will pick the open java instead.

---

### Post by thatguruguy on 2011-12-18
Read [this]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html").

tl;dr version: The version of Sun Java in the repository has a significant security hole, and Sun is no longer allowing distributions (such as Ubuntu) to take the necessary steps to patch the hole within the distribution's repositories. You need to either download Java directly from Sun's site, or install the open source version of java (Iced Tea).

In other words, it is incorrect to state that "EVERYTHING IS FINE NOW", since the version the OP is using has a significant security hole.

---

### Post by ebasa on 2011-12-18
> **thatguruguy said:**
> Read [this]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2011-December/001528.html").
In other words, it is incorrect to state that "EVERYTHING IS FINE NOW", since the version the OP is using has a significant security hole.

Well it is fine as far as I am concerned in that it works on the two websites I use it on. Ice tea just doesn't. Not that concerned about 'SECURITY HOLES" but that is just me.

---

### Post by suresnjain on 2011-12-19
I agree with the answer ebasa gave.icedtea does not work with one website I want and hence forced to use this sun java with security hole.Any easy way to patch this up?

---


---
title: "gnome-terminal refuses to log debug output"
date: 2009-07-21
forum: General Help
---

### Post by Starks on 2009-07-21
I'm trying to debug Wine and the typical 'blahblah > filename.txt' command isn't working. Nothing gets logged.

---

### Post by jenkinbr on 2009-07-21
try ```
blahblahblah > filename.txt 2>&1
```

The '2>&1' will print standard error to the standard output, which is already redirected to file.

See if that helps.

---

### Post by nikhilk on 2009-07-21
> **jenkinbr said:**
> try ```
blahblahblah > filename.txt 2>&1
```

I find```
blahblahblah &> filename.txt
``` simpler to type and achieves the same effect!

---

### Post by jenkinbr on 2009-07-21
> **nikhilk said:**
> I find```
blahblahblah &> filename.txt
``` simpler to type and achieves the same effect!
That's a new one, never heard of &> doing the same as 2>&1...

---

### Post by nikhilk on 2009-07-21
> **jenkinbr said:**
> That's a new one, never heard of &> doing the same as 2>&1...

I refer to the great bash HOWTO at tldp.org, it is a very useful read if you do bash scripting (or want to get a start on it)
[This]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html") is the link to the redirection section.

---


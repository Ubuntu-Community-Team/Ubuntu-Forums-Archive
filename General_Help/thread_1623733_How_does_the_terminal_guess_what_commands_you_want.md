---
title: "How does the terminal guess what commands you want?"
date: 2010-11-17
forum: General Help
---

### Post by lone_wolfII on 2010-11-17
This is not really for help, just curious. I couldn't really find a general Ubuntu discussion area. 

So I typed ipconfig and of course it said no such command blah blah blah. 

What I found interesting was that it provided a list of other commands I may have meant to use, ie. ifconfig. 

So what's the algorithm used to determine the commands? Is it SOUNDEX or something else?

---

### Post by dcstar on 2010-11-17
> **lone_wolfII said:**
> This is not really for help, just curious. I couldn't really find a general Ubuntu discussion area. 

So I typed ipconfig and of course it said no such command blah blah blah. 

What I found interesting was that it provided a list of other commands I may have meant to use, ie. ifconfig. 

So what's the algorithm used to determine the commands? Is it SOUNDEX or something else?
The following packages:
```
command-not-found
command-not-found-data
```

---


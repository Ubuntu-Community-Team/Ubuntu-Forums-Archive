---
title: "How do I find a file or a name in a file"
date: 2009-09-20
forum: General Help
---

### Post by bobsummer45 on 2009-09-20
What would the command to type I am using 9.04 server.
I want to do a search to find say a domain name on my webserver.
Example: google.com etc

What command would I type to find out where that is.

I am really new to LINUX I could sure use the help.

Thanks in advance!

---

### Post by geirha on 2009-09-20
You want to find out which files contain a certain string? If so, grep would be the logical choice. It sounds like you want to search through configuration, so I'd limit he search to /etc

```
grep -ri 'google.com' /etc
```

I recommend you have a look at the man-page to get an idea of what else grep may be used for. «man grep»

---


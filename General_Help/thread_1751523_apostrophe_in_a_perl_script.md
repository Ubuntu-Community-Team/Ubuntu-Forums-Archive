---
title: "apostrophe in a perl script?"
date: 2011-05-06
forum: General Help
---

### Post by rbc on 2011-05-06
Here’s the "script" I have:
perl -pi -e 's/MY\ COMPANY/Tonys\ Restaurant/' *.doc

Obviously I want search every .doc file in the current directory, look for the phrase MY COMPANY and replace it with Tonys Restaurant, but I’d rather it be Tony’s (with an apostrophe). perl does not seem to like that. Is there anyway to overcome that? Or should I be going about this a different way? I apologize, but all the Google results were either way over my head and more than I need to accomplish, or they seem to suggest that I can escape the apostrophe, as I’ve done with the spaces, but this does not work. Thanks in advance

---

### Post by sisco311 on 2011-05-06
Use double quotes:
```
perl -pi -e "s/MY COMPANY/Tony\'s Restaurant/" *.doc
```

---

### Post by rbc on 2011-05-07
I knew there's be a simple answer, and as always, I find it here. Thank you

---


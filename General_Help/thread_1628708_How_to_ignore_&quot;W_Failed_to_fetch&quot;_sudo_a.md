---
title: "How to ignore &quot;W: Failed to fetch&quot; sudo apt-get update errors?"
date: 2010-11-23
forum: General Help
---

### Post by inameiname on 2010-11-23
How do I ignore "W: Failed to fetch ...." error messages with 'sudo apt-get update'? Mainly, so in a command such as this:

```

sudo apt-get update && sudo apt-get upgrade

```

...it will simply ignore the repo(s) that are currently unavailable for whatever reason and continue with the command.

As it is now, it just halts it all, even if just one of my repos has a temporary issue.

---

### Post by inameiname on 2011-06-18
I still haven't figure this out. Not a pressing matter, but from time to time a bad repo causes this error to occur, and stops all the other stuff I have after in the command from running because of it. Of course I could just remove the repo or disable it, but sometimes its just temporarily out, and returns to good after a day or two at the most.

---


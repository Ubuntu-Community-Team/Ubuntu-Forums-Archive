---
title: "Run all php scripts as script owner?"
date: 2011-10-21
forum: General Help
---

### Post by jkries on 2011-10-21
I have been creating php sites on a shared host for several years.
Now I have moved some of these tools onto a home server running Ubuntu 11.04 server.

I noticed that any of the scripts that need to write to a folder are hitting a wall.

It seems the script owner is the FTP username, and the script is being run as www-data

How can I get all scripts to execute as the script owner, as they do on the shared host?

I have tried several solutions from Google searches (such as suPHP), but they were either over my head or unsuccessful.

I appreciate any help you can give this Linux newcomer.

---


---
title: "lftp Help"
date: 2011-10-28
forum: General Help
---

### Post by BuzzStPoint on 2011-10-28
I have logs that I update every day, then I like to upload them to keep a backup and work on another computer. 

Currently I'm using lftp 

Here's where I'm at. 
mirror --delete --only newer -- reverse


It's my understanding the reverse will only update my webserver. not local copies. 

Is there a way to make it so in the morning I can have a cron run in the morning. 
and update the files as needed. 

If I work at home, I want it to update the files on my work computer, and if I worked at my work computer it will update the web server files. 
How would that be set up?

---


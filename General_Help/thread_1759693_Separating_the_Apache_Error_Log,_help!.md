---
title: "Separating the Apache Error Log, help!"
date: 2011-05-16
forum: General Help
---

### Post by ubila on 2011-05-16
Hello, 
I want to separate the Apache2 Error log to log certain events in a specified file.

For example.
client denied by server configuration > denied.log
Directory index forbidden by Options directive > forbidden.log

I would like it add it to the logs as the events happen, and like the other logging systems, create new files when the current is full. ie. denied.log.0 

How can i do this?

Thanks

---

### Post by ubila on 2011-05-16
So far ive been doing it by using sh scripts to pull out the relevant log info then dump it into a new file. 

But can apache do this for me?

Thanks

---


---
title: "Wget download manager"
date: 2011-01-08
forum: General Help
---

### Post by LinuxQuestionAsker on 2011-01-08
So I am trying to download a list of files(more than 10000) each a unique path.  How ever downloading 1 at a time is very slow considering they are small and I have a 50mb connection.  I have been trying to think of a way to do this easily with wget however it is not going that well.  I have come to the conclusion that my wget script is turning into a full fledged download manager.  So what I would like to do is find a command line download manager that I can set a config file for the number of threads then replace my wget with a script that parses the wget commands and queues them in the download manager.  So now all I need are recommendations on the download manager to try.

Things it must have
  multiple connections per file
  multiple files at a time(a must for small files)
 
Things that would be nice
  For it to automatically intercept and parse wget calls

---


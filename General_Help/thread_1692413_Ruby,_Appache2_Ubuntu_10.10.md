---
title: "Ruby, Appache2 Ubuntu 10.10"
date: 2011-02-21
forum: General Help
---

### Post by pholman1960 on 2011-02-21
I am running 10.10 on AWS, I installed a ruby program that uses apathe2.  I do not know much about ruby, I just followed instructions on how to install by reading the forums.

My application does not seem to let go of the return html until the very last moment, because of this, users think nothing is happening, but indeed there is a data mining process running.   On the old, real slow server, you could see the application build a report line by line.

There must be a flush or cache command I am missing.  I can not figure it out.  The output is coming back to a browser.  Is the $stdout.flush only used for log files and writing to the server disk?  Or does it also have an effect on the html coming back from the apache2 server.

Did I miss a setting on appache2, or ruby, or ubuntu?

help

---


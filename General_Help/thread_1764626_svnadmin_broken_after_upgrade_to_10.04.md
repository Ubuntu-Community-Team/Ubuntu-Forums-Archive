---
title: "svnadmin broken after upgrade to 10.04?"
date: 2011-05-22
forum: General Help
---

### Post by hollow5555 on 2011-05-22
A few months back I migrated my Ubuntu 9.10 server to 10.04. My server hosted a subversion repository for a personal programming project. Now I want to add a 2nd repository (actually a new project).

When I try to browse the root repository ([http://mysite/](http://mysite/) using the any tool from tortoisesvn to rapidsvn to command line tools on both windows and linux systems) I get the error 200 OK which I understand usually means invalid URL. No matter what I try I can't browse the root repository. If I use a web browser I can see my existing project by going to [http://mysite/websvn](http://mysite/websvn), almost as if the root of the repository was my existing project.

When I try to create a new repository for my old project I get:
> svnadmin: SQLite compiled for 3.6.22, but running with 3.6.19

According to apt-get I've got the latest version of sqlite and subversion.

Am I just really doing something wrong or was something broken in the upgrade? All I want to do is add a new project! :)

---


---
title: "why is python-django version so out of date"
date: 2011-04-26
forum: General Help
---

### Post by adrian_nye on 2011-04-26
The version currently in aptitude on my 10.04 system is 1.1.1, which is years out of date.
The current production version is 1.3.   I'm wondering what can be done
to improve that situation?

Thanks

---

### Post by DaithiF on 2011-04-26
Hi,
django 1.1 was released in July 2009, and 1.2 in May 2010.  Since Ubuntu 10.04 came out in April 2010, ie. before django 1.2, then 1.1 seems the sensible choice.  Django releases can contain backwards-incompatible changes, so it would probably not be a good choice to automatically push out new versions of django as part of ubuntu updates.

In practice, for serious django development you'll probably need to remove the ubuntu packaged version and install a later django from source.  You should also maybe look into pip and virtualenv for controlling django (& other python lib dependencies) for your django projects.  See [http://www.saltycrane.com/blog/2009/05/notes-using-pip-and-virtualenv-django/](http://www.saltycrane.com/blog/2009/05/notes-using-pip-and-virtualenv-django/) for a good intro. to this topic.

---


---
title: "Python package install so not to break the system"
date: 2009-08-25
forum: General Help
---

### Post by tartley on 2009-08-25
Hi,
I'm a Python programmer. I want to install some Python packages to make them available to my own projects. Some of those packages are already installed, because they are used by Ubuntu. However, the version that Ubuntu uses is different than the version I want to use. If I install the version I want, it hoses the system and all sorts of things (eg. system update) start to break.

Anyone got any hints and tips for approaches to use?

I'm tempted to try and maintain an entirely independent Python installation. Then I can install whatever I like into 'site-packages' there, without affecting the main 'system' Python installation. Obviously this technique is definitely required if I start using a version of Python that differs from the system Python, so I thing I might as well figure it out now.

One issue with this approach is that if I have projects or third-party components which invoke a new 'python' process, then they will pick up the default system Python executable. I guess when I'm working, I need to change the PATH for the shell I'm working from so that my custom Python is found before the system one. Some system tools might not work from within such an environment, but I'll just have to eat that.

Do I make any sense?

---


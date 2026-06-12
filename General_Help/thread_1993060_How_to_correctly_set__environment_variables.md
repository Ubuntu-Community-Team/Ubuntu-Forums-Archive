---
title: "How to correctly set  environment variables"
date: 2012-06-01
forum: General Help
---

### Post by daniel4k on 2012-06-01
Hello everyone,

I installed texlive 2011 using the information on: [http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html). After the install I added the following to the end of my .pam_environment file:
```
MANPATH DEFAULT=${MANPATH}:/usr/local/texlive/2011/texmf/doc/man
INFOPATH DEFAULT=${INFOPATH}:/usr/local/texlive/2011/texmf/doc/info
PATH DEFAULT=${PATH}/usr/local/texlive/2011/bin/i386-linux
```

Now when I print one of those variables, the entry I added appears repeated:
```
$ printenv MANPATH
:/usr/local/texlive/2011/texmf/doc/man:/usr/local/texlive/2011/texmf/doc/man
```Am I setting the environment variables correctly? The information in [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables) suggest that I use .pam_environment.

I'd appreciate it if someone could shed some light on this.  [-o<

[edit]
I forgot to mention that I also get an error when using tex manpages. The manual page shows up but when I leave there is the following message:
```
$ man pdflatex
man: can't resolve /usr/share/man/man1/pdflatex.1.gz: No such file or directory
```

---


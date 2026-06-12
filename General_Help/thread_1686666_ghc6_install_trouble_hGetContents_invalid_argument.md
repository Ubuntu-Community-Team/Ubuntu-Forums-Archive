---
title: "ghc6 install trouble: hGetContents: invalid argument (invalid UTF-8 byte sequence)"
date: 2011-02-12
forum: General Help
---

### Post by olifhar on 2011-02-12
Hi, I'm having some trouble installing both ghc6 and haskell-platform. I figure I'll work on getting ghc6 installed first, then worry about haskell-platform...

Here's what seems to be the relevant error that comes up when I try to ([FONT="Courier New"]apt-get[/FONT]|[FONT="Courier New"]aptitude[/FONT]) [FONT="Courier New"]install ghc6[/FONT]:
```
A package failed to install.  Trying to recover:
Setting up ghc6 (6.12.1-13ubuntu1) ...
ghc-pkg: /home/opm/.ghc/i386-linux-6.12.1/package.conf.d/unix-compat-0.2-edefa7bced91ebe610d455bab466e200.conf: hGetContents: invalid argument (invalid UTF-8 byte sequence)

```

(Here's the full output, if you're interested: [http://paste.ubuntu.com/566475/]("http://paste.ubuntu.com/566472/") )

My searching around has not really helped me understand what's going on, except that it might be caused by a mismatch in locale. So, here's the output of [FONT="Courier New"]locale[/FONT] too:
```
LANG=en_US.utf8
LANGUAGE=en_US:en
LC_CTYPE="en_US.utf8"
LC_NUMERIC="en_US.utf8"
LC_TIME="en_US.utf8"
LC_COLLATE="en_US.utf8"
LC_MONETARY="en_US.utf8"
LC_MESSAGES="en_US.utf8"
LC_PAPER="en_US.utf8"
LC_NAME="en_US.utf8"
LC_ADDRESS="en_US.utf8"
LC_TELEPHONE="en_US.utf8"
LC_MEASUREMENT="en_US.utf8"
LC_IDENTIFICATION="en_US.utf8"
LC_ALL=
```

Any ideas?

*Additional background*: this all seems very strange to me, because I used to have ghc6 installed. I tried to install haskell-platform (through apt), which failed and told me that there was something wrong with ghc6, and so I reinstalled ghc6 and began to get the above error message.

*Also:* Should have said before: running Ubuntu Maverick. XMonad is installed, which is why I had ghc6 in the first place.

---


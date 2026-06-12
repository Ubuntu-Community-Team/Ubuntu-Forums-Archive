---
title: "Question about installing TexLive 2009"
date: 2010-02-07
forum: General Help
---

### Post by AmadeusOK on 2010-02-07
Hey everyone,

I'm trying to install TexLive 2009 following the instructions at [http://tug.org/texlive/quickinstall.html]("http://tug.org/texlive/quickinstall.html"). I unpacked it in /usr/local/src. When I run "./install-tl" I got the following message:

```

Detected platform: x86_64 with GNU/Linux
 
 <B> binary systems: 1 out of 15

 <S> Installation scheme (scheme-full)
     83 collections out of 84, disk space required: 2002 MB

 Customizing installation scheme:
   <C> standard collections
   <L> language collections

 <D> directories:
   TEXDIR (the main TeX directory):
     !! default location: /usr/local/texlive/2009
     !! is not writable, please select a different one!
   TEXMFLOCAL (directory for site-wide local files):
     /usr/local/texlive/texmf-local
   TEXMFSYSVAR (directory for variable and automatically generated data):
     /usr/local/texlive/2009/texmf-var
   TEXMFSYSCONFIG (directory for local config):
     /usr/local/texlive/2009/texmf-config
   TEXMFHOME (directory for user-specific files):
     ~/texmf

 <O> options:
   [ ] use letter size instead of A4 by default
   [X] create all format files
   [X] install macro/font doc tree
   [X] install macro/font source tree
   [ ] create symlinks to standard directories

 <V> set up for running from DVD

Other actions:
 <I> start installation to hard disk
 <H> help
 <Q> quit

Enter command: i
Installing to: /usr/local/texlive/2009
./install-tl: mkdir(/usr/local/texlive/) failed, goodbye: Permission denied

```

Where should I unpack the tarball? Do I need to create a subdirectory /texlive? What can I do? Thanks in advance for any kind of help.

---


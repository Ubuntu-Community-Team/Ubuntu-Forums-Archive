---
title: "some help with pygame"
date: 2009-09-28
forum: General Help
---

### Post by phillip1882 on 2009-09-28
i'm trying to get py gambe but it says i'm missing some dependancies.
in particular:
SDL     : found 1.2.13
FONT    : not found
IMAGE   : not found
MIXER   : not found
SMPEG   : not found
PNG     : found
JPEG    : found
SCRAP   : found
PORTMIDI: not found
PORTTIME: not found

where do i get the nessicary modules to install pygame?

---

### Post by RavensKrag on 2009-12-10
Sorry to revive this thread after so long, but I have the same problem and though I might as well not start a new thread.

Anyway, so I've been able to satisfy the dependencies for PORTMIDI and PORTTIME by installing the libportmidi-dev package.  Still, I don't know how to resolve the other dependencies.

EDIT:
Ok, now I feel really stupid.. just wanted to inform those who made the same foolish mistake - just go check the readme in the source directory *facepalm*

---

### Post by dejotaerre on 2009-12-14
i found those dependencies here (except porttime):

[http://www.libsdl.org/projects/SDL_mixer/release/SDL_mixer-1.2.11.tar.gz](http://www.libsdl.org/projects/SDL_mixer/release/SDL_mixer-1.2.11.tar.gz)
[http://www.libsdl.org/projects/SDL_image/release/SDL_image-1.2.10.tar.gz](http://www.libsdl.org/projects/SDL_image/release/SDL_image-1.2.10.tar.gz)
[http://www.libsdl.org/projects/SDL_ttf/release/SDL_ttf-2.0.9.tar.gz](http://www.libsdl.org/projects/SDL_ttf/release/SDL_ttf-2.0.9.tar.gz)
svn co svn://svn.icculus.org/smpeg/trunk smpeg
[http://downloads.sourceforge.net/project/portmedia/portmidi/184/portmidi-src-184.zip](http://downloads.sourceforge.net/project/portmedia/portmidi/184/portmidi-src-184.zip)

---


---
title: "integrating home-network"
date: 2011-07-07
forum: General Help
---

### Post by LiquidStranger on 2011-07-07
Hi,
I'm currently making the switch from (mostly) desktop to (almost exclusive) notebook use. I own three computers:
A) my notebook (Dell XPS M1330) which is used when I'm not at home and should become the new "center" of my home network. Currently running Ubuntu 11.04
B) an atom-powered microITX case with a TV card running mythbuntu and storing recordings as well as my music
C) my desktop PC, reasonable graphics-card, lots of harddisk space (~5TB, divided among 5 hard disks of varying size), containing data from several projects and simulations, permanent recordings from the tv box etc

Up to now, I mostly used the notebook when not at home, the desktop when at home, syncing some relevant files over the network. When I want to watch TV, Mythfrontend wakes the TV-box up.

I need access to the data on my desktop, but usually only some small subset for a short period of time. Like checking on some data from an old simulation, watching a movie etc. Ive looked into autofs for mounting nfs shares on demand which works quite well, but can I use it to wake the desktop only when necessary, so that it doesn't have to be running all the time. And can I use the desktop's processing power somehow from my notebook? The desktop is running a Phenom 955 4core CPU with 4GB RAM, which could come in handy sometimes. Something like a small scale "cloud" maybe, or if this is too complex some kind of remote session that I can detach from without terminating it.
Basically, I want to treat the desktop as an on demand source for data and processing power.

Any hints on how to achieve this or reasons why this is all impossible or completely unreasonable would be appreciated.

---


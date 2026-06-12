---
title: "Spotify (dependency libxss1 (&gt;= 1:1.2.0) does not exist on karmic 9.10"
date: 2011-08-11
forum: General Help
---

### Post by mogie on 2011-08-11
Hey.

Trying to follow the installation procedure on spotify.com
[http://www.spotify.com/no/download/previews/](http://www.spotify.com/no/download/previews/)

I need libxss1 1:1.2.0, but it doesn't exist with apt-get repositories. Karmic has only 1:1.1:3-1

I was AMAZED that no one (when Googling this) had adressed the same issue anywhere - ever!

I'm not upgrading my kernel right now, so I need some help compiling this for Karmic. Anyone willing to help? 

NB: My Wine Spotify crashes all the time, so thats why I'm trying the "real deal" now..

My kernel is 2.6.31-23-server x86_64

---

### Post by mogie on 2011-08-12
bumpy :/ help me out! I'm not good at compiling..

---

### Post by mogie on 2011-08-15
Is there any way to try compile it with livxss1 1:1.1.2 by editing the dependencies in the spotify package? ... Anyone?

---

### Post by anlop on 2011-11-04
try this:

[http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/libxss1_1.2.0-2_i386.deb/download/](http://pkgs.org/ubuntu-10.10/ubuntu-main-i386/libxss1_1.2.0-2_i386.deb/download/)

---

### Post by degarb on 2011-11-16
Same boat and symptoms as op.  I got about 50 megs free and took 100 plus hours back in 2009 to get karmic to work with everything.  Never had same sucess with other machines getting wireless and jump drives, even with latest pinguy.  So, upgrading on main laptop for living room is not an option.

the 10.10 libxss installed.  I got spotify client installed, but not support for gnome.

Now, no launcher or way to launch spotify.  Typing spotify in terminal returns "segment fault".

---


---
title: "gnome-terminal performance problem"
date: 2010-10-05
forum: General Help
---

### Post by adam.rosenstein on 2010-10-05
Hi, I am a recent Ubuntu convert from SuSE (test-driving 10.10 beta).  My question is, does anyone besides myself find working in gnome-terminal painfully slow?  I just tried using xterm instead and it is easily 10x faster.  SSH in my GT to elsewhere is just as painful.  Why is that?

Some sample tests:

From [Comprehensive Linux Terminal Performance Comparison]("http://martin.ankerl.com/2007/09/01/comprehensive-linux-terminal-performance-comparison/"): cat'ing a txt (rfc3261)

```
xterm          : real   0m0.658s
gnome-terminal : real	0m5.809s
```

paging through bash man page (holding down spacebar): roughly ten times faster in xterm.

From [gnome-terminal performance]("http://mces.blogspot.com/2005/10/gnome-terminal-performance.html") ( which is quite old but has recent comments)

```
time for x in `seq 10000`; do echo {a,b,c,d,e}{A,B,C,D,E}; done
```

```
xterm         : real    0m0.732s
gnome-terminal: real	0m11.530s
```

editing a remote emacs buffer is just too darned painful.
compilations of my os also take way longer if i let stdout go to term.

I've got a toshiba qosmio x505 (4 cores 6 gigs, nvidia graphics w/proprietary driver).

Things I've tried:

[LIST]
[*]ensure cpu is not being "eaten" by something else
[*]disable scrollback buffer
[*]disable scrollbars
[*]change system font anti-aliasing properties
[*]change system fonts/sizes
[*]resize terminal window
[*]disable second monitor (was nvidia twinview: i normally run clones)
[*][*]disable compiz ( i adore compiz, but ran metacity and found no difference)
[*]disable gnome-terminal transparency (i also love trans + blur!) by selecting solid background
[*] and by selecting trans with max
[*] and by selecting picture with no picture (after reading about a bug with this in prior versions of gt).
[/LIST]

No improvement from any of these.  Other aspects of text rendering are quite snappy: local x-emacs, Google Chrome,  and firefox all smooth as silk.  "Foreign" apps a very responsive as well (vmware with various guests, crossover-office with M$ nonsense -- all totally usable).

My technical expertise is high:

I've developed my own (rpm-based) linux distro at work from scratch (started with LFS).  I've been a Linux user/software developer for over a dozen years.  As a unix user in-general I've been at it quite a bit longer: Solaris/SunOS4/HP-UX and other crusty old unicies.

Thanks in advance, and please let me know if I've chosen the wrong forum for my question.

-Adam

---

### Post by llawwehttam on 2010-10-05
gnome-terminal has a lot of extra features and config options while xterm is pretty basic.

Most people aren't too fussed about the difference in speed and those that are have the knowledge to use a different terminal.

I personally like Terminator.

---

### Post by adam.rosenstein on 2010-10-05
well, its the font rendering, anti-aliasing actually.

turning on truetype fonts in xterm makes it beyond impossible (catting the rfc pegs a core and doesnt finish in 30 seconds)

evilvte has an anti-alias enable/disable option.  with font anti alias i get about the same as gnome-terminal, without it, roughly 1/5the the time

---

### Post by adam.rosenstein on 2010-10-05
Found it!.  For anyone else still struggling, it was the nvidia driver: see [nvidia 256.52 xorg-server 1.9.0 performance regression]("http://www.nvnews.net/vbulletin/showthread.php?t=154563&page=4")

The latest is 260.19.06 and it solves the problem.  In gnome terminal, with pretty fonts etc., I am now getting:

```
$ time for x in `seq 10000`; do echo {a,b,c,d,e}{A,B,C,D,E}; done
.
.
.
real	0m1.531s

```

which, I'd say is a huge performance improvement over 11.530s.

Your software manager will likely pick up this update on its own.

---


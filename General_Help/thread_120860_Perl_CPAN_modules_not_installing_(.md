---
title: "Perl CPAN modules not installing :("
date: 2006-01-23
forum: General Help
---

### Post by richw on 2006-01-23
Hi all,

I hope I have this post in the right forum. 

Now down to business - every time I try to install a CPAN  module, it wont happen.

I've tired

> cpan IO::Socket::INET

and 

> perl -MCPAN -e shell
install IO::Socket::INET 

and at the end I get this at the end...

> Removing previously used /root/.cpan/build/IO-1.22

  CPAN.pm: Going to build G/GB/GBARR/IO-1.22.tar.gz

Checking if your kit is complete...
Looks good
Writing Makefile for IO
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible


Now that suggests theres a problem with the makefile, i'm running as root so I dont believe there could be a permissions problem. This also happens no matter what i'm trying to install...

Can anyone shed any light on what I have done wrong and what I can doo to fix it? 

[-o<

---

### Post by Mustard on 2006-02-08
I think I encountered the same problem.  I'd mention that I am stumbling around like a blind man when it comes to installing perl modules, but I found a file in /etc/perl/CPAN called Config.pm in which there are a number of configuration options.  One of these options was 'make' and the path to make was not configured.  I made a backup of the orginal Config.pm file and then added /usr/bin/make as the path to the make.  I think this fixed the problem I was having with installing perl modules. I have no idea whether its the right thing to do though. :)

---

### Post by richw on 2006-02-08
:eek: 

I thought I wasn't going to get an answer!

I'll give that a go tomorrow and report back :-D

---


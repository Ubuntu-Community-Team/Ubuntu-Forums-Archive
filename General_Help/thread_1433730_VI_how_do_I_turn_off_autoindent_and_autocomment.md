---
title: "VI how do I turn off autoindent and autocomment"
date: 2010-03-19
forum: General Help
---

### Post by feliscatus on 2010-03-19
Hi,

A most cumbersome part of my existence has been dealing with VI when I'm trying to write programs/scripts.

I start my scripts with a comment block like this:

# -------------------------------#
# -------------------------------#
#       something.pl       #
# -------------------------------#
# -------------------------------#

when I move to the end of the last comment line, with Esc-$, and press enter, VI automatically puts a '#' on the next line, and sometimes will put spaces and tabs, which force me to the end of the line, and I end up sitting there and deleting tabs all day because I always format my programs with lots of comments/frames/blocks.

Also, when I paste text into VI, if the first line starts with a comment, it will comment and auto-indent everything else.

I have already added to my .vimrc as follows, to no avail.

syntax on
set noautoindent
set nosmartindent
set nocindent
set showmatch

Please help! Because I can't stand emacs...I want to use VI but it's just SO annoying.

---


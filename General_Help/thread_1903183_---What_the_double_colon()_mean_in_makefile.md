---
title: "---What the double colon(::) mean in makefile"
date: 2012-01-01
forum: General Help
---

### Post by bzhao on 2012-01-01
1 include config.mk
2 quiet?=true
3 ifeq ($(target),)
4 .DEFAULT:
5 @for t in $(ALL_TARGETS); do \
6 $(MAKE) --no-print-directory target=$$t $(MAKECMDGOALS) || exit $$?;\
7 done
8 all: .DEFAULT
9 clean:: .DEFAULT
10 install:: .DEFAULT

somebody know the double colon mean in this makefile?

Thanks indeed!

---

### Post by pretty_whistle on 2012-01-01
[SIZE=2]*make* has a little used feature that is signified with the double colon ::  .  This tells *make* to associate more than one *action* for a *target*.  Normally, with a the single colon : , you can have multiple target and prerequisites to map the dependencies, but only one of them can have an associated action.[/SIZE]

---


---
title: "Start GVim maximized"
date: 2009-10-10
forum: General Help
---

### Post by fatmarik on 2009-10-10
So I have been trying to start GVim maximized rather than its default size and I have set the option in my .vimrc as: set lines=39 columns=157. But the problem is that it isn't taking fullscreen with the provided values from: set lines? colums?. So I was wondering if there is a vim command that allows it to load up maximized. I am running Ubuntu 9.04 if that helps. All help is appreciated.

---

### Post by fatmarik on 2009-10-10
anyone?

---

### Post by karthikophobia on 2009-11-03
try this
[http://vim.sourceforge.net/scripts/script.php?script_id=1302](http://vim.sourceforge.net/scripts/script.php?script_id=1302)

---

### Post by SilverWave on 2010-02-23
> **fatmarik said:**
> So I have been trying to start GVim maximized rather than its default size and I have set the option in my .vimrc as: set lines=39 columns=157. But the problem is that it isn't taking fullscreen with the provided values from: set lines? colums?. So I was wondering if there is a vim command that allows it to load up maximized. I am running Ubuntu 9.04 if that helps. All help is appreciated.

> > E.g In ~/.bashrc:
> 
> alias gvim="gvim -geom 80x30"

My setting is:
alias gvim="gvim -geom 210x50"

Cheers.

---


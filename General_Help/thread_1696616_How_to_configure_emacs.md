---
title: "How to configure emacs"
date: 2011-02-27
forum: General Help
---

### Post by jkounis on 2011-02-27
I just finished developing a website on Ubuntu 10.10 with apache 2/mysql 5.1/php 5.3. In order to go live, I purchased a VPS system running CentOS 5.5 and uploaded the files there.

Everything works about the same, except my emacs configuration. 

*I really miss the Ubuntu emacs configuration!*

The things I miss are:[LIST=1]
[*]When I mark text in Ubuntu, the emacs window highlights the region from the mark to the cursor position in blue, so that I can easily see what I am about to copy or delete
[*]Automatic php and css modes indent my code automatically
[*]Overall color use is very good. Comments are Red. Strings are green. Variables are yellow. I suppose this could be part of the php mode listed above. (Comments are red... Function Names are Blue... emacs colors on Ubuntu, I love you:).)
[/LIST]

The version of email on my CentOS server doesn't do any of these things. 

Is there a way to copy the Ubuntu emacs configuration to the CentOS server? I looked at the emacs load-path variable and there are literally hundreds of .el files loaded, so I'm not sure how to proceed.

---

### Post by jpkotta on 2011-02-28
You should try tramp mode.  It lets you edit files on a remote machine with a local Emacs.  You can use ssh, ftp, and several other protocols.  Incidentally, you can also use tramp with sudo to edit local files as another user.  To use it, just visit a file (C-x C-f) and prepend a tramp prefix like "/ssh:user@remote:/path/to/file".

[LIST=1]
[*]That's transient-mark-mode, and is the default on version 23.
[*]There might be CentOS packages to install those modes, or you can get them from the web (see [http://www.emacswiki.org/emacs/PhpMode](http://www.emacswiki.org/emacs/PhpMode) and [http://www.emacswiki.org/emacs/CascadingStyleSheetMode](http://www.emacswiki.org/emacs/CascadingStyleSheetMode)).
[*][http://www.emacswiki.org/emacs/ColorTheme](http://www.emacswiki.org/emacs/ColorTheme).  I like calm-forest.
[/LIST]

---

### Post by jkounis on 2011-03-01
Thanks! Tramp mode works like a charm. It is the easiest thing for maintaining a remote site.

By the way, I downloaded the modes that you mentioned, but things like css-mode don't work on emacs 21 that comes with CentOS. Fortunately, I found [this link]("http://www.centos.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=26353&forum=38#forumpost107766") that explains how to upgrade.

---


---
title: "Compiz ccsm screwed up - won't launch"
date: 2011-08-10
forum: General Help
---

### Post by x371322 on 2011-08-10
I've been having one frustrating day here. I hit something in the compiz manager, don't know what, and it completely destroyed my GUI. Whatever happened, it apparently completely removed unity from my computer. No launcher, no menu bar, nothing. I know this has been something of a common issue, and after a couple hours of googling and using terminal I finally managed to get unity back up and running. So I'm good there.

But now, my compiz manager won't even launch. The icon just hangs. 

So far, I've tried uninstalling and re-installing ccsm, didn't fix it. I try to launch from terminal, it still doesn't work. In fact, here's the output I get in terminal when trying to launch ccsm, maybe someone can identify the problem. I know I see some things in there that failed. Not experienced enough to know what I'm looking at here.

> [I]Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
/usr/lib/python2.7/dist-packages/ccm/Window.py:92: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.LeftPane.pack_start(page.LeftWidget,   True, True)
/usr/lib/python2.7/dist-packages/ccm/Window.py:95: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.show_all()
/usr/lib/python2.7/dist-packages/ccm/Widgets.py:1567: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self._table.attach (button, col, col+1, row, row+1, 0, xpadding=TableX, ypadding=TableY)
Loading icons...
/usr/lib/python2.7/dist-packages/ccm/Widgets.py:1572: Warning: g_object_set_qdata: assertion `G_IS_OBJECT (object)' failed
  self.show_all ()
Initializing compiztoolbox options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing detection options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing session options...done
Initializing staticswitcher options...done
Initializing regex options...done
Initializing decor options...done
Initializing scale options...done
Initializing opengl options...done
Initializing bailer options...done
Initializing wobbly options...done
Initializing fade options...done
Initializing place options...done
Initializing unitymtgrabhandles options...done
Initializing ezoom options...done
Initializing composite options...done
Initializing imgpng options...done
Initializing grid options...done
Initializing animation options...done
Initializing resize options...done
Initializing unityshell options...done
Initializing vpswitch options...done
Initializing expo options...done
Initializing workarounds options...done
Initializing obs options...done[/I]


And that's it. The terminal just hangs after that. It doesn't even return me to the prompt.

I also tried resetting ccsm with *gconftool-2 --recursive-unset /apps/compiz*
also did nothing.

Anyone have any ideas?

---

### Post by x371322 on 2011-08-10
Okay nevermind. I figured it out. All i did was go into terminal and reset unity with the *unity --reset* command. It took a while to run but it said it had to reset the window manager back to metacity, and now I can launch compiz again.

(which is odd because I tried the command *metacity --replace* a couple of times earlier, but it wouldn't work. The* unity --reset* did the trick though)

So for now all seems back to normal.

---


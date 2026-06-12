---
title: "OpenOffice Writer Artifacts (Redraw/Repaint/Rendering problem)"
date: 2010-01-09
forum: General Help
---

### Post by zardoz on 2010-01-09
Hello.

OpenOffice Writer produces strange line and character artifacts when deleting and adding lines in a document. The text below the modifications is rendered wrongly.
The only solution is to minimize and maximize the window again, press CTRL+SHIFT+R, or any other form to force a manual screen refresh.

There are quite a lot of resources on the web about that problem, but none helped me so far.

I use Ubuntu 9.10 64 bit on a Lenovo T61 Laptop with Nvidia Quadro NV 140m graphics card.
The problem occurs with and without the proprietary Nvidia drivers installed (tried both version 173 and 185). Also with and without visual effects enabled.
Also the hint somewhere here in the forum of activating "Force synchronization between X and GLX" (which was on by default) didn't do a thing.

Any further suggestions what I could try to get rid of that annoying problem?

Best regards,
Kai

---

### Post by mattgif on 2011-09-15
I'd like to bump this for those who, like me, are continuing to experience this problem.  This is a sort of chronicle of what's been tried, and where people have looked for help.

I've had this problem through the last 4 versions of Ubuntu.  It persists in 11.04 w/LibreOffice 3.3.3.  The glitch seems to be correlated with nvidia cards and compiz.  This bug report appears to concern this issue: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904?comments=all](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904?comments=all).  (Notice that the report was created in 2008.  While the status is currently "fixed", this doesn't seem to mean anything, as it has been marked "fixed" several times in the past.)

The received solution is to go into the Compiz settings and enable the workaround "Force synchronization between X and GLX."  While this works for some, it does not work in my case, or for others I know.  

Gentoo users seem to experience the same problem, and have a few fixes detailed here: [http://en.gentoo-wiki.com/wiki/Compiz](http://en.gentoo-wiki.com/wiki/Compiz).  The following, in particular, seems relevant:

>  Some users found there were screen refresh problems by default setting. Here is a trick if you would like to run compiz-manager. Edit the file /usr/bin/compiz-manager, and find the function named build_args(), remove the --loose-binding parameter for the COMPIZ_OPTIONS command. 

```
build_args()
{
	if [ $INDIRECT = "yes" ]; then
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS --indirect-rendering "
	fi
	if check_nvidia; then
		#COMPIZ_OPTIONS="$COMPIZ_OPTIONS --loose-binding"
		COMPIZ_OPTIONS="$COMPIZ_OPTIONS"
	fi
} 
```

Try to restart compiz-manager to make yourself lucky. 

Sadly, this still fails to solve the problem.  

And that, friends, is the state of the problem.  Persistent, frustrating, and largely ignored.

---


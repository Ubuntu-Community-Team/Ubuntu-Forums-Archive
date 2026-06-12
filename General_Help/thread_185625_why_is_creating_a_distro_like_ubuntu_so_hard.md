---
title: "why is creating a distro like ubuntu so hard ?"
date: 2006-06-01
forum: General Help
---

### Post by syxbit on 2006-06-01
i know this might sound ignorant, but what do ubuntu programmers need to do ?
they don't write programs etc..
isn't ubuntu just the linux kernel with gnome etc...
so, my point is, couldn't ubuntu Edgy Eft just be the same as dapper, but with the new gnome, openoffice, firefox, gaim and new linux kernel etc.. ?
i'm not saying ubuntu people don't work hard, i know they do, i just don't understand fully.

---

### Post by Shay Stephens on 2006-06-01
You must not have tried to install other distros ;-)

I tried a number before finding Ubuntu.  None of them worked right.  Ubuntu did.  The difference is that the team of "bon-bon eating slackers" that whip up a great distro.  They *do* program.  I don't know all they make, but the contribute patches and stuff back to Debian and generally raise the bar on what Linux can do.

Do worry about it, just enjoy.  As you gain experience, you too will likely marvel at what they have accomplished :-)

---

### Post by mattisking on 2006-06-01
I'm not the right person to answer this... I've not been with it long enough, but I'm bored waiting for the "official" word of the Dapper release so I'll tell you my take on it...

Each distro of Linux customizes the choices available into a whole. While there are major applications, each application package must be written for each system that it's released on. With Red Hat you get RPM's. For Debian/Ubuntu you get DEB's. These packages are occasionally supported by the actual developers of each application, but far more often, they are packaged by packaging teams that work to get all the dependencies resolved. 

As code is updated in whatever repository it lives in, be it cvs, subversion, bazar, whatever... each distro must import these updates and apply them to the packages contained. Often times one package update breaks another application and each distro must work to either fix the code "up-stream" (from the source in this case) or just fix the problem locally. When Breezy... Dapper... I forget now, switched to Firefox 1.5 from 1.0 there were major changes that had to be made to TONS of other applications that depend on the firefox package and the internal changes were dramatic enough to break tons of stuff.

Also, there are things like colors, themes, icons... BRANDING to deal with. Also, there are installers... most distros write their own or adapt an existing one for their needs. Many distros support "splash" screen at startup... some don't. Breezy added usplash for this purpose and then adapted it further to also "splash down". That wasn't a part of Gnome... it was part of the Dapper experience.

I don't really know how do to any better than that. I'm sure someone will.

---

### Post by swamytk on 2006-06-01
_Integration_ is the magic. 

Your kernel should integrate well with your hardware. Kernel to be customized to more generic way so that everyone's hardware is detected and working properly, at the same time maintaining the performance of kernel by not overloading with too many unnecessary modules.

All your applications should be well integrated with each other. The pre-requisite of each application may be another application, service, kernel feature, kernel module, hardware, etc.

---

### Post by David Corrales on 2006-06-01
Developers will also sometimes work on fixing bugs for an specific package and send the patch to HEAD. HEAD here means the original provider of the software. For example, if they work some time on the Gimp fixing bugs, they'll send the patches to HEAD to be incorpored into all of the Gimp releases.
And like others said, there's a huge work that goes with integrating software, creating all the necessary scripts, etc.

---

### Post by asimon on 2006-06-01
And spending half an hour browsing bugs at [Malone](https://launchpad.net/distros/ubuntu/+bugs) gives you a glimpse of the multitude of problems which creating a distro involves.

---


---
title: "Remote Desktop via Empathy or Jitsi?"
date: 2011-06-16
forum: General Help
---

### Post by amendt on 2011-06-16
Like a lot of us we help out our senior friends via Remote Desktop. I have found Empathy to be great for this, but for some reason my 11.04 desktop couldn't make the link to his 10.04 desktop so I tried to get him to install [www.jitsi.org](www.jitsi.org) because that to me seemed to be the easiest fix.  What do you recommend?

---

### Post by mikewhatever on 2011-06-29
I think TeamViewer is the easiest for remote desktoping. Jitsi looks very promising, but I'd wait for the stable release. Currently, there are several nightly beta builds every day, it's kinda crazy.

---

### Post by amendt on 2011-06-29
Thanks Mike!  Teamviewer even works on my Android, but I was hoping to use something that was GPL and community driven.  I found another neat program called [gitso]("http://code.google.com/p/gitso/")it is small and works on Mac Microsoft and Linux. Maybe Gitso should become my fall back program.

---

### Post by mikewhatever on 2011-06-29
Well, it's a VNC viewer, similar to the Desktop Viewer included by default. The problem with all of them is insecurity. They are OK to use on an internal network, but not over the internet. VNC can be made secure by tunneling it over SSH. Gitso still have it in the roadmap, but it looks like the program hasn't seen any development in over a year.

---

### Post by doas777 on 2011-06-29
for graphical remote access (across teh internet) I recommend NX (FreeNX/NeatX). it runs over ssh, so if you have a reasonably secure ssh config, you should be ready to go. easy to install, and clients in for many OSes. also performs much better than vnc based solutions. it does not however allow you to directly interact with teh interactively running user session, even if you login to the same account however, since ssh is tty based. personally i prefer it that way.

---

### Post by beccon on 2011-08-13
> **mikewhatever said:**
> I think TeamViewer is the easiest for remote desktoping.
It's the Skype of desktop sharing: Works pretty good - probably better than the competition - but you never know, who else is on the line. As data tends to be more sensitive than gaga on the phone - I'd be even more cautious with TeamViewer.

> **mikewhatever said:**
>  Jitsi looks very promising, but I'd wait for the stable release. Currently, there are several nightly beta builds every day, it's kinda crazy.
Meanwhile the have a (semi)stable version. The eternal Beta status has never been a problem to me - as there had been hardly any regressions and if, it had been fixed the other day. 

But that's me - the freelance consultant. A big IT departement might think different.

Jitsi's desktop sharing is - unlike Empathy etc. - not based on VNC or Remote Desktop but is part of video conferencing i.e. the screen is transfered by H264 video stream.

That has pros and cons: You can stream your screen (or parts of it) via vc equipments, MCUs etc. to a bunch of people - perfect to make presentations. Not so great when bandwidth is an issue. It can happen that artefacts etc. disturb the images.

And mentioning Skype in the beginning: It has desktop sharing too - the same applies here: You have to trust them. Jitsi has end to end encryption. 

Conrad

---


---
title: "Web Page Loads On Half of the Screen"
date: 2009-08-14
forum: General Help
---

### Post by ciamele on 2009-08-14
Hello, I have a strange issue. When I go to the message board [here]("http://forums.gatorsports.com/eve"), it only loads on the right half of the screen. Please see the attached screenshot. It's done this for quite a while, so I know it's not the most recent Firefox update.

Ubuntu 8.04
Firefox 3.013

Has anyone seen this before? Any ideas on how to fix it? Thanks in advance!

---

### Post by nikhilk on 2009-08-14
> **ciamele said:**
> It's done this for quite a while, so I know it's not the most recent Firefox update.

Well, to be absolutely sure that it is not a browser problem, can you try opening that page from some other browser and check?

---

### Post by nikhilk on 2009-08-14
OK, I just checked it myself. The page loads correctly in Opera and I saw the same problem as you in Firefox.

I thought Adblock or some other plugin might be the culprit but even in safe-mode I got the same problem.

So, I thought that the site might be checking user agent and is some browser specific. But even changing the user agent (I tried three IE, Opera and Netscape) did not help. Probably a bug with Gecko rendering engine?

---

### Post by PRC09 on 2009-08-14
Pretty sure it is a problem with the page itself.I have the same problem with Firefox but IE8 loads the page fine but wants to keep installing flash which is already installed.And it keeps wanting to over and over again.

---

### Post by lisati on 2009-08-14
Might be some kind of flash and/or plugin problem. There's a section at the bottom of the screen when I opened the web site that appears to be flash (or similar) based. Maybe the solution *could* be to have another flash-type plugin installed as well as what you already have but don't quote me on this.

edit (about a day later): seems to load correctly on my Ubuntu machine with FF 3.0.13

---

### Post by ciamele on 2009-08-15
The page loads correctly in the latest Firefox in Windows XP.

I'll try posting on one of their threads to let the admins know of the issue. If it is an issue on their side, maybe they can correct it.

---

### Post by ciamele on 2009-08-17
I upgraded from 8.04 to 8.10 and the problem was resolved.

---


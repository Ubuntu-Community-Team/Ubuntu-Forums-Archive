---
title: "How can I determine what repository a package is coming from?"
date: 2009-08-26
forum: General Help
---

### Post by jrothney on 2009-08-26
Hi there, hoping there is an easy answer to the above question. This likely applies across the board with ubuntu, but in my case it is specific to repos supporting my pvr.

I'm running mythbuntu 9.04 and have enabled two 3rd party repos:
- "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) jaunty release" (for vdpau support with myth & nvidia)
- "deb [http://ppa.launchpad.net/commandir-team/ubuntu](http://ppa.launchpad.net/commandir-team/ubuntu) jaunty main" (for IR support with myth)

I have done apt-get update and apt-get upgrade to pull in the packages from these repos and I believe that I am using these packages because:
- I am able to run mythtv & mplayer with the vdpau profile selected
- I am able to drive my pvr using my remote and the IR eye connected to the commandIR

All is well, and I really don't want to break anything. However, I am told there are new packages available for upgrade - they are all mythtv and nvidia packages. I like to keep my system as up-to-date as possible.

How do I know that the packages being recommended for upgrade are packages from the 3rd party repos I have specified and not simply the core ubuntu/mythbuntu repo?

Thanks in advance.

---

### Post by mkvnmtr on 2009-08-26
In my package manager if I make the window larger it tells me what repository the package comes from. If I wish to see everything from a repository i click on the origin button and see only packages from that repository. I use that option with the medibuntu repository a bit.

---

### Post by michy99 on 2009-08-26
It is extremely unlikely that the core Ubuntu repositories will have a newer version than the third party repositories.

---

### Post by jrothney on 2009-08-26
Thanks guys. I'll play around a little more with package manager and see if I can see where each one is coming from.

---

### Post by jocampo on 2009-08-26
> **jrothney said:**
> I really don't want to break anything. However, I am told there are new packages available for upgrade - they are all mythtv and nvidia packages. I like to keep my system as up-to-date as possible.
Thanks in advance.

There is a fine line between keeping your system as up to date as possible and keeping your system stable; this rule applies to Microsoft as well, not just Ubuntu. If you do not want to take the risk and break anything, do not download or upgrade "suggested" or "recommended" packages or, which is the same, try to use Ubuntu main repositories. Recent upgrades usually are not fully tested or have not been checked on different environments so there is a small possibility of a break during that process.

---


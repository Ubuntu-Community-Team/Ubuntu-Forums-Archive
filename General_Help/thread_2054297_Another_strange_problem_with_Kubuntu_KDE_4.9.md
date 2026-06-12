---
title: "Another strange problem with Kubuntu KDE 4.9"
date: 2012-09-07
forum: General Help
---

### Post by Epodx64 on 2012-09-07
The update manager is no longer prompting me for a password to update files? It's not a real big deal since this is a single user system but it seems like a major security flaw btw i'm using the updated muon software center & muon updater through [https://launchpad.net/~echidnaman/+archive/qapt](https://launchpad.net/~echidnaman/+archive/qapt)

---

### Post by bra|10n on 2012-09-07
Not a direct answer to your question but a suggestion;

```
sudo apt-get update && sudo apt-get dist-upgrade
```

and leave your present packaging worries behind you...

---

### Post by Epodx64 on 2012-09-07
I'm going to do a clean install once Kubuntu 12.10 comes out I pretty much have everything in beta form on my LTS heh but it runs good no real problems except the update manager having elevated permissions.

---

### Post by PaulW2U on 2012-09-07
> **Epodx64 said:**
> I'm going to do a clean install once Kubuntu 12.10 comes out I pretty much have everything in beta form on my LTS heh but it runs good no real problems except the update manager having elevated permissions.

12.10 will feature an updated muon but in the meantime there's always synaptic. ;)

---

### Post by Epodx64 on 2012-09-07
> **PaulW2U said:**
> 12.10 will feature an updated muon but in the meantime there's always synaptic. ;)

I accutally use synaptic over muon lol I tried Apper but that was frustrating Muon is alright I just don't understand why the update manager apparently has root privileges think I should just uninstall it and use synaptic? and apt-get to handle updates? or am I worrying to much over this that its a big security hole?

---

### Post by PaulW2U on 2012-09-07
> **Epodx64 said:**
> I accutally use synaptic over muon lol I tried Apper but that was frustrating Muon is alright I just don't understand why the update manager apparently has root privileges think I should just uninstall it and use synaptic? and apt-get to handle updates? or am I worrying to much over this that its a big security hole?

Well it's never happened to me but I rarely use muon now. I use aptitude and synaptic most of the time depending on my needs.

I've just done a quick Google search and I found a number forum posts made by users with the same problem. I'm off out for the day shortly so I don't have time to look and test for myself.

muon is getting better but even though we're up to version 1.4 now, I still look at it as an application under development.

---

### Post by Epodx64 on 2012-09-07
> **PaulW2U said:**
> Well it's never happened to me but I rarely use muon now. I use aptitude and synaptic most of the time depending on my needs.

I've just done a quick Google search and I found a number forum posts made by users with the same problem. I'm off out for the day shortly so I don't have time to look and test for myself.

muon is getting better but even though we're up to version 1.4 now, I still look at it as an application under development.

Well, hopefully by 1.5 these little bugs are fixed because I think Muon does have potential it's kind of growin on me the past couple of months but I still prefer the command line as long as I know what I'm getting. apt-get is quite powerful why'd they jettison aptitude?

---

### Post by Epodx64 on 2012-09-07
I was looking through my software sources and went to the qapt ppa and found a bunch of muon software that didn't get updated I downloaded all the new versions from the ppa and removed the older ones there's no more problem with the permission elevation in the new software strange it didn't offer to update these packages for me. 

p.s.

The new version is indeed 1.4

---


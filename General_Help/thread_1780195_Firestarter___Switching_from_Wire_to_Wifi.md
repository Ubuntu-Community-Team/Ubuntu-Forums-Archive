---
title: "Firestarter:   Switching from Wire to Wifi"
date: 2011-06-11
forum: General Help
---

### Post by held7over on 2011-06-11
Ubuntu 10.10  Firestarter 1.0.3

My Desktop gets moved around a lot, meaning, I switch between Wire and Wifi often. I have been re-running the Firestarter wizard (when I remember to do so) each time I change from one mode of communication to another.

However, in Firestarter, on the STATUS page I can see both my wired connection and my wifi connection along with transfer data stats, despite which kind of Internet connection I have told Firestarter my computer is using. 

Does this mean Firestater is actually protecting both routes and that I don't need to rerun the wizard to customize Firestarter for protecting the newest mode of communication I am using between these two different choices of Internet contact???

Thanks! :p

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **held7over said:**
> Ubuntu 10.10  Firestarter 1.0.3

My Desktop gets moved around a lot, meaning, I switch between Wire and Wifi often. I have been re-running the Firestarter wizard (when I remember to do so) each time I change from one mode of communication to another.

However, in Firestarter, on the STATUS page I can see both my wired connection and my wifi connection along with transfer data stats, despite which kind of Internet connection I have told Firestarter my computer is using. 

Does this mean Firestater is actually protecting both routes and that I don't need to rerun the wizard to customize Firestarter for protecting the newest mode of communication I am using between these two different choices of Internet contact???

Thanks! :p

I don't have this issue in GUFW or UFW..  And I use both.  Weird. I used firestarter years ago, but it just seemed buggy to me. The only thing firestarter provided me differently was silently dropping pings..   Now I have business router that can be configured do that for me and I can keep the abilty to ping my system for network debugging instead (what it was intended for originally).... just my two cents

---

### Post by held7over on 2011-06-11
Thanks for your thoughts, linuxinstalledfromhdd. I have installed DD-WRT on my Linksys Router, but I have a lot to learn about it. I suspect it probably has some answers for me, but I like to have all the road blocks I can get in place. However, since you brought up UFW, I am noting that have UFW on my list to look at in the future. Can it cover both potential connections at the same time, so that I don't have to remember to switch my firewall settings when I change from wire to wireless? 

I am slowly creating my own server which now is outfitted with virtual environments on it using OpenVZ (no graphics implemented for speed). Don't mistake this for me knowing anything....I am just blindly following HOWto directions...Ha.

My next project is to create a virtual environment which contains my firewall. I don't seem to have found the right stuff to study, though. I get lost trying to read Smoothwall's documentation, and I am not sure which version of their stuff to use.....it is more complication and time from my perspective than I want to do right now. I am looking for a simple, yet effective firewall that can act to route incoming IP communications to the correct virtual environment. I'd really like that to be easy to set up and understand, yet effective.

Can UFW do this? Can Firestarter do this?

After I get past setting up the firewall, next comes creating anther virtual environment and putting an Apache type app in it to route URL type communications to their correct Virtual Environment Container. I am hoping to find an EASY yet effective Web Server app for that also, so that I can finally actually start working on what I wanted to do in those Containers. If you have any suggestions for an easy Web Server to learn and use, I'd appreciate your input here also.

---


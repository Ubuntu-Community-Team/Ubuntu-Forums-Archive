---
title: "ubuntu 11.10 spring engine ppa:spring/ppa"
date: 2012-01-14
forum: General Help
---

### Post by AgentZ86 on 2012-01-14
Hi 

I added the pps:spring/ppa to the software center sources because the current version listed doesn't run anything they all require version .85 and not .82 versions

Anyhow I'm not sure how to unstall the spring lobby from the software center there does not seem to be any new entries with this added software source

Please advise
Thanks

---

### Post by howefield on 2012-01-14
Suppose you've done a reload of your software packages since adding the ppa ?

Spring in Oneiric is version .82.7.1 and Spring Lobby version 0.130.

After adding the ppa and reloading the packages, the versions move to .85.0 and 0.140

---

### Post by AgentZ86 on 2012-01-14
> **howefield said:**
> Suppose you've done a reload of your software packages since adding the ppa ?

Spring in Oneiric is version .82.7.1 and Spring Lobby version 0.130.

After adding the ppa and reloading the packages, the versions move to .85.0 and 0.140

how do I reload the package list ? 

I thought it would do it once you restart the software center ? 

And do I have to install the .82 version first or can I go directly to the latest version ?

Sorry for that muli questions and thanks for the reply

---

### Post by AgentZ86 on 2012-01-14
scratch that, I installed synaptic and reloaded that way

thanks

---

### Post by howefield on 2012-01-14
After updating you will get the updated version straight away, the other method of updating the package lists would be to run sudo apt-get update from a terminal.

To be honest, I don't see a way of updating package lists in Software Centre, usually tend to use Synaptic or apt-get.

---

### Post by AgentZ86 on 2012-01-14
> **howefield said:**
> After updating you will get the updated version straight away, the other method of updating the package lists would be to run sudo apt-get update from a terminal.

To be honest, I don't see a way of updating package lists in Software Centre, usually tend to use Synaptic or apt-get.

I got it installed, thanks.

I tried to run the spring lobby but not getting any battle lists
Says disconnected from server when I login or restister new nick name ? 

Do you get the lobby running ?

---

### Post by howefield on 2012-01-14
> **AgentZ86 said:**
> Do you get the lobby running ?

Ahh.. no :)

My interest was only in helping you with the original question, not to actually play the game. I simply checked the ppa out in a VM.

---

### Post by grahammechanical on 2012-01-14
For those reading this who do not know, another way to update the software packages or repository lists is the open Update Manager from the power cog menu and to click check. In a similar way clicking settings in Update Manager will get you to Software Sources where you can add a ppa.

The Software Sources utility will be removed from System Settings in 12.04.

Regards.

---

### Post by AgentZ86 on 2012-01-14
> **howefield said:**
> Ahh.. no :)

My interest was only in helping you with the original question, not to actually play the game. I simply checked the ppa out in a VM.

lol, ok thanks

Just wanted to make sure it was not an install problem, I'm assuming it's installed correctly.

---

### Post by AgentZ86 on 2012-01-14
> **grahammechanical said:**
> For those reading this who do not know, another way to update the software packages or repository lists is the open Update Manager from the power cog menu and to click check. In a similar way clicking settings in Update Manager will get you to Software Sources where you can add a ppa.

The Software Sources utility will be removed from System Settings in 12.04.

Regards.

Hi I did know about that but where is the reload to reload the packages once you add a software source

I could not find it, so I installed synaptic and clicked reload

I thought it would have done it automatically or a reload button or something from the software center

---


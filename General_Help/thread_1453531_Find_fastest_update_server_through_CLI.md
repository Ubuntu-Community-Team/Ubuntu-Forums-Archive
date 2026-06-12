---
title: "Find fastest update server through CLI"
date: 2010-04-13
forum: General Help
---

### Post by Paqman on 2010-04-13
The graphical package management tools like Synaptic have a nice feature where you can scan for and connect to the fastest server. I'm writing a setup script for minimal installs and would like to offer the option to scan for a fast server, does anybody know how to achieve this through the command line?

---

### Post by Paqman on 2010-04-17
Anyone?

---

### Post by Paqman on 2010-05-11
One last bump, just in case...

---

### Post by CharlesA on 2010-05-11
I don't know if it's possible, or even how to do it. I just know that the "default" server maxes out my download bandwidth (granted I have horribly slow internet but still)

---

### Post by QLee on 2010-05-11
[QUOTE=Paqman]One last bump, just in case...[/QUOTE]

I've used apt-spy in Debian for that purpose, since you are an advanced user and coder you might be able to download the source for that and modify for Ubuntu repositories or take a piece of it for your script. I have no idea of how big of a job that might be, chances are probably better for you to get a useful answer if you post your query in the programming sub forum.

---

### Post by tgalati4 on 2010-05-11
Take a laptop from your server location and perform an update and determine which are the fastest servers, then manually edit your sources.list on your servers.  I doubt the fastest servers would change much from your geographic location. If the servers are down, then you have bigger problems.

---

### Post by Paqman on 2010-05-11
> **QLee said:**
> chances are probably better for you to get a useful answer if you post your query in the programming sub forum.

I did consider that, but i'm just Bash scripting. Nothing clever at all.

---

### Post by Paqman on 2010-05-11
> **tgalati4 said:**
> Take a laptop from your server location and perform an update and determine which are the fastest servers, then manually edit your sources.list on your servers.

It's a script for users to automate the minimal install process. See below!

---


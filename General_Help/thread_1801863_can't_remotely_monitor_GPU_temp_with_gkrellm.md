---
title: "can't remotely monitor GPU temp with gkrellm?"
date: 2011-07-11
forum: General Help
---

### Post by ceejay on 2011-07-11
Hello there!

I want to remotely monitor an HTPC I'm building: gkrellm seems like just the thing. I've installed gkrellmd (and gkrellm) on the HTPC, and also gkrellm on the machine I want to do the monitoring from.

I can remotely monitor the HTPC with "gkrellm -s htpc".

So far so good...

BUT, when I run gkrellm on the HTPC itself, I have the option of monitoring the temperature of my nvidia GPU - it shows up as an option under Builtins/Sensors/Temperatures. All I have to do is tick the box and it shows up.

However, when I run gkrellm -s ... on the other machine, the GPU temp is not presented as an option. I might guess that this is because this machine doesn't have an nvidia card itself, though I would have hoped that was irrelevant.

Any suggestions?

TIA

---

### Post by ceejay on 2011-07-11
Both machines are running 11.04, perhaps I should add. 

Any ideas?

---


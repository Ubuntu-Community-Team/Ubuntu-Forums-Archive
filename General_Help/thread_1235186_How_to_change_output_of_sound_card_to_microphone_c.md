---
title: "How to change output of sound card to microphone connector"
date: 2009-08-08
forum: General Help
---

### Post by deviant on 2009-08-08
Hello guys. 

Quick question: is it possible to instruct the driver / sound card to output the sound on the microphone connector instead of the default one?
I`m asking these because I`ve just damaged my default headphone connector from the notebook and I can`t afford to take it to service right now since it will take at least one week until I will get it back. 
And I can`t live without my music either :(

My sound card is:

```
itch@sisif:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

And on the front of the notebook I have 3 connectors: 
*headphone 
*microphone
*front speaker (I believe)

---

### Post by Redache on 2009-08-08
Sadly no as the Microphone Connector is an Input rather than an output.

Have you tried the Front Speaker Port? That should be an output but it might be a bit hot for your Headphones.

---


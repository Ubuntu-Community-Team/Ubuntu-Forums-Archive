---
title: "Really annoying netcat error!"
date: 2011-04-08
forum: General Help
---

### Post by Legitguy on 2011-04-08
Hello! recently I started getting an error whenever I tried to open a port and listen using netcat. Here is what happened: 

My command: 'nc -vv -l 23' 

And I keep getting: 
 'Warning: Inverse name lookup failed for `0.0.0.23' Listening on any address 39114' 

I've been playing around with my shells and I switched to /bin/ash/, but i switched back and the finger command confirms that I'm using /bin/bash. Any suggestions? 

[EDIT!] 

I wasn't specifying ports with the -p option! i was using nc -l 22, instead of: nc -l -p 22. 

I've never had to do this before, but still, I should've done it, so my bad :)

---


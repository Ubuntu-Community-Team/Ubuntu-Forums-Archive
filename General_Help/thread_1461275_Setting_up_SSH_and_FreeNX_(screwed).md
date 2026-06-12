---
title: "Setting up SSH and FreeNX (screwed?)"
date: 2010-04-24
forum: General Help
---

### Post by Gutter22 on 2010-04-24
After using the default remote desktop I decided I was going to set up a FreeNX server on my recent install of Ubuntu 9.10. Trying to follow the tutorials on the net I somehow managed to miss something and things aren't going so well. 

First, I have no idea how to tell if my SSH server is running and setup correctly. I also have no clue on how to setup and use the SSH bsa and rsa keys. Those parts of the tutorials lost me in a maze. 

Second...FreeNX seems to be screwed as well. The client seemed easy enough in Vista, but setting up the server in the terminal is daunting. I'm also having problems with the settings such as username and setting it up to use custom keys. Some parts of the tutorials pointed to files that didn't exist so I got really lost.

So, is there a way to wipe away all traces of SSH and FreeNX to try again? It seems so screwed its hard to trace down all the problems. Or is there a better way to manage my mess? 

Can someone explain the basics that I would need to setup SSH and FreeNX on my Ubuntu machine so that I can access it through Vista? Such as the order in which things should be installed and settings that need to be changed in both?

---

### Post by v1ad on 2010-04-24
sudo apt-get install fuse fuse-sshfs 
this will get your ssh up and running.

---

### Post by Gutter22 on 2010-04-24
When I used that I got:   ```
E: Couldn't find package fuse
```

---

### Post by Gutter22 on 2010-04-26
SSH seems to be up and running now. 

However, FreeNX is still failing to connect. I get a failed to auth  message every time. I believe it is related to my keys. Can someone  explain which keys go where?

---


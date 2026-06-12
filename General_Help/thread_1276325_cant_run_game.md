---
title: "cant run game"
date: 2009-09-26
forum: General Help
---

### Post by jakebros1 on 2009-09-26
i wanted to play this game its like runescape but its a diffrent server that you need to download and its not like a web browser u can just play on u need to download a file and i have it on my laptop but since i share it with family i want to downlaod it on my computer that is using ubuntu
i have wine and i tried running it but its complicated if anyone knows what to do please help the game site is called 

[http://smiteme.tk/](http://smiteme.tk/) 
if u end up downloading or figuring how to download it on ubuntu please post back:)

---

### Post by LoloftheRings on 2009-09-27
The problem is.. It's a java game. So you will have to install java (windows version) in wine.

After installing wine, you can run the game by creating this script in the game client directory:

```

#!/bin/sh
wine java -Xmx500m -cp .;./bin; EGUI

```

Right click the script, go to properties -> permissions and tick the executable box.

I'm not sure if this is possible, but you could give it a try.

---

### Post by jakebros1 on 2009-09-27
what  i dont understand can u explain it whaat to do again

---


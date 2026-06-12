---
title: "Starting a Process with Priority"
date: 2010-04-29
forum: General Help
---

### Post by mastermindg on 2010-04-29
I haven't seen a definitive response here yet so I figured I'd give it....

I've set Firefox to run at lower priority due to it's "buggy" nature lately. I accomplished this by:

1) Creating a shell script called firefox under /usr/local/bin:

```
#!/bin/bash
nice -15 /usr/bin/firefox
```

2) Make it executable: 

```
sudo chmod +x /usr/local/bin/firefox
```

That's it! There was an earlier article that suggested renice, but (as it implies) it's used after a process already exists.

---


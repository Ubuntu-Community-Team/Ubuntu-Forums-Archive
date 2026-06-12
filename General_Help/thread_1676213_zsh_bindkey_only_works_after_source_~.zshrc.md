---
title: "zsh bindkey only works after source ~/.zshrc"
date: 2011-01-26
forum: General Help
---

### Post by Razor X on 2011-01-26
Ok, so this has been bugging me for a long time and I finally decided to ask about it. I think this is a zsh issue since I have the same problem on a FreeBSD install. If I have bindkey commands in my .zshrc file, they will only work after I run 
```
source ~/.zshrc
```For example, if I put into my ~/.zshrc
```
bindkey "^E" end-of-line
```I will only get an ^E output instead of my cursor going to the end of line. As far as I can tell, everything else in my .zshrc file seems to work fine without having to run the source command. I find this very strange, any ideas are appreciated!

I'm running Kubuntu 10.10 x64 with the latest updates.

---


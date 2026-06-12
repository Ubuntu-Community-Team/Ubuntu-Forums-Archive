---
title: "create a new prog launch keyword"
date: 2009-11-06
forum: General Help
---

### Post by mickmouse13 on 2009-11-06
I know that in a terminal i can type 
```
Firefox youtube.com
```and this will open a firefox web browser and go to [http://www.youtube.com/](http://www.youtube.com/)
i would like to create something where i simply open a terminal and type YT and it will open firefox and youtube. 
Either explain how to make this or show me to the place where all the others are please. 
I'm running ubuntu 9.10


to make sure we are clear i was to be able to type YT into the terminal and it will open firefox and go to youtube.com.

---

### Post by falconindy on 2009-11-06
From the terminal, type:

```
echo "alias yt='firefox youtube.com &'" >> $HOME/.bashrc
```
Close and reopen the terminal, and 'yt' will be an alias to opening youtube on firefox. It's case sensitive, so if you'd rather it be YT just make the appropriate change.

---

### Post by mickmouse13 on 2009-11-06
thanks, worked great.

---


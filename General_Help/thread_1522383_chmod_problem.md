---
title: "chmod problem"
date: 2010-07-02
forum: General Help
---

### Post by theniks on 2010-07-02
Hi
I am trying to install vtigercrm with ubuntu and i have some really basic questions (some even downright silly). 
```
sudo chmod  chmod 777 config.inc.php

```I ran this command and i get error 
```
chmod: invalid mode: `chmod'
Try `chmod --help' for more information.

```
pretty basic question here :) tried searching forums but couldnt find anything :)
Thanks in advance
Regards
Nik

---

### Post by marshmallow1304 on 2010-07-02
You put chmod twice.  You want
```
sudo chmod 777 config.inc.php
```

---


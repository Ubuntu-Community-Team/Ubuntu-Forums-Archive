---
title: "where do i find the sudo source?"
date: 2012-05-12
forum: General Help
---

### Post by manarius on 2012-05-12
hi people

sorry if that question offends anyone, noobs have questions too ;)

i just wanted to quickly ask where i might find the uncompiled sources for the sudo command?

the s on my keyboard is not working too well so i often mistype
udo
instead of 
sudo

this is no problem, and cp'ing sudo to /usr/local/lib/udo of course solves the basic problem,
but since i am a freak (who would have guessed ;) ) i would love to add some ascii art to that command.

i basically want to show an ascii picture of udo lindenberg and then continue with the sudo as usual.

i know that this is not necessary and i know that its a waste of your time, so please accept my sincere apologies for that ;)

thanks for reading,
big thanks for helping,
bigger thanks for telling me how you would echo this in the console "the right way" ;) [ i for sure will be able to get this done, but if you want to give any advise or help, just do so :) ] 

have fun
manarius

---

### Post by nothingspecial on 2012-05-12
```
apt-get source sudo
```

Note, you don't need sudo to download source code.

Have fun and be careful :)

---

### Post by steeldriver on 2012-05-12
... I would think it would be FAR better to wrap a call to /usr/bin/sudo in a little shell script called 'udo' and do your ascii art within THAT

```

#!/bin/bash

# do your stuff here

/usr/bin/sudo "$@"

```

---

### Post by whatthefunk on 2012-05-12
It would be so much easier to make an alias in .bashrc assigning "udo" to "sudo."

---

### Post by phrak on 2012-05-12
> **whatthefunk said:**
> It would be so much easier to make an alias in .bashrc assigning "udo" to "sudo."

this is exactly what I was thinking

```
alias udo='sudo '
```

I have several alias' for my complete inablitiy to spell.  To the point that I carry around a copy of my .bashrc.

---


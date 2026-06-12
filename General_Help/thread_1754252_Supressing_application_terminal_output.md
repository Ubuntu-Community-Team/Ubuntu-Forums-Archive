---
title: "Supressing application terminal output"
date: 2011-05-09
forum: General Help
---

### Post by doriad on 2011-05-09
When I run 'kile&' from a terminal, I get messages like this:

Application asked to unregister timer 0x1a000020 which is not registered in this thread. Fix application.

Is there a way to run programs and suppress all of this sort of output? It is always annoying to return to my terminal to see it flooded with that sort of thing.

Thanks,

David

---

### Post by Buntumatic on 2011-05-09
Sure, you can send it to /dev/null

[http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

---

### Post by doriad on 2011-05-09
Right, so 

kile &> /dev/null 

would do the trick. But then I have to type all of that every time I want to run something :). Is there a way to set a system wide "always &> /dev/null unless otherwise specified" or something like that?

David

---

### Post by Buntumatic on 2011-05-09
Create an alias or wrapper script. Remember, what's in PATH first will be run, even if it has same filename.

---


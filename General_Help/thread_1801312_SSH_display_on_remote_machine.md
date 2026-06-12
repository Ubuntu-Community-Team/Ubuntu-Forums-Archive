---
title: "SSH display on remote machine"
date: 2011-07-10
forum: General Help
---

### Post by Gawains Green Knight on 2011-07-10
I have SSH -X working fine, displaying stuff that's running on the remote machine on my local machine. 

But how do I display on the remote machine? I did this many years ago on unix and seem to recall that this was either default or a simple case of setting DISPLAY....

---

### Post by nothingspecial on 2011-07-10
Depending which shell you are using
```

export DISPLAY=:0.0
```

or 
```

DISPLAY=localhost:0.0 ; export DISPLAY
```

---

### Post by Gawains Green Knight on 2011-07-10
Thanks!!!

---

### Post by nothingspecial on 2011-07-10
No problem :D

---


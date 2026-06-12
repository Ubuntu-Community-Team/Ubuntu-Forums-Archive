---
title: "How can I flush my dns?"
date: 2006-06-06
forum: General Help
---

### Post by Rackerz on 2006-06-06
How can I flish my dns? Or better yet just completely remove and re-add my internet device (eth0). MSN wont connect using Gaim, Kopete or aMSN. They wont connect because they say they can't connect to the msn server. In windows I can use MSN Messenger fine and I **_NEED**_ MSN. So back to Windows I go?

---

### Post by ifokkema on 2006-06-06
[QUOTE=Rackerz]How can I flish my dns? Or better yet just completely remove and re-add my internet device (eth0). MSN wont connect using Gaim, Kopete or aMSN. They wont connect because they say they can't connect to the msn server. In windows I can use MSN Messenger fine and I **_NEED**_ MSN. So back to Windows I go?[/QUOTE]

Not sure if I get your question right...
But you can set your DNS in your /etc/network/interfaces file.
'Stopping' and 'starting' your eth0 is done by
```
sudo ifdown eth0
sudo ifup eth0
```

Hope this helps!

Ivo

---

### Post by mscman on 2006-06-06
You could do a full networking restart by running
```
sudo /etc/init.d/networking restart
```

Or if that's not working (i.e. networking is kind of frozen) try
```
sudo /etc/init.d/networking force-reload
```

Stop networking completely by doing 
```
sudo /etc/init.d/networking stop
```

Restart it with
```
sudo /etc/init.d/networking start
```

Not sure if this is what you need, but worth a shot...

---


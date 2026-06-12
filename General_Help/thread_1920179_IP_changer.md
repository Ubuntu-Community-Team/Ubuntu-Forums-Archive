---
title: "IP changer?"
date: 2012-02-04
forum: General Help
---

### Post by byzantines2000 on 2012-02-04
how would someone go about doing this? just curious, im bored, cant sleep and i think imma just stay inside today.

---

### Post by haqking on 2012-02-04
> **byzantines2000 said:**
> how would someone go about doing this? just curious, im bored, cant sleep and i think imma just stay inside today.

go about doing what ? you never asked a question.

If you mean from your title how do you change your IP ?

use network manager or edit your /etc/network/interfaces file

if you mean your public IP when on the internet then you can get a static one from your ISP or if it is dynamic then that means it changes anyways.

If you mean so surfing sees a different address to the one allocated you then you can use anonymiser services such a TOR or by visiting sites such as [www.hidemyass.com](www.hidemyass.com)

Peace

---

### Post by Dangertux on 2012-02-04
Alternatively to do it without editing a file (no persistance)

you can 

```

ip addr add 192.168.1.53 dev eth0 label eth0

```

or 

```

ifconfig eth0 192.168.1.53 up

```

Hope this helps (note these will not change the IP assigned by your ISP)

---


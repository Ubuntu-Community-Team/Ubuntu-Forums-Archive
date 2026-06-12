---
title: "block inbound ip"
date: 2009-10-26
forum: General Help
---

### Post by jmore9 on 2009-10-26
Can anyone explain simply how to use iptables to block or drop silently connection attempts to my machine.

I have read the ubuntu page on iptables but i am still somewhat confused.

something like iptable drop xxx.xxx.xx.xx I have totaly forgotten how to do that.

Thanks in advance for any help any one can provide.

---

### Post by kbielefe on 2009-10-26
I recommend using gufw.  Nice graphical interface, and sets up all that low level stuff behind the scenes, so you don't always need the gui up.

---

### Post by The Cog on 2009-10-26
gufw would indeed be the recommended GUI. 

But do you really need it? If you don't want any incoming connections, then the simplest solution is simply not to install any services that would accept incoming connections. By default, Ubuntu doesn't have any such services running so it won't accept incoming connection requests anyway. And if you were to install a listening service, you would have to reconfigure the firewall to allow connections in to it again anyway.

---


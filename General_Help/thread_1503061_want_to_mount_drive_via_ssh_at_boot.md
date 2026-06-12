---
title: "want to mount drive via ssh at boot"
date: 2010-06-06
forum: General Help
---

### Post by fro1269 on 2010-06-06
I want to automatically mount an SSH server on boot. I am able to do this manually by running this script after I reboot

```

#!/bin/bash
clear
sshfs -o idmap=user user@server:/ /home/fro1269/sshmount

```

I have put the script in /etc/networking/if-up.d/ 
but it does not mount after the network is connected. This is on a laptop that connects via wifi. So my network connection does not start until a few seconds after the desktop loads. I am running 10.04. Any ideas?

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
Add ```
sleep 30
``` to the top of your script and then add the script to startup applications.

---

### Post by fro1269 on 2010-06-06
Thanks! 30 worked fine but there was a little too much delay. I played around and it turns out 15 gave it just enough time to connect and have a little extra just in case my router is having a bad day. I now get a OPENSSH dialog box where I can authenticate.

Is there a way i can include the password for the server in the script so I do not have to enter it in every time?

Thanks again for the quick response.

---

### Post by Sin@Sin-Sacrifice on 2010-06-06
I know there's a way... I've seen it before but I don't remember. You're gonna have to read [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---


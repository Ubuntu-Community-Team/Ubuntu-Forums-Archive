---
title: "Remote Desktop Connection"
date: 2010-08-22
forum: General Help
---

### Post by DavidG24 on 2010-08-22
Hi guys,

I was wondering if someone would be able to clear up a few questions I have in relation to Remote Desktop Connections between two Ubuntu 9.10 x64 systems.

I have a PC and Laptop both running Ubuntu 9.10 and for both I have set the Remote Desktop Connections so that its allowed. Whilst using the prepackaged Remote Desktop Application I am able to Remote Connect, however I have to accept on the machine I'm trying to connect to; i.e. if I try to connect to my PC from my Laptop, I have to move to my PC and click the 'okay to connect' option. Is there a way I can setup on my PC that I don't have to do this? (I thought setting a password would be the trick but no dice!)

Any tips/starting points would be greatly appreciated

Cheers,

David

---

### Post by Morrad on 2010-08-22
I'm running a very minimal Ubuntu install, so I can't find the menu option corresponding to this, but in your "Remote Desktop Preferences" window, shouldn't unchecking the 3rd checkbox ("Ask for your Conformation") do what you describe?

I'm assuming the preferences window looks like it does here: [http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/allow-remote-control-to-your-desktop-on-ubuntu/)

---

### Post by DavidG24 on 2010-08-25
Hi Morradd,

Thanks for that, about 20 minutes after I posted it I realised what a trivial question it was.

Cheers,

David

---

### Post by CharlesA on 2010-08-25
In any case, please use a strong password for the Remote Desktop service, as it is one of the ways a machine can become compromised, if VNC (vino is what Ubuntu uses for remote desktop access, and is based on VNC) is allowed access to the internet.

---


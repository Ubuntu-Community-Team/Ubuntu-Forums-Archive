---
title: "editing Limits.conf... read only?"
date: 2010-06-26
forum: General Help
---

### Post by HunterGathererDrone on 2010-06-26
Total noob here, but I'm figuring things out.  I'm having problems installing Ardour because of JACK, and troubleshooting the situation using previous discussions.  Honestly nothing is helping.  JACK will not connect and the message reads: 

 p, li { white-space: pre-wrap; }  Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10


When I try to access the limits.conf its a read only and will not allow me to edit it because "I am not that owner, I cannot edit these permissions"  and I am logged in as the only name I supplied on the install.  Is there an administrator login?  How come I don't have access to edit this file?  I'm digging what Ubuntu has to offer quite a bit, but these little things I'd love to get fixed so that I can use Ardour.  Thanks for you help in advance.

Justin

---

### Post by Insanexyz on 2010-06-26
open terminal,

type:

sudo gedit /pathtoyourfile/

---

### Post by HunterGathererDrone on 2010-06-26
All that did was bring up a blank page.  Where do I go from there?

---

### Post by HunterGathererDrone on 2010-06-26
Nevermind got it, though it didn't fix my original problem with JACK.

---


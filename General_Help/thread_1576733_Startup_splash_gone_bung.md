---
title: "Startup splash gone bung"
date: 2010-09-17
forum: General Help
---

### Post by Jonny87 on 2010-09-17
This is some thing that I've noticed with any install of Ubuntu whether its regular Ubuntu or Kubuntu etc. The splash that comes up with the distro name Ubuntu/Kubuntu on start up look perfectly fine and as it should until I've installed my Nvidia drivers. then it goes all bung.

[LIST]
[*]Lower Resolution
[*]Slightly different colouring
[*]and Not taking up the whole screen.
[*]Sometimes it even sits slightly to the right.
[/LIST]
Is there a way that I can fix this? I know its nothing all that major but it would be nice if it looked as its meant to.

---

### Post by themusicalduck on 2010-09-17
That happens because the Nvidia drivers don't have a particular feature that works well with Plymouth, that the open source drivers do have.

This is the fix I used - [http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html](http://www.ubunturoot.com/2010/04/how-to-get-plymouth-working-with.html)

I always recommend that method to people, but just once someone did say that it borked their bootup so bare that in mind. It could easily be reversed from a live CD though if needed and I don't see why it shouldn't work if it's followed properly. I just feel like I ought to warn people anyway :P

My splash still sits slightly offcentre though, but at least it's the right resolution.

---


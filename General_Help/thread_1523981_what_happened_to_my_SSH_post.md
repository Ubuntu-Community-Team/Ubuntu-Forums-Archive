---
title: "what happened to my SSH post/"
date: 2010-07-04
forum: General Help
---

### Post by kaykav on 2010-07-04
I posted a ques. about an hour ago. Can't find it. What happened?
    Thanks

ps Maybe I didn't fill in the prefix.
  I'll start over.................

---

### Post by J V on 2010-07-04
[Search > Find all your posts]("http://ubuntuforums.org/search.php?do=finduser&u=213957")

Looks like you need to start over...
[ ]("http://ubuntuforums.org/search.php?do=finduser&u=213957")

---

### Post by kaykav on 2010-07-04
I can't seem to get into this 'SSH' thing. I have been  trying to understand it all. I bought a book $20. read articles,tutorials,all to no avail. There is something everyone is not telling me to do. I think I need step by step instructions. Portforwarding,key-generation,downloading any apps, using proper files, dialog box entrees, all this is a little confusing.  I'm told to enter a remote machine address using .com at the end of address. My computers don't have a .com for an address. Do they? They have an octet address.  Need help.
                thanks

---

### Post by J V on 2010-07-04
The only question in there was the address: Yes they have an octet address, use that.

---

### Post by Iowan on 2010-07-04
I suppose it depends what you want SSH to do for you... I use it to access my server from inside my network, so the IP address works (no .com required). In fact, my local DNS server makes t possible to connect via "SSH machinename". I haven't set up keys, so I get prompted for a password.

---

### Post by kaykav on 2010-07-04
OK now I entered an octet address, but was 'Connection refused'.
         what do I need to do to connect to my other computer?
                          Thanks

---

### Post by J V on 2010-07-04
Port forwarding... find out which port you are connecting to, and configure your router to forward that port... It gets more complicated from here, there will be other guides somewhere...

---

### Post by kaykav on 2010-07-04
Thanks for your input.......My quest continues.

---

### Post by Iowan on 2010-07-04
Are your client and host on the same side of the router (are they in the same subnet)? If so, port forwarding should be unnecessary. [Here]("https://help.ubuntu.com/community/SSH") is a help page that might be useful...

---


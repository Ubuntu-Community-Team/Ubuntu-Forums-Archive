---
title: "Function of Remote Desktop?"
date: 2009-11-26
forum: General Help
---

### Post by russet_wolf on 2009-11-26
I've heard of it, but I want to know, what exactly does it do?
I get that you get access to the "Desktop environment" from another computer, but can you also access all the files and stuff on the computer, or...? I'm not clear on the full function of this feature.

Any explanation would be appreciated. Thank you!

---

### Post by XCan on 2009-11-27
You can view and edit all your files. If you want to transfer the files over remotely, you can use, for example, ssh.

---

### Post by audiomick on 2009-11-27
If you think back to the old days when computers were as big as a wardrobe and the users all logged in via "brainless" terminals, that's more or less what is happening.

The commonest usage on desktop computers is for administrators who need to  do stuff on one of the computers the are looking after. With one of the remote desktop applications they can manipulate the computer they need to fix without actually having to go to where the computer is physically.

I have used VNC and windows Remote Desktop in a windows environment to adjust PA systems. One computer is connected to the Mixing desk, or digital audio matrix. The connection is either network or USB, depending on the device.  A second computer, usually a laptop, which doesn't even have to be all the fast, is networked to the first and accesses the desktop of the first via wireless lan. This allows one to walk around the hall or open air location and here the adjustments being made at the point they are relevant for, instead of having to walk back and forwards adjusting then listening, or telling a colleague by radio what to adjust.

---

### Post by bodhi.zazen on 2009-11-27
I assume "remote desktop" == VNC or FreeNX

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

Take care, VNC servers are the most often cracked on these fourms and the only security you have is the strength of your password.

IMO better to tunnel VNC over ssh or better still ssh -X

If you are on a windows box, install Xming as an X server.

---


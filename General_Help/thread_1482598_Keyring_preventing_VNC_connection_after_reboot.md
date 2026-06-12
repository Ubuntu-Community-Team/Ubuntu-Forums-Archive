---
title: "Keyring preventing VNC connection after reboot"
date: 2010-05-13
forum: General Help
---

### Post by zipdog on 2010-05-13
I have a headless Jaunty server that I need to access from both mac and PC clients. If the server has been rebooted, I can SSH into it, but I can not VNC into it unless I unlock the keychain. The problem is that I can't figure out how to unlock the keychain from SSH connections, so the only available method is to attach a keyboard to the physical box and enter the keychain password at the server itself.

Is there a Terminal command that I can use to unlock the keychain? I have seen references to the 'security' command but that appears to be unavailable to Jaunty?

Is there an even better method than a Terminal command? I don't want to be putting passwords into the Terminal log if I can help it. Ideally, I would connect via SSH, confirm the keychain somehow, and tunnel in through VNC.

I've seen posts about this elsewhere, but none of them contain solutions.

---

### Post by Mistrblank on 2010-05-18
I'm also having the same problem after a fresh install of 10.04.  

I've enabled remote desktop and when I attempt to connect via the client system, the remote system has the keychain request pop up.

---

### Post by 1dirtypanda on 2010-05-24
i'm having this problem too. does anybody know how to turn this "feature" off?

---

### Post by tbresson on 2010-05-26
I'm having this problem aswell.

I thought it might be related to autologon which I have but I havn't testet it. Found this thread afterwards.
[http://ubuntuforums.org/showthread.php?t=1466519&highlight=vnc+unlock+keyring](http://ubuntuforums.org/showthread.php?t=1466519&highlight=vnc+unlock+keyring)

It kinda sucks you have to make your server less secure just to be able to remote it.

---

### Post by tbresson on 2010-05-29
[http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/](http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/)

---

### Post by Freaky#Funga on 2010-12-12
You could also try this workaround.
[http://ubuntuforums.org/showpost.php?p=10229123&postcount=6]("http://ubuntuforums.org/showpost.php?p=10229123&postcount=6")

---

### Post by gigaferz on 2011-03-08
this thing works.
should mark it as solved

---


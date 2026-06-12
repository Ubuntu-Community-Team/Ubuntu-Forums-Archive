---
title: "Don't use auto login option"
date: 2010-05-16
forum: General Help
---

### Post by gwm on 2010-05-16
Ubuntu install offers the option of automatically logging one in at startup.

If you choose this option, you are logged in automatically. However, you are still asked for your password, to unlock your keyring. So all you have done, is saved yourself one click (or one key press of the enter-key).

The downside, is that there is no delay of your automatically started programs that maybe wait for you to log in. These can start using improperly initialized resources - like the keyring, I suppose.

In my case, this has resulted in the sound system failing. Restart then resulted in the sound being restored but the Trash folder going missing and so on. Finally, the Quit button on the task bar vanished forever.

Perhaps I have identified the cause incorrectly, but that is my assessment and therefore I recommend not to use this login option.

I am running 10.4 Gnome 64 bit. The program I started automatically, was Evolution.

---

### Post by techunit on 2010-05-16
This is not correct and kind of inaccurate. There is away around this and I have used it before. When you are asked for the keyring password enter your normal password. Then the next time you are asked for it click options the check the automatically enter or something of that nature if this doesn't work then I will track down it for you using google...

---

### Post by blueridgedog on 2010-05-16
This should make the key ring stop asking for a password if that is your intent:

[https://help.ubuntu.com/9.10/internet/C/faq-keyring.html](https://help.ubuntu.com/9.10/internet/C/faq-keyring.html)

---

### Post by aske on 2010-05-16
> **blueridgedog said:**
> This should make the key ring stop asking for a password if that is your intent:

[https://help.ubuntu.com/9.10/internet/C/faq-keyring.html](https://help.ubuntu.com/9.10/internet/C/faq-keyring.html)
uuuhm for me the "available to all users" was ticked by default (ubuntu 10.04) and still keyring asks me for a password..
but i don't think i have seen any problems with anything.. unless this is what is causing my amarok to stop playing sound sometimes (something about the devices is the notification i get)..

---

### Post by techunit on 2010-05-16
Oh yeah I had that problem but I seem to remember fixing it some how.

---

### Post by gwm on 2010-11-09
Hi,
I revisited this issue recently with a new installation of Maverick (10.10). I believe it has now been resolved.
The thread is:

[http://ubuntuforums.org/showthread.php?t=1613930](http://ubuntuforums.org/showthread.php?t=1613930)

---


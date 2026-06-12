---
title: "3CX IP PBX in Windows 7 virtual machine"
date: 2010-11-03
forum: General Help
---

### Post by Jonners59 on 2010-11-03
I have been using 3CX on Vista for 2 years now. I recently upgraded my PC to run Ubuntu 10.4. I installed Sun's VirtualBox and set up a virtual machine within which I run Windows 7. I then installed the latest version of 3CX in this virtual machine/Windows7 environment and used the back up config to setup the new 3CX system. It works great, but for one thing.... When voice mail messages are left by callers, it does not seem to exist. The message is not in the users account, and is not sent by eMail as a wav file as it used to.

Where could they be?
What could be causing this?
How do I fix, please any help??????

---

### Post by Jonners59 on 2010-11-07
[FONT="Arial"][SIZE="3"]OK, this turned out to be not an Ubuntu matter, not surprisingly.  But in case anyone else does the same, here is the solution:

- Check whether you've actually enabled recording on your new installation on your extension's settings.
- Check Settings > General > Global options > Recording Path and set it a location of your liking.
- Check Settings > General > Mail Server and see whether the settings you have entered there are correct.

 I resolved the saving messages... It would seem that, and logically the path to save the files disappeared. The field was blank, and after so long since I set things up, I forgot it was there. And what was great, all the messages we had missed were there too!

Sending via eMail. That was not so good though.

I use gMail, So the server is smtp.gmail.com
Username is the eMail address and corresponding password. However it uses TLS encryption, which 3CX does not currently support though it does have the capability.  Maybe next release.

Therefore to make it work, I had to use the smtp of my ISP. Not as tidy, but it worked.[/SIZE][/FONT]

---


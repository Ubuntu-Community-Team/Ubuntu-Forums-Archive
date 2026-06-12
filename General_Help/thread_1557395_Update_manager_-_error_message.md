---
title: "Update manager - error message"
date: 2010-08-20
forum: General Help
---

### Post by JohnBUK on 2010-08-20
As a newbie I am trying to learn more about Ubuntu.
A new problem has occurred which doesn't seem to cause my laptop to misfunction but I do not understand the issue or how to put it right.

I have Ubuntu Lucid running on a Dell Inspiron 1545 and every time I run the Update Manager the following message pops up:

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

I currently run Virtualbox OSE as I need to use Net Objects Fusion to manage two websites. That runs OK despite this message.

Can anyone help me deal with this issue please.
Thank you

---

### Post by snowpine on 2010-08-20
I think you may have skipped a step when [installing VirtualBox]("http://www.virtualbox.org/wiki/Linux_Downloads"): 

> The Oracle public key for apt-secure can be downloaded here. You can add this key with 

wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -

---

### Post by JohnBUK on 2010-08-20
snowpine - many thanks for that. Tried to enter via Terminal and got the following:

gpg: no valid OpenPGP data found.

John

---

### Post by snowpine on 2010-08-20
Silly forums, they put a ... in my URL!

Click here and scroll down a bit for the actual link:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by JohnBUK on 2010-08-20
snowpine thanks again. I'm having a problemgetting the Terminal to accept my password - I enter the message you suggest and I am prompted for the password - at that point the Terminal does not react to any of my keystrokes!! 
Another thing occurs to me - I have the "free" version of Virtualbox OSE installed and this is the "non-free". Is that right?

JB

---

### Post by snowpine on 2010-08-20
> **JohnBUK said:**
> snowpine thanks again. I'm having a problemgetting the Terminal to accept my password - I enter the message you suggest and I am prompted for the password - at that point the Terminal does not react to any of my keystrokes!! 
Another thing occurs to me - I have the "free" version of Virtualbox OSE installed and this is the "non-free". Is that right?

JB

The terminal will not show your password while you're typing it, just type and press Enter and you should be OK. :)

It's true that virtualbox-ose is in the Ubuntu repository, so I'm not 100% sure why you have virtualbox.org in your sources list... just trying to help you with the error message...

---

### Post by JohnBUK on 2010-08-21
Snowpine, many thanks again for your reply. Now you mention it I seem to recall reading an article stating the VBox had been updated and I then tried to update it without realising they were NOT talking about the OSE version. I suspect therefore this is left-over as it were from that error.
Certainly my OSE version works fine.
I have Ubuntu Tweak and presumably can remove any mention of the ordinary version so this error message does not pop up again? I hesitate to bother you again but can you - or anyone else - direct me how to expunge this for ever! 
I'm very grateful for your help etc.
John B

---

### Post by snowpine on 2010-08-21
If you want to remove the repository from your sources, there are two ways:

1) System, Administration, Software Sources

or

2) Edit the text file /etc/apt/sources.list with your favorite text editor, delete the line referencing to virtualbox.org. (If you don't find it there, check for a virtualbox file in the folder /etc/apt/sources.list.d)

---

### Post by JohnBUK on 2010-08-21
snowpine - Thank you so much! I did exactly as you said on the "sources.list" file, found the entry for the "non-free" Virtualbox, removed it and now the Update Manager works fine without errors.

Many, many thanks once again. I am gradually improving my knowledge of this excellent OS and maybe one day I will be able to help someone similarly.
regards
JohnB

---


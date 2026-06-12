---
title: "Setting up samba"
date: 2010-08-06
forum: General Help
---

### Post by safee1248 on 2010-08-06
can someone direct me on how to set up Samba?

---

### Post by crokett on 2010-08-06
[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by Morbius1 on 2010-08-06
Sure,

Open Nautilus ( your Home folder )

Right click on say ... Documents
Select "Sharing Options"
[COLOR=Blue]*At this point if you don't have samba installed it will ask you if you want to install it - you do.*[/COLOR]

Select "Share this folder", "allow others to create and delete..", and "Guest Access"
Select "Create Share"
[COLOR=Blue]*It will now ask you if you want it to modify permissions - you do*[/COLOR]

You have just installed samba and created a samba public share.

Go to the other machines on your network and see if they can find the "documents" folder

---

### Post by pricetech on 2010-08-06
System - Administration - Synaptic Package Manager.

Search for "system-config-samba", without the quotes.  Installing that will give you Samba and the GUI configuration tool.  Once installed; System - Administration - Samba will bring up the the GUI tool.  It's all pretty intuitive from there.

Have fun.

---

### Post by Morbius1 on 2010-08-07
I feel obligated to note that there are 2 completely different ways to create samba shares.

The method I described using Nautilus directly is called Nautilus-shares ( Samba calls it "usershares" ). It will create share definitions at [COLOR=Blue]/var/lib/samba/usershares[/COLOR].

The method pricetech described is called Classic-shares and it's shares are defined at [COLOR=Blue]/etc/samba/smb.conf[/COLOR].

I would recommend that you choose one method or the other since using both at the same time especially on the same target folder will result in unexpected behavior. And if you run into trouble always describe what method you're using in your post. A surprising number of people in this forum don't know about Nautilus-share even though it's been part of samba for years.

---

### Post by egalvan on 2010-08-07
An excellent source of "how-to's"

[http://ubuntu.swerdna.org/](http://ubuntu.swerdna.org/)


Here is his "simplified" one...

[http://ubuntu.swerdna.org/ubulanprimer.html](http://ubuntu.swerdna.org/ubulanprimer.html)


Note, these look really complicated, but I printed two out, and used a highlighter to mark the relevant stuff.
it boils down pretty well...
I DO recommend reading the whole thing BEFORE starting, as you sometimes have choices to make...

As Morbius1 points out, "classic shares" and "nautilus shares" are one VERY IMPORTANT choice.

---

### Post by Morbius1 on 2010-08-07
The difference between the two methods really comes down to how much control you want to have over the share.

Both methods can create a public share accessible to everyone. Both methods can create a share that requires a username and password to access. But Nautilus-share can't create a protected share accessible by one remote user with proper credentials and not accessible to another with proper credentials. Only Classic-share can do that. In fact you can set up a classic share that is accessible by only one user using only one specific machine on the network.

I would argue that for the average home user Nautilus-share is the easier path especially for a new linux user since the share creation process resembles the way you create a simple share on Windows.

---


---
title: "Virtual box Ubuntu 10.04 mouse problem"
date: 2010-05-24
forum: General Help
---

### Post by DJ . on 2010-05-24
I am running windows 7 with virtualbox and ubuntu 10.04 as the guestos and the mouse  used to work, but now it doesn't. I don't have guest additions and i  can't get it because i can't log in. Virtual box says the mouse is  captured but it isn't working. How do i fix this? I have the latest version of virtualbox.

---

### Post by DJ . on 2010-05-27
Anybody?

---

### Post by lmarmisa on 2010-05-27
Please, check the two VirtualBox icons on the right side.

How are they?.

Do you see any change on them after pressing the right Control key?.

I attach a copy of these icons to this post.

Best regards,

Luis

P.S. there is a specific forum for Virtualization.

---

### Post by lmarmisa on 2010-05-27
You can install the VirtualBox GuestAdditions without the use of the mouse following these instructions:

1) Start your guest system.

2) Select Devices -> Install Guest Additions in the VB window.

3) Open a text screen (for example tty1) typing Alt + Ctrl F1 (use the left Control key).

4) Log-in your account.

5) Type these commands depending if your Ubuntu system is 32 or 64 bits :[B] 

# Case of 32 bits guest Ubuntu operating system

cd /media/cdrom[/B]
**sudo ./VBoxLinuxAdditions-x86.run**
[B]
# Case of 64 bits guest Ubuntu operating system
  
cd /media/cdrom[/B]
**sudo ./VBoxLinuxAdditions-amd64.run**

Restart the system:

**sudo reboot**

Best regards,

Luis

---

### Post by geet89 on 2010-05-27
just install virtual box again

---

### Post by DJ . on 2010-05-28
> **lmarmisa said:**
> You can install the VirtualBox GuestAdditions without the use of the mouse following these instructions:

1) Start your guest system.

2) Select Devices -> Install Guest Additions in the VB window.

3) Open a text screen (for example tty1) typing Alt + Ctrl F1 (use the left Control key).

4) Log-in your account.

5) Type these commands depending if your Ubuntu system is 32 or 64 bits :[B] 

# Case of 32 bits guest Ubuntu operating system

cd /media/cdrom[/B]
**sudo ./VBoxLinuxAdditions-x86.run**
[B]
# Case of 64 bits guest Ubuntu operating system
  
cd /media/cdrom[/B]
**sudo ./VBoxLinuxAdditions-amd64.run**

Restart the system:

**sudo reboot**

Best regards,

Luis
Keyboard won't work either.

---

### Post by DJ . on 2010-06-05
anybody have any ideas?

---

### Post by DJ . on 2010-07-02
still not working...

---

### Post by DJ . on 2010-07-19
upgraded to the next vbox, didn't help.

---

### Post by Mike_IronFist on 2010-07-19
> **DJ . said:**
> I am running windows 7 with virtualbox and ubuntu 10.04 as the guestos and the mouse  used to work, but now it doesn't. I don't have guest additions and i  can't get it because i can't log in. Virtual box says the mouse is  captured but it isn't working. How do i fix this? I have the latest version of virtualbox.

You can use the keyboard to navigate around, using the tab key to cycle through the various on-screen buttons. It sucks, I know, but it usually works.

If that doesn't work for you, you could always completely uninstall virtualbox, and then re-install it, or re-install Ubuntu on Virtualbox. Your call.

---


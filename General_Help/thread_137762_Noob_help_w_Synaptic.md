---
title: "Noob help w/ Synaptic"
date: 2006-02-28
forum: General Help
---

### Post by sledge367 on 2006-02-28
I am just getting started w/ Linux and heard how awesome Ubuntu was so gave it a shot. I have successfully now dual-booted XP and U5.1 but am running into two issues:
1) As soon as I startup I get a window that tells me I have 34 updates to install. When I click on that it asks for my password which I give it and then nothing happens. Nada. If I put in the wrong pw it tells me but if I put in the right password nothing happens at all other than the pw prompt going away.

2) When I try and load the Synaptic Package Manager I get a similar action. When I give it my pw nothing happens. If I have already tried to do the updates thing it then won't even ask for a pw for Synaptic and vice-versa.

Any ideas? I am sure I am probably just missing something stupid but I do need help. I have even gone so far as to reinstall and choose a different kernel from the installation options (I still don't know which one to properly choose anyway - i386, i386 image, 12.... option) but still no joy.

I appreciate any and all helps someone can offer.

Sledge367

---

### Post by souled on 2006-02-28
Try running ```
sudo apt-get upgrade
``` This command will update your updatable packages. Synaptic is the frontend to apt. Not sure as to why your Synaptic doesn't work, but you can update and install stuff from the command line. If you want to install programs, use ```
sudo apt-get install (package)
```

---

### Post by kayakrob on 2006-02-28
I am having the exact same problem. It seems that the user I created doesn't have priv to perform ANY admin type functions. All the apps that are already installed (openoffice, games etc..) work fine.

Rob

---

### Post by sledge367 on 2006-02-28
Those commands would be entered in the terminal window, right? When I do it asks for a password (which doesn't get shown at all or even *s in its place) and then nothing happens again. Any ideas?

Any ideas how to get Synaptic to work? Being so new to this, the command line is a tougher start for me (not quite as used to it as working in all the dos commands, etc).

Also, which Kernel is the right one to pick?

Thank you again for anything anyone can do to help a new convert.

Sledge367

---

### Post by souled on 2006-02-28
Those commands go into the Terminal, correct. When you type in your password, nothing will show up. Nothing shows up for security reasons. I honestly can't help you with your Synaptic problem. I was just trying to give you an alternative to installing/removing/upgrading packages since you can't do it via Synaptic.

Try running Synaptic from terminal. type in ```
sudo synaptic
``` Type in your password. Copy and paste any errors that output in the terminal. This is a way to discover why your programs won't run. Running the program through the terminal will tell you of problems.

---

### Post by ronmarley1 on 2006-02-28
sledge367,
Are you connected to the Internet?

---

### Post by sledge367 on 2006-02-28
Yes, I can access the internet just fine through Firefox. 
All of the installed Ubuntu applications work fine (Openoffice., Evolution, etc) but I can't do the update, Synaptic, User and Groups, nothing else. Whatever one I choose first when I start up the system, it asks for a password and then the clock comes on for a short time and then nothing happens.

Any ideas?

---

### Post by sledge367 on 2006-02-28
Yes, I can access the internet just fine through Firefox. 
All of the installed Ubuntu applications work fine (Openoffice., Evolution, etc) but I can't do the update, Synaptic, User and Groups, nothing else. Whatever one I choose first when I start up the system, it asks for a password and then the clock comes on for a short time and then nothing happens.

Any ideas?

---

### Post by Bachstelze on 2006-02-28
What are you typing when prompted for a password ?

---

### Post by sledge367 on 2006-03-01
I have tried several things. If I use my user pw then the input box goes away and then nothing happens ever. If I try and do it again or another application it does nothing, not even ask for a pw.

If I try and use the root pw it goes away and then comes back in 3 seconds saying incorrect pw.

Anybody have any ideas?

---

### Post by amosbatto on 2006-03-01
Your caps lock key isn't on?  That one always gets me.

If you installed in expert mode, did you create a root password? When I created a root password, normal sudo stopped working for me.  You might need to edit your sudoers file to get your normal username password to work again. 

    $ su
    # nano /etc/sudoers

Give your normal user root priveleges by adding this line to the bottom of the sudoers file:

    your-user-name   ALL=(ALL) ALL

---


---
title: "can't access home folder ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by giovannisarto on 2011-10-15
Hi everyone,
today I installed ubuntu 11.10 64 bit. Until today I've been using Fedora 15 64 bit with gnome shell. I have separated partition for the system and for the data. So what I did was just format the system partition. Now when i attempt to login with my username this message pops up "Could not update ICEauthority file /home/gio/.ICEauthority". I don't even know what this file is. I tried to boot in recovery mode as root and it says this file doesn't exist and it doesn't see the home folder...what can I do? I hope I've been clear enough, any help appreciated! Thanks in advance, 

Giovanni

---

### Post by orange2k on 2011-10-15
Did you encrypt your home folder maybe?

---

### Post by giovannisarto on 2011-10-15
no I didn't! Maybe it's a permissions problem, but I can't figure out how to change them!

---

### Post by kopiwe on 2011-10-15
I suppose you have the same username you used to have under Fedora. In this case I suggest you rename your old user folder and let ubuntu set a new, clean one. This avoids conflicts with various configuration data. 

Rename your old user folder (/home/username) from the live-cd.

open terminal and go to your home folder after you mounted your home partition.

```
cd /media/yourharddrive/home

```rename your old user folder to username-old (or whatever you like)

```
sudo mv username username-old
```at restart ubuntu makes a new user folder with new config files.

Now you can copy the relevant documents into your new folder.


Edit: Ups, didnt know that, thanks Lars

---

### Post by Lars Noodén on 2011-10-15
If it's a permissions issue, you'll need to make sure that both accounts on the two systems are using the same UID.  It's the number, not the name, that counts.  You can see what UID your home directory with [font=Courier New]ls[/font]

```

ls -n ~

```

You can see what UID your user has using [font=Courier New]grep[/font]

```

grep $USER /etc/passwd

```

If the UID in [font=Courier New]/etc/passwd[/font] does not match the one in the directory, then that will have to be changed using [usermod](http://manpages.ubuntu.com/manpages/oneiric/en/man8/usermod.8.html)

---

### Post by giovannisarto on 2011-10-15
Thank you very much! Ubuntu forums rocks!! I managed to change the permissions by running gksunautilus!

---


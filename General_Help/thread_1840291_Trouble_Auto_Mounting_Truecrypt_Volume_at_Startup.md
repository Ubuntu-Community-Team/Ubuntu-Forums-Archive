---
title: "Trouble Auto Mounting Truecrypt Volume at Startup"
date: 2011-09-07
forum: General Help
---

### Post by reapermedia on 2011-09-07
Hi there!

I'm a new user to the forums, although I frequently browse here for answers to problems that I have. Unfortunately I have not been able to find a solution that works for me for this particular problem anywhere on the web. I'm quite a novice when it comes to ubuntu, it isnt even my main os yet, although hopefully, after sorting out this problem, I will be one step closer to almost exclusively using ubuntu!

I have a dual boot system via grub2, which boots my truecrypt encrypted windows 7 installation (using a truecrypt recovery iso), and my LVM 2 encrypted ubuntu 11.04 installation. I also have a primary partition on the same drive which is a truecrypt volume and holds all my documents. this partition is auto mounted at boot time with my windows 7 installation perfectly fine. However I want to achieve the same thing with my ubuntu installation.

Both installations and the documents volume use the same passphrase. Ideally, the ultimate solution would be for truecrypt to grab the passphrase I type in at boot time to decrypt the lvm partition and use that to decrypt the documents partition, although i know this is a tough call.

So basically I've been thinking like this, it would be ok to store a command in this form:
```

truecrypt --force -p "passphrase" /dev/sda4 /media/Documents

```
to auto mount the volume at startup, as this file will only be accessible after decryption anyway.

But i've tried multiple solutions to try and get this command to run at startup and nothing works!!! >.< This command needs root privileges, to mount the volume, and it works fine whenever run under sudo in the terminal.

I've tried adding the command to /etc/rc.local with and without /usr/bin/ preceding the command. And I've got nowhere. running 
```

$ sudo /etc/rc.local start

```
or
```

$ sudo /etc/init.d/rc.local start

```
mounts the volume no problem, but for some reason it doesn't work automatically.

Any help would be very much appreciated!
Cheers! :-)

---

### Post by reapermedia on 2011-09-08
Bump, Anyone? :(

---

### Post by Swashy on 2011-09-08
I too need to put an automatic start-up code into rc.local but I'm not sure how to go about it. Perhaps you aren't putting the code in that file correctly?
I tried searching around about the rc.local file but there doesn't seem to be much about it.
Do you know what the "exit 0" code exactly does and how I should arrange it in relation to the code I want to inject? How should the code be put in the file? Should it start with $?

Sorry I'm not much help for your problem..

edit: according to[ this thread]("http://ubuntuforums.org/showthread.php?t=1840549&highlight=rc.local") it goes before the phrase "exit 0" and with no $ sign. I'll try putting it in there with sudo and seeing what shenanigans happens...

edit2: It worked for me upon startup! Sudo seems to translate through gui as a keyring pop-up.

You didn't put a $ in there did you? I'm not sure if it would make a difference but its worth it trying.

---

### Post by reapermedia on 2011-09-09
> **Swashy said:**
> I too need to put an automatic start-up code into rc.local but I'm not sure how to go about it. Perhaps you aren't putting the code in that file correctly?
I tried searching around about the rc.local file but there doesn't seem to be much about it.
Do you know what the "exit 0" code exactly does and how I should arrange it in relation to the code I want to inject? How should the code be put in the file? Should it start with $?

Sorry I'm not much help for your problem..

edit: according to[ this thread]("http://ubuntuforums.org/showthread.php?t=1840549&highlight=rc.local") it goes before the phrase "exit 0" and with no $ sign. I'll try putting it in there with sudo and seeing what shenanigans happens...

edit2: It worked for me upon startup! Sudo seems to translate through gui as a keyring pop-up.

You didn't put a $ in there did you? I'm not sure if it would make a difference but its worth it trying.

Yup, that's what I did, to no avail!

---


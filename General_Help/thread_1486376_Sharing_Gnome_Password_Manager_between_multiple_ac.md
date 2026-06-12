---
title: "Sharing Gnome Password Manager between multiple accounts"
date: 2010-05-17
forum: General Help
---

### Post by HyperFlexed on 2010-05-17
Hi, I use gnome password manager. It stores encrypted passwords in the ~/.gpass directory.

I have 2 users, johnny, and audio. My default gpass setup is at /home/johnny/.gpass

I've created a group called gpassusers and added johnny and audio.

I chgrp'd /home/johnny/.gpass to gpassusers.
I chmod'd /home/johnny/.gpass 770 (to give group access)

I then created a symlink as follows

```
ln -s /home/johnny/.gpass /home/audio/.gpass
```

when I try to cd into /home/audio/.gpass I get

```
audio@picard:~$ cd .gpass
bash: cd: .gpass: Permission denied
```

for sanity's sake, here's the ls of johnny's home directory
```
drwxrwx---  2 johnny gpassusers   4096 2010-05-17 19:34 .gpass
```

and here's the ls of audio's home directory
```
lrwxrwxrwx  1 audio audio    19 2010-05-17 19:34 .gpass -> /home/johnny/.gpass
```

and just to verify groups are set up properly
```
audio@picard:~$ groups audio
audio : audio adm dialout fax cdrom floppy tape dip video plugdev fuse admin gpassusers
audio@picard:~$ groups johnny
johnny : johnny adm dialout cdrom audio plugdev lpadmin admin sambashare gpassusers
```

what gives?

---

### Post by lizzard on 2010-05-17
The problem seems to be that you can't change into the audio-homedirectory as user "johnny", because it's owned by audio:audio. So you can't change into /home/audio/.gpass either.

---

### Post by HyperFlexed on 2010-05-17
> **lizzard said:**
> The problem seems to be that you can't change into the audio-homedirectory as user "johnny", because it's owned by audio:audio. So you can't change into /home/audio/.gpass either.

I can't change into /home/audio/ as johnny, but that's not my issue.

I want audio to be able to change into /home/audio/.gpass which is a symlink to /home/johnny/.gpass.

/home/johnny/.gpass is chmod'd to 770 owned by johnny:gpassusers

shouldn't this allow access to audio who is in gpassusers?

Or is there an issue because /home/johnny is owned by johnny:johnny? (which is a level below /home/johnny/.gpass)

I have a feeling this should be possible, but if anyone can explain a reason why it wouldn't be, I'm all ears. I've created the audio account because my sound applications don't play nice with Compiz. I still need access to the passwords in gpass though. If I just duplicate the .gpass folder they won't synchronize.

I suppose I could set up a cron job under root to synchronize them every so often, but that's a bit of a hack. (and the last cron job I tried to make didn't work, even though it was showing up in the logs :P)

---

### Post by lizzard on 2010-05-17
Damned, I didn't read your post carefully enough.
Try 
```
chown audio:gpassuser /home/audio/.gpass
```
to set the group after you set the symlink, as it's still audio:audio.

---

### Post by HyperFlexed on 2010-05-17
> **lizzard said:**
> Damned, I didn't read your post carefully enough.
Try 
```
chown -R audio:gpassuser /home/audio/.gpass
```
to set the group after you set the symlink, as it's still audio:audio.

```
audio@picard:~$ chown -R audio:gpassusers /home/audio/.gpass
audio@picard:~$ ls -al
...
lrwxrwxrwx  1 audio gpassusers    19 2010-05-17 19:34 .gpass -> /home/johnny/.gpass
...
audio@picard:~$ cd .gpass
bash: cd: .gpass: Permission denied

```

---

### Post by lizzard on 2010-05-17
I think it's a problem with user rights in home directories. A quick and dirty solution could be to create a seperate gpass-directory in /home with rights set to 770 and then symlink from johnny to this direktory. And afterwards from gpass-directory to audio.
```
sudo mkdir /home/gpass
sudo chmod 770 /home/gpass
sudo :gpassuser /home/gpass
sudo ln -s /home/johnny/.gpass /home/gpass
sudo ln -s /home/gpass/.gpass /home/audio/.gpass
```

---


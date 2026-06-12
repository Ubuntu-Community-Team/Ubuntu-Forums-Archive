---
title: "Pulseaudio Problem"
date: 2012-01-26
forum: General Help
---

### Post by awmian on 2012-01-26
I am having a unique problem. My system can't seem to locate pulse audio
```
asad@asad-laptop:~$ pulseaudio
The program 'pulseaudio' is currently not installed.  You can install it by typing:
sudo apt-get install pulseaudio

```

but when I try to install it I get
```
asad@asad-laptop:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  apport-hooks-medibuntu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.

```

Can anyone explain what's going on?

---

### Post by satanselbow on 2012-01-26
You have not provided any details of what lead up to this? 
Do you have any sound at the moment?

A quick fix might be to purge pulse and then reinstall:

```
sudo apt-get update
sudo apt-get purge pulseaudio
sudo apt-get install pulseaudio
```

---

### Post by awmian on 2012-01-26
> **satanselbow said:**
> You have not provided any details of what lead up to this? 
Do you have any sound at the moment?

A quick fix might be to purge pulse and then reinstall:

```
sudo apt-get update
sudo apt-get purge pulseaudio
sudo apt-get install pulseaudio
```

I tried to switch to ALSA. I don't know whether I removed pulseaudio from my system or did something else. But ever since that the vol control applet vanished and also the vol wheel stopped working on my notebook although I still was getting sound. Btw I'm using lucid.

So I thought I would reinstall pulse.

so doing what you told me seems to have taken care of the initial problem
```
asad@asad-laptop:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

but I'm still not sure whether I'm on pulse or ALSA. Also the vol wheel still is not controlling the sound vol

---


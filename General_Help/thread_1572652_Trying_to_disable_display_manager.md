---
title: "Trying to disable display manager"
date: 2010-09-11
forum: General Help
---

### Post by zigmo on 2010-09-11
I setup an Ubuntu Server and everything was fine.
I then accidentally installed gnome and found I had to switch terminal sessions to get a console everytime, so I decided to try to remove gnome.
First, I tried

```
update-rc.d -f gdm remove
```
but it still booted into gnome. Next, I tried 

```
sudo apt-get remove gdm
```
but now, it boots into

```
Ubuntu is running in low graphics mode
Your screen, graphics card and input device settings could not be detected correctly.
You will need to configure these yourself.

OK

What would you like to do?

O Run Ubuntu in low-graphics mode for just one session
O Reconfigure graphics
O Troubleshoot this error
O Exit to console login
O Restart X
```
I can Exit to console, but that is hardly a long term solution.
How can I remove gnoem entirely so I don't have to worry about this again (or have the memory overhead of it running).
Thanks for any suggestions.

---

### Post by Sin@Sin-Sacrifice on 2010-09-11
sudo apt-get purge ubuntu-desktop

---

### Post by zigmo on 2010-09-11
I don't have that as an option. I have:

```
ubuntu-artwork         ubuntu-mono            ubuntu-system-service
ubuntu-docs            ubuntu-serverguide     ubuntu-virt-server
ubuntu-keyring         ubuntu-sounds          ubuntu-wallpapers
ubuntu-minimal         ubuntu-standard
```

Which should I purge?

---

### Post by zigmo on 2010-09-12
I didn't have ubuntu-desktop, so I tried to purge gnome-desktop-environment. It still didn't work, so I reinstalled gnome-desktop-environment. At least now, it boots directly into gnome, with no errors.
I just want to disable the GUI completely: I don't mind if I have to remove it if I have to. It doesn't even appear to be enabled in rcconf (which I think just checks the various rc directories for startup scripts), so I don't get why it's even running.

Edit:
Hmmmm ... I think I might be running upstart - that might explain things.

---


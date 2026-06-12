---
title: "Open emacs with ssh"
date: 2011-06-30
forum: General Help
---

### Post by peggs on 2011-06-30
Hi!

I am using emacs at work, and when I am home I use ssh through the terminal to connect to my computer at work. However starting emacs through ssh only gives me emacs in the terminal. As it is a bit awkward to work with I would like to open the GUI version of emacs through ssh. I tried installing tramp, but that did not seem to have any effect....:(

---

### Post by tcsmith1978 on 2011-06-30
Do you use SCP to access your files?

---

### Post by peggs on 2011-06-30
I thought scp was to copy files over a ssh connection? That is not what I am trying to accomplish. I want to open a file on the remote server using either the GUI for emacs on my local computer or the GUI for emacs on the remote server. I also tried using the flag -X, i.e. ssh -X username@servername and it works for gedit(but very unstable and slow!) and for emacs it opens a blank window and freezes..

---

### Post by seawolf167 on 2011-06-30
Are you on a windows or *nix-based OS at work? 

For a *nix based system, you can open Emacs via

```
ssh -X -C -c blowfish -l* username* -p *port ip.address.of.machine*
```

Then open Emacs like normal

```
emacs&
```

A windows system is a little more complex, let me know if this is the case and I'll give you more info.

---

### Post by peggs on 2011-06-30
It's a linux based system at work as well. With your suggestion the same happends. It seems to be working ok, but when I open emacs it just opens a blank window and then freezes.

---

### Post by seawolf167 on 2011-06-30
How long do you wait before killing the window? I know emacs takes a little while to open up, and you are limited by your upstream bandwidth at your house and your downstream bandwidth at work.

Can you try running something simple like

```
xclock
```or

```
xterm
```and see if they load?

---

### Post by peggs on 2011-06-30
ok, emacs actually opens now, I just have to wait for some minutes. So I'll guess it's a problem with the bandwidth. Thanks !

---

### Post by seawolf167 on 2011-06-30
No problem - the bottle neck here is almost certainty your up speed bandwidth at your house. If you get a higher up load rate it'll be able to transfer the information faster. 

Glad it is working though :)

---


---
title: "Trying to find a command"
date: 2010-12-05
forum: General Help
---

### Post by cwosengir on 2010-12-05
Hi, I recently installed Ubuntu on my other pc and I used the alternative version.  Half way through the installation I did get an error but I skipped past a few parts and when I rebooted my computer without the cd I arrive at a login where I would type my username and pass.  After that I'm logged in but I'm still at this command line, but I remember taking a operating system class way back and there was a special command to load up the gui when I faced this similar screen but idk what that command is or what I could do to get to the gui, any help most appreciated thanks!

---

### Post by amauk on 2010-12-05
startx

---

### Post by sikander3786 on 2010-12-05
Welcome to the forums :-)

I don't think if you get errors during the install process and you can skip them :confused:

Can you reproduce that error here? If there were errors/error, it might not be a good install.

startx has evolved to this I think.

```
sudo service gdm start
```

---

### Post by cwosengir on 2010-12-05
> **sikander3786 said:**
> Welcome to the forums :-)

I don't think if you get errors during the install process and you can skip them :confused:

Can you reproduce that error here? If there were errors/error, it might not be a good install.

startx has evolved to this I think.

```
sudo service gdm start
```

yea its the strangest thing, every installation of any linux distribution that I've tried gets an error or freezes.  Only tried free version of fedora, and 2 different versions of ubuntu, including the alternative downloads, but some part of the installation failed and I dont know the exact error since i can only hook up 1 computer at a time but i was able to get to a list and skip over that part of the failed installation... and it told me to reboot when the cd ejected and i arrived at this command line which never popped before.  i'll keep everyone posted and thanks for everything.

---


---
title: "Firefox, Bash, and System Monitor freeze simultaneously"
date: 2010-02-10
forum: General Help
---

### Post by Potters Son on 2010-02-10
Hello, all

I have been having a freaky experience where Firefox appears to freeze up and brings down the terminal and any process viewer with it. For example, I can open a gnome-terminal or xterm window, but the moment I press a key, that window freezes up as well and must be force-quitted with the Force Quit panel applet. In addition, the System Monitor applet I have on my top panel freezes. It's really weird.

I began having this problem around a month or two ago. I thought it was something to do with something I installed, so a week or so ago I did a clean install, backing up my documents, Firefox profile, and GNOME settings from the old installation but wiping everything else (I'd already ruled out the Firefox profile by renaming the folder and creating a new one from the profile manager). Yet the problem persists.

I'd be happy to post any output, but as bash (including Ctrl+Alt+F1 command line) freezes as well, it's a little hard to treat the problem when it happens.

One more thing: I am on a university campus which uses 802.1x encryption on both wired and wireless connections; is it possible that that is causing the crashes?

---

### Post by Richard1979 on 2010-02-10
Try doing a "ls -lha" on your home directory, in "~/.mozilla" and "/tmp" (or / to see the permissions on /tmp).
If the ones in your home directory say anything other than USERNAME:GROUP (usually same as username) then try doing this:

```

cd ~
sudo chown USERNAME:USERNAME * -R

```

---


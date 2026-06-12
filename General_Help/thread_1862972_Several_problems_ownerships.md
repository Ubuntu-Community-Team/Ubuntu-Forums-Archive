---
title: "Several problems: ownerships?"
date: 2011-10-17
forum: General Help
---

### Post by canhoto on 2011-10-17
Hi.

I've been having several problems. My Firefox began to crash all the time. I choosed to uninstall it by deleting all Firefox-related folders and files, including (at least that's waht I thought) the profile ones. For that, I needed to change their ownership. I ended up changing the ownership of the / directory (stupidly, I know now), and I began having lots of problems. First, I wasn't able to run sudo commands or to open Synaptic.  After some research in these forums, I managed to change teh ownership (to root) of the implied files and folders, using a live CD. Now I can run sudo and synaptic. But I have several problems:

1. I reinstalled Firefox with Synaptic and - guess what - my bookmarks, extensions, etc. were still there and... it's still crashing.
2. Sound doesn't work, the sound controls do nothing, the sound preferences say they are waiting for the soun system to answer, and nothing happens
3. The network manager doesn't appear in the panel and doesn't connect to the wireless networks. I installed Wicd (and it's working).
4. The Ubuntu Software Center does nothing when I click "install" on whatever the application I want to install
5. When I log out or shut down, I get messages like "could not update UCEauthority file /var/lib/gdm/.ICEauthority
6. When the screen locks and I try to unlock, it gives me authentication failure. I don't enter a wrong password, I'm sure.

And that's all :-)

Any help?

---

### Post by blueridgedog on 2011-10-17
Are all of these hardware issues new after the permission problem?

I suggest a re-install (with a partition format) as the cleanest way to get your system working.

To remove your firefox profile, you can delete the folder:

~/.mozilla

Such as 

```
rm -rf ~/.mozilla
```

You can also verify if it is a profile or plug in issue by running firefox in safe mode:

```
firefox -safe-mode
```

---


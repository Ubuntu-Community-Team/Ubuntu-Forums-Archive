---
title: "Can't Access Trash, Computer, or Network Locations"
date: 2009-07-11
forum: General Help
---

### Post by deathblossom on 2009-07-11
Somehow my gnome-panel got screwed up (well, I was trying to re-build it to change something and it didn't go as planned...) and in the process of trying to fix it, I ended up not being able to access these places. I tried to fix it by doing a clean install of Jaunty. While this fixed my gnome-panel, I still have these other problems (maybe related to settings from a separate home partition, not sure, really):

1. Clicking on the Trash Icon in the side bar or on the panel does not display the trash folder and will result in my desktop icons disappearing. If I click on any other folder, then my desktop icons will reappear. I can access the Trash folder from my .local/share/Trash folder, but clicking on the actual Trash icon doesn't work.

2. I experience the same issues when clicking on the Computer icon or the Network icon.

3. This extends to trying to ssh into devices. It will ssh, but when I try to pull up the folder to explore the device, the window will crash back to my icon-less desktop.

It sounds like the system is trying to access locations that do not exist anymore or got moved, but I have no idea how to change those.

**ETA**: Apparently, this is a problem with Ubuntu One. Uninstalling it fixed these issues. Apparently there is an upgrade that fixes this issue, I may check it out later.

---


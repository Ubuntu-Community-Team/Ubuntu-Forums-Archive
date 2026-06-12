---
title: "ld.so.preload is restricting webcam usage in Karmic"
date: 2009-11-06
forum: General Help
---

### Post by trpnblies7 on 2009-11-06
Since updating to Karmic, my webcam has only worked under root privileges, i.e., if I open gstreamer-properties normally and try to test my device, I get a permission denied, but if I sudo gstreamer-properties, it works fine.

I've finally figured out that the problem is the file **etc/ld.so.preload**. When I was using Jaunty, in order for my webcam to work with flash applications/websites like tinychat.com, I needed to add the line **/usr/lib/libv4l/v4l1compat.so** to the ld.so.preload file because flash applications still don't work with v4l2. In Karmic, though, something has changed.

If ld.so.preload is blank, and I add the above line to it during my session, everything is fine and I'm able to switch to v4l1 in gstreamer-properties so that flash applications will work. However, once I logout or restart my computer, I once again can only access my webcam as root.

Does anyone know why ld.so.preload is having this effect? Any idea how to fix it? This never happened in Jaunty; I was able to restart my computer without any issues.

A very tedious solution would be to clear the file every time I shut down my computer and then add the line back in once I turn it on again, but I'm hoping there's a more sensible way to go about this.

Any help would be greatly appreciated.

---

### Post by trpnblies7 on 2009-11-06
Any ideas?

---

### Post by trpnblies7 on 2009-11-06
bump?

---


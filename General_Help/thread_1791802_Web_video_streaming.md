---
title: "Web video streaming"
date: 2011-06-27
forum: General Help
---

### Post by db579 on 2011-06-27
I'm using Ubuntu 11.04 Natty Narwhal on a Dell Studio XPS 16 Laptop. Watching video files of any kind locally works fine with movie player or VLC but streaming video off the web barely works at all.

The video quickly becomes very laggy and the frame/refresh rate seems to drop right down as if the laptop was under extreme load. Watching full screen isn't really possible. I've tested this in Chromium and Firefox so it's not a browser issue.

My graphics card is ATI Mobility Radeon HD 4670 and the CPU is an Intel i7 Q820 so it shouldn't really be underpowered.

Anyone have a fix?

---

### Post by FormatSeize on 2011-06-27
Have you installed Flash Player? In my experience, Flash Player alone wouldn't play everything, so I also instll SWF Player, also from the Adobe website.

---

### Post by lovinglinux on 2011-06-27
If you referring to sites like YouTube, then is a flash issue. Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues. If you still get that issue after running Flash-Aid, then click the extension "Help" menu, then "Generate Report". Attach the contents of the *firefox-report.txt* file saved in your Desktop, so I can analyse your situation.

---

### Post by db579 on 2011-06-27
Hi, thanks very much for the flash aid tip, I ran that and it seems to have solved the problem.

---

### Post by lovinglinux on 2011-06-27
> **db579 said:**
> Hi, thanks very much for the flash aid tip, I ran that and it seems to have solved the problem.

You are welcome.

---


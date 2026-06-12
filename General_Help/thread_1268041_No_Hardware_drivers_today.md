---
title: "No Hardware drivers today?"
date: 2009-09-16
forum: General Help
---

### Post by NoaHall on 2009-09-16
I was setting up a client's computer, with the same graphics card as several others I've set up. It's a fresh install, but there's one problem - when I go to hardware drivers, there's nothing there. Of course, I could use envy ng, but I'd rather not install anything else. I've tried to install the driver through the command line, but it still says there's no graphics card enabled. Any ideas?

Problem solved - updated kernel, then installed via apt-get, then reboot. After that, shows up in Hardware Drivers.

---

### Post by P4man on 2009-09-17
ive seen hardware drivers take some time to work for unknown reasons. Sometimes it takes a reboot before it will prompt to install restricted drivers, without even installing or updating anything. I figure its load balancing the nvidia ftp site or something :p

---


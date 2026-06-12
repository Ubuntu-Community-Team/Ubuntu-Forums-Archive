---
title: "debs not getting imported by apt-cacher-ng"
date: 2010-08-31
forum: General Help
---

### Post by JedMeister on 2010-08-31
I have used apt-cacher successfully for a long time on my home LAN. Its been great but after a recent server crash I decided to switch to apt-cacher-ng due to reports of lower memory footprint and faster response. Thats all well and good and after just a little mucking around it seems to be working.

But there are a few old (but still current) debs that I am having trouble importing into the apt-cacher-ng cache. Most of them were picked up after adding all the repos to my client and running apt-get update. But there are still a few that aren't. (the 2 biggest ones are from the same repo). My client machine runs apt-get update without fault but when I import (using the apt-cacher-ng web interface) it lists all the repos (including the one these debs should be in) but isn't importing any more of the debs. There are no errors showing.

I'm not sure what to do next. Any ideas?

---

### Post by JedMeister on 2010-09-04
Ok guess not. I need to get on with a project I'm working on so I guess I'll just redownload them.

---


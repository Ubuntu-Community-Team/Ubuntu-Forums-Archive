---
title: "Chromium Updates"
date: 2011-04-14
forum: General Help
---

### Post by Entyrion on 2011-04-14
Hello everyone, 

I recently installed Ubuntu on my laptop and I'm enjoying it so far. Staying true to my new open source theme, I've decided to switch from using Chrome to using Chromium instead. However, there was one question that has had me stumped. I've received two different answers to this question in the past, so I'm looking for a definitive answer.

My one and only reservation about Chromium is that I have read that it will not auto-update; I will have to periodically update to newer versions of Chromium myself. I've asked about this previously on these forums, but I have not received a response, so any clarification would be greatly appreciated. Here are the two things I've been told so far:

1. Repositories for stable versions of Chromium are automatically set when I installed Chromium in Ubuntu, therefore Ubuntu will notify me when periodic stable updates are available.

OR:

2. Chromium will NOT update unless I manually add the stable PPA from somewhere like [https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable)

While I was very thankful for the help volunteered by these two posters, as you can see these two answers are contradictory; either Chromium will be auto-updated via Ubuntu as stable updates are available OR I will need to set it up myself.

Allow me to say that I am new to Linux and Ubuntu and I am not interested in Chromium testing or development; I am only interested in stable updates that add functionality or bug fixes, etc designed for the average Joe web surfer. I have no interest in the bleeding edge development updates or dealing with bugs, etc. I just want to make sure Chromium will stay reasonably up to date over time.

So guys, can anyone give me a definitive answer? Which is it? Will Ubuntu take care of it on its own (I did install Chromium via the Ubuntu Software Center), or will I need to set up the DIY manual update system?

If I will need to set this up myself, could anyone offer noob-friendly directions for doing so?

Thank you very much in advance!

---

### Post by cottfcfan on 2011-04-14
I'd use the "stable ppa" anyway.
Open up synaptic package manager, go to repositories, click the 3rd party software, then add, and paste in:
ppa:chromium-daily/stable
then close & reload.
Chromium will now update automatically to the latest stable version.

---

### Post by Entyrion on 2011-04-14
Just the straightforward and noob-friendly answer I was looking for! Thank you! Marking as solved.

---


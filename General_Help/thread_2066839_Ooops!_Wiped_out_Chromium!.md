---
title: "Ooops! Wiped out Chromium!"
date: 2012-10-05
forum: General Help
---

### Post by pottzie on 2012-10-05
I'm using Lubuntu 12.04, and in a futile attempt to get flash working, tried to install Chromium 22 over the version that Lubuntu ships with. 

 Followed the guide at [http://modifyubuntu.com/#programs](http://modifyubuntu.com/#programs)  and when I tried to ad the ppa, I got this warning:

"You are about to add the following PPA to your system:
 *** ABORT MISSION ***

Don’t use this PPA to get the latest Chromium. This is not an official channel. Lobby Ubuntu devs to reinstate the daily builds instead.

I’m patching this build with my personal preferences for keybindings since that’s the only way to change them (e.g., Ctrl-N &#8594; New Tab, Alt-1 &#8594; Previous Tab, Alt-2 &#8594; Next Tab, Alt-3 &#8594; Close Tab).

This PPA is dangerous. Don’t enable it. Look at the name. It was chosen on purpose.
 More info: [https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)
Press [ENTER] to continue or ctrl-c to cancel adding it"

 So of course I pressed "enter." The guide says to upgrade using apt-get upgrade, so I did that too. Now when I click on Chromium using either the icon in the package tray or the icon from the pop up menu, Chromium doesn't open. And Chromium is the only browser that plays ANY video, even though there are some (a lot!) of videos that Chromium couldn't play. I installed Google Chrome, Opera, and Firefox trying to get video working so I can watch any video, but nothing except Chromium would play any video. Firefox shows flash player installed under about;plugins, but no video, just a blank white space.

 What can I do to either get Chromium as it was, or maybe better install the newer Chromium? And I've seen several press releases about Google Chrome beta 23, with better video support being released. Can I get that?

 After I tried to get the ppa installed, I got this message.
"Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 99, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 132, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 322, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 141, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer"

 Probably doesn't make things any better

---

### Post by vasa1 on 2012-10-05
> **pottzie said:**
> .... Lobby Ubuntu devs to reinstate the daily builds instead...
They're on the look out for volunteers because it's quite a laborious task.

---

### Post by pottzie on 2012-10-05
Wonder what's involved in doing that?

---

### Post by marinara on 2012-10-06
how to get back to old chromium: go to synaptic and remove the ppa from your repos.  then remove chromium, then update and install chromium

---


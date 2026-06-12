---
title: "How to Manually Update Chromium"
date: 2011-04-08
forum: General Help
---

### Post by Entyrion on 2011-04-08
Hello everyone!

I recently converted my old laptop to Ubuntu a couple days ago and I'm loving it! This is my first post, but I've been reading the Ubuntu forums which have been helpful for tweaking little things and I'd say I've graduated from "absolute" Ubuntu/Linux noob to "almost total" noob in the last couple days (at least I know what the terminal is now!). On my regular PC, I'm a big fan of the Google Chrome browser, but for my Ubuntu machine, I was hoping to stay as true to the open source theme as possible, so while I do have Chrome installed too, I'd love to use Chromium as my primary browser.

The one drawback for me with Chromium vs. Chrome is that there are not automatic updates, but I wasn't able to find a clear, noob-friendly walk-through to set up a means to regularly update Chromium manually (either using the terminal or using the GUI). From what I understand, it would involve finding and installing Chromium build repositories, then checking and updating from those periodically.

The problem is that I don't really know how to go about doing any of this. How exactly does one add repositories? After they're added, how does one update from the Chromium builds located there? Are there any Chromium repositories for relatively stable builds versus the uber-newest test builds?

Am I completely off track and there's an easier way to set up a means to update Chromium?

Any help you guys can offer would be great, thanks in advance!

---

### Post by tredegar on 2011-04-08
The repositories are set for your installed version (9.10, 10.04, 10.10, whatever).

You will be informed when there are updates available for your version.

If you wish to use the latest and greatest, then you might have to compile from source code. Awkward, but not impossible. Might drive you mad though.

My advice: Just use it as it is, and accept the updates as they come along.

Enjoy.

---

### Post by Frogs Hair on 2011-04-08
Hi and Welcome

Google the Chromium PPA for your version of Ubuntu , but know that there are different ones available. I see from a quick search there a daily build , beta channel , and stable PPA.

The daily build updates almost daily and is for development and testing and may break . I would suggest a stable PPA , witch will update less and provide proven updates.

---

### Post by Entyrion on 2011-04-08
Thank you so much for your quick reply! Let me confirm what you said though, because based on what I've read in other forums about Chromium, I'm a bit confused >.<

Has an automatic updating system for Chromium (the open source project, not the official Google Chrome browser) been added to Ubuntu since those older forum posts? If the repositories come stock as part of my Ubuntu 10.10 install and I will be automatically notified of new Chromium updates, is that not essentially an auto-update system?

If that is the case, I'm all set (and very excited that such a feature has been added!), since I have neither the expertise nor the inclination to compile the uber-newest source code myself.

Again, thank you so much for your clarification. I apologize if I'm being dense, but I just wanted to make sure you were saying what I thought you were saying :)

---

### Post by Entyrion on 2011-04-08
@Frogs Hair: It looks like we were cross-posting; my initial response was to tredegar.

I found a Google Chromium Stable channel at [https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable) ...will I need to add that PPA to my system in order to get stable updates to Chromium? Or will they be included in periodic updates in the Ubuntu Update Manager like tredgar seemed to imply.

Like I said, I'm a total noob, so I apologize if my confusion is frustrating :(

---

### Post by Entyrion on 2011-04-12
I apologize if I'm being dense, but because I received 2 different responses to my question (1. don't worry, Chromium will update itself, and 2. go get the PPAs online), I'm a bit confused. Can someone please clear this up for me?

Will Ubuntu periodically update Chromium on its own, or do I need to go out and start adding repositories and whatnot manually? (I don't need cutting edge updates, but I do want to make sure that I'm periodically getting stable updates to my Chromium browser).

Thanks!

---

### Post by Entyrion on 2011-04-14
I posted another thread along these lines because nobody was answering my more recent requests for clarification. Below is the answer I received on that other thread:

"I'd use the "stable ppa" anyway.
Open up synaptic package manager, go to repositories, click the 3rd party software, then add, and paste in:
ppa:chromium-daily/stable
then close & reload.
Chromium will now update automatically to the latest stable version."

Thanks to "cottfcfan" for responding on that other thread. I followed his instructions and this issue is resolved. Marking this thread as solved.

---


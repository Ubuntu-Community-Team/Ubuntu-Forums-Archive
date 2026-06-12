---
title: "speaker+headphones issue"
date: 2010-04-30
forum: General Help
---

### Post by _0R10N on 2010-04-30
When I installed Karmic I had some sound issues. First I didn't have sound at all. After I managed to get sound working, I realized that when connecting headphones, the sound kept coming from the speakers, as well. Someone help me out, and I fixed that last problem.

Now, last night I upgraded to Lynx and guess what?? The problem was back again.

I fixed this problem again. And here is what I've done to get it working properly:
When the upgrade process was taking place, I saw that the alsa package for backports would be deleted. Then, I installed the appropriate version for Lucid. Rebooted and nothing changed... Then I started to walk through the options under System->Preferences->Sound. And I found on the "Output" tab, that Connector was set to "Analog Speakers", I changed it to "Analog Output". That did the trick!.

Now, I'm wondering if I really needed to install the backports package... if you go through this same problem, please, I ask you to try changing the Connector value on the Sound window, first. Let me know if it worked...

Kind regards!

---


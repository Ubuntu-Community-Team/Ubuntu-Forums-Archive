---
title: "Disable or reconfigure workspace switcher?"
date: 2012-07-22
forum: General Help
---

### Post by Jay MC on 2012-07-22
Hi guys,

Wonder if anyone had any thoughts on this.

I've never been a fan of workspaces.  I'm guess some people must like them, but I'd rather use the launcher (or equivalent in other OSes) to manage the different apps that I'm using in a single workspace.  Minimise/maximise is my way of moving from task to task.  I guess this is because my tasks use multiple combinations of apps (where each is shaking hands with all the others, so to speak, in various combinations) rather than discrete groups of them, that can be separated out.

Normally, the presence of different workspaces is a complete non-issue, because I don't use them.  However, GIMP has a glitch.  Sometimes, when I maximise it, one of the floating toolbars "jumps" to the workspace below the main one.  So the only time I ever use the workspace switcher is to retrieve my stray toolbar and drag it back to the main screen, where it can be reunited with the rest of GIMP.  This is a minor annoyance. 

I don't know whether any other apps have this glitch, but if they do, I can imagine it causes new users a lot of confusion.  The first few times it happened, I thought a load of apps and half of GIMP had closed - I didn't realise I'd switched workspace - and just logged out/in again to fix the problem.

So, my question is:

- Can I disable workspaces entirely?
- If not, can I reconfigure them? - e.g., make four horizontal workspaces, rather than a 2x2 square?

On a related note, if anyone benefits from workspaces, I'd really like to hear how - simply because I don't have any use cases that are helped by them, and I'd be interested to hear how they help other users.

---

### Post by GreatDanton on 2012-07-22
I don't believe it's possible to change the alignment of the workspaces, however if you want to have 4 workspaces in one column you could install Gnome shell. Keep in mind that Gnome shell it's different than unity so maybe you won't like it.

Maybe you should take a look at this site: [http://www.tuxgarage.com/2011/09/ubuntu-oneiric-gui-options.html](http://www.tuxgarage.com/2011/09/ubuntu-oneiric-gui-options.html)

One workaround to your problem is to set Unity bar to Auto hide, so it will not cover your Gimp.

---

### Post by Jay MC on 2012-07-22
Thanks for the reply, GreatDanton.  That's a shame, but only a minor one  :)

---

### Post by sikander3786 on 2012-07-23
> **Jay MC said:**
> So, my question is:

- Can I disable workspaces entirely?
- If not, can I reconfigure them? - e.g., make four horizontal workspaces, rather than a 2x2 square?

On a related note, if anyone benefits from workspaces, I'd really like to hear how - simply because I don't have any use cases that are helped by them, and I'd be interested to hear how they help other users.

Yes, the workspaces can be disabled and they can also be reconfigured. You would need a tool like CCSM or Ubuntu-Tweak for tweaking these options. Ubuntu-Tweak is the safer option so I'll recommend it over CCSM.

For installing Ubuntu-Tweak, get to a Terminal and run these commands, one-by-one:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```

Once installed, open the Dash and search for 'Ubuntu Tweak' and open it. In the main Ubuntu Tweak window, click 'Tweaks' button near the top-center and in the next frame, choose 'Workspace' under 'Desktop' heading.

This is where you would be adjusting the number of your horizontal and vertical workspaces. If you want 4 horizontal workspaces, adjust the 'Horizontal workspace' slider to 4 and the 'Vertical workspace' to 1. If you want to turn of workspaces, choose 1 for both of those.

For me, I benefit from the workspaces by placing different application windows at different workspaces, like many others do. Browser is running at one, chat window at the other, media player at the third, VirtualBox at the fourth and so on. For easy switching, I have set the left-bottom edge of my screen to 'Show Workspaces' when the pointer hits there as illustrated in the screenshot below.

Hope it helps.

---


---
title: "Double Click Launcher Removed?"
date: 2012-06-03
forum: General Help
---

### Post by JosephBeck on 2012-06-03
Before you used to be able to double click the icon in the launcher on the left side to bring up all windows of that program. It was incredibly useful and far better than alt+tab. I reinstalled Ubuntu 12.04 thinking it was a glitch and somehow I got it back, but now it went away again. Is it a bug that I cant use the launcher to switch between windows of the same program or is it on purpose? If so it is a really poor idea and if anyone has a way to bring it back please share, or at least tell me how I can change it to a more comfortable key setting because typing AltTab is rather awkward for me.

---

### Post by stinkeye on 2012-06-03
In **ccsm > window management**, check the scale plugin is enabled.

Still doesn't work, check you are in the **Ubuntu** session and not the **Ubuntu 2d** session.
Terminal...
```
echo $DESKTOP_SESSION
```

---

### Post by JosephBeck on 2012-06-04
> **stinkeye said:**
> In **ccsm > window management**, check the scale plugin is enabled.

Still doesn't work, check you are in the **Ubuntu** session and not the **Ubuntu 2d** session.
Terminal...
```
echo $DESKTOP_SESSION
```

I am in Ubuntu standard (3D) and the scale plugin is enabled. It was working perfectly after the refresh until it stopped working as I was customizing Ubuntu. I dont want to have to reinstall it again to get it to work. Is there anything inside the scale plugin I should be looking for? I didnt install anything that would mess it up.

---

### Post by stinkeye on 2012-06-04
By double click, do you mean a click to focus and then a click to spread windows of that app?

In the terminal, run...
```
unity --reset & disown
```
You will lose any ccsm customizing you have done.

---

### Post by JosephBeck on 2012-06-04
> **stinkeye said:**
> By double click, do you mean a click to focus and then a click to spread windows of that app?

In the terminal, run...
```
unity --reset & disown
```
You will lose any ccsm customizing you have done.

Thank you so much! Its back and perfect. Something must have gotten messed with when my Cog menu disappeared and I returned it. It worked perfectly now.

---

### Post by stinkeye on 2012-06-04
When you have ccsm set up how you like, use the preferences 
to export your profile.
Save as **myccsm.profile**
Then when needed you can import the saved profile.

---

### Post by JosephBeck on 2012-06-05
> **stinkeye said:**
> When you have ccsm set up how you like, use the preferences 
to export your profile.
Save as **myccsm.profile**
Then when needed you can import the saved profile.

Sadly the problem came back x-x. Idk why so I will have to investigate but I will do that so thank you. Apparently when you make it so you only have 1 desktop instead of the default 4 view it disables to ability to double click the launcher and spread the windows. You have to have at least 2 work spaces in one category be it vertical or horizontal.

---

### Post by stinkeye on 2012-06-05
Yes, the same here for 1 workspace.
I use two workspaces with the cube because I like the flip effect when changing which I bind to my mouse side button.
Don't you find an extra workspace useful?

You could set a corner to scale all windows as in pic.

---

### Post by JosephBeck on 2012-06-05
> **stinkeye said:**
> Yes, the same here for 1 workspace.
I use two workspaces with the cube because I like the flip effect when changing which I bind to my mouse side button.
Don't you find an extra workspace useful?

I don't mind it really but if I could go without the workspace button I would. I guess I just have to live with there being a workspace button on my launcher because i double click a lot so its more useful than removing an annoying icon. I wish I knew why it did that or that it would be repaired to not work that way.

---


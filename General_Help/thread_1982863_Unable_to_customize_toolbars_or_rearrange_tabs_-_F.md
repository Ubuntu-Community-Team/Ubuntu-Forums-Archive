---
title: "Unable to customize toolbars or rearrange tabs - Firefox 12"
date: 2012-05-19
forum: General Help
---

### Post by robbiemacg on 2012-05-19
Having recently upgraded to Firefox 12 (as part of the upgrade to Precise), I now find myself unable to customize toolbars, rearrange tabs, drag tabs into bookmark folders. That's a lot of lost functionality.

I discovered the issue when trying to remove the Flash-aid button from my toolbar. I figured, no more flash updates for FF, might as well reclaim some real estate. No dice. I can open the dialogue to customize toolbars (View > Toolbars > Customize), but I can't manipulate items form the menu or in my toolbar.
Likewise, I just discovered that I've lost the ability to drag tabs into bookmark folders.

I've searched the forums, and I can't find a clear case of others experiencing these/similar issues. Can anyone suggest a fix or point me in the right direction to find some info?

Thanks,
Robbie

---

### Post by Vaphell on 2012-05-19
does the guest account have similar problem?
what happens if you rename your .mozilla dir so firefox recreates a fresh config?

---

### Post by robbiemacg on 2012-05-19
I've just logged in as a guest; sure enough I can rearrange tabs, etc. Your intuition is good.
I might try as you've suggested and force FF to create a new .directory, but I'm wary of losing my add-ons, bookmarks, etc. I'll back that stuff up and give it a shot, though, baring a non-'Turn it off and then back on again' solution.
Thanks very much for the helpful advice, of course.

---

### Post by lovinglinux on 2012-05-19
First make a backup of ~/.mozilla folder, just in case you don't like the changes proposed here.

Then, right-click on the toolbar, select "Customize", then click "Restore Default Set" button. This should take care of not being able to move toolbars and icons. It will reset all buttons and you will need to redo any customization.

Close Firefox locate your profile folder under ~/.mozilla/firefox, then rename the file *places.sqlite*. Open Firefox, then go to the bookmark manager (CTRL+SHIFT+O) and restore a backup using the "Import and Backup" button. This should take care of issues with bookmarks. However, there is a bug in the global menu integration that prevents users from performing some actions with bookmarks. So I would test if you can perform those actions, like dragging a tab to the bookmark tree, using the sidebar bookmarks.

---

### Post by robbiemacg on 2012-05-19
[[COLOR=#DD4814]**lovinglinux**[/COLOR]]("http://ubuntuforums.org/member.php?u=649167")! I'll do as you've suggested. You are the the Firefox/Flash/ETC champ. Thanks for your time, and for offering a through explanation.

---

### Post by robbiemacg on 2012-05-22
Having applied the solution proposed above, I found I was still encountering the issue.
I got a little scientific, took a look at my Add Ons, and discovered that a bug related to the TorButton Extension was causing all the trouble. ([https://trac.torproject.org/projects/tor/ticket/1392](https://trac.torproject.org/projects/tor/ticket/1392))

---

### Post by SloppyNick on 2012-08-27
Thanks for the solution, robbiemacg. I had a similar problem with my toolbar not being customizable. Turns out the culprit was the Global Menu Bar Integration addon (which integrates Firefox with Unity). Since I had reverted from Unity back to Gnome, this apparently was a problem. I disabled the addon, and that solved the problem.

Hope this helps others with the same issue!

---


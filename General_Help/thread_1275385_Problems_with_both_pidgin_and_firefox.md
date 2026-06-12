---
title: "Problems with both pidgin and firefox"
date: 2009-09-25
forum: General Help
---

### Post by Oaney on 2009-09-25
I am new to linux, but am somewhat familiar with unix through my mac... I broke Ubuntu though... can anyone help?

Problems
*Pidgin wont load. It opens for half a second, then looks like it minimizes but closes completely.
*Firefox does not allow back and forward navigation. The back button is greyed out, I right click and the back option is greyed out. Backspace doesnt move me backwards, and ctrl-[ and ctrl-] dont work either...

This is a fairly new installation of 9.04, about two weeks old. Pidgin and firefox were working fine for the first week, and then I was trying to change the appearance options when it happened. I had to do a hard reset, and when i logged back in, pidgin wouldnt work. Firefox stopped allowing navigation after I tried fixing pidgin by deleting the .purple directory in the home folder...

Can anyone lend me any advice?

---

### Post by c0mput3r_n3rD on 2009-09-25
For Pidgin: When you open pidgin it moves to the top tray (where the time & date is) next to the sound icon and internet icon. ( the icon will look like a letter in 9.04, and either a green dot or a clock in 8.10).

For firefox: Do a
```

sudo apt-get upgrade

```If that doesn't fix the issue do a:
```

sudo apt-get reinstall firefox

```

---

### Post by mac9416 on 2009-09-25
As far as Firefox goes, try running:
```
$ firefox -safe-mode
```

If everything works, then a setting or plugin is causing the problem. I suggest disabling plugins one at a time until back/forward works again. If that does not work, reset all your settings permanently with safe mode.

Some great info: [http://support.mozilla.com/en-US/kb/Basic+Troubleshooting#Troubleshoot_plugins](http://support.mozilla.com/en-US/kb/Basic+Troubleshooting#Troubleshoot_plugins)

Good luck

---

### Post by lovinglinux on 2009-09-25
Reinstalling Firefox or starting it in safe-mode probably won't help.

Instead, see **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

### Post by Oaney on 2009-09-25
Pidgin didnt move up there. Its not open anywhere. I read another forum where someone was having similar issues, and the advice was to go to the home folder hit ctrl+h to show hidden, find the .purple directory and delete it, then restart pidgin.

I did this, and pidgin did load. It asked to set up an account, and I went through the process entering my aim information, clicked ok and it just sat there, it didnt connect. I closed it and tried to open it again and I had to go through the same account process. I tried several more times and each time it doesnt save the account info that i entered.

I will try those suggestions with firefox soon

---

### Post by Oaney on 2009-09-26
I went through that firefox troubleshooting thread and found the solution to my exact problems, no back and forward buttons, no browsing history, etc. I followed the instructions there and it didnt do anything. It just creates roughly 40 places.something.corrupt folders in the directory instead but still wont navigate or save history.

Regarding pidgin, I deleted the .purple folder in the home directory on advice from another post, and now It asks me to add an account each time. When i add my aim info it loads the buddy list, but no buddies, and the accounts window freezes and becomes unresponsive. It asks me to force quit, but when i do it closes pidgin completely. Upon restarting pidgin i need to go through the same account process...

---

### Post by lovinglinux on 2009-09-26
> **Oaney said:**
> I went through that firefox troubleshooting thread and found the solution to my exact problems, no back and forward buttons, no browsing history, etc. I followed the instructions there and it didnt do anything. It just creates roughly 40 places.something.corrupt folders in the directory instead but still wont navigate or save history.

You have to close Firefox before deleting any files on your profile. The solution is the correct one according to your problem description.

---

### Post by Oaney on 2009-09-26
Ok, i got firefox working. But instead of just deleting that file, I deleted the entire profile... ie

home/.mozilla/firefox/####### where ######## are the random letters assigned to the profile.

Now the only problem I have is the pidgin issue. Is there a simple way to reinstall, or rebuild pidgin like it was from the original installation of ubuntu? Ill keep searching for pidgin repair on the internet, but Ill also ask here in case anyone knows of a simple solution.

Thanks a bunch for the firefox info!

---

### Post by Oaney on 2009-09-26
I solved the pidgin issue by going to the synaptic package manager, finding pidgin, and marking it for upgrade (along with all supporting files.) My buddy list is loaded, and everything seems to be going smoothly with both applications that were giving me trouble.

Thanks everybody!

---


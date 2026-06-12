---
title: "Disable Automatic Saving of Firefox Tabs on Logout/Shutdown"
date: 2009-07-11
forum: General Help
---

### Post by LucasHenderson on 2009-07-11
I Googled around a fair amount, and dug through various settings before posting this, so forgive me if this has already been asked.
Here's what happens:
I have Firefox open with a number of tabs, and/or windows. Without closing Firefox, I logout of(or shutdown) Ubuntu(which automatically closes Firefox). I then log back in, and click the Firefox icon. It opens up with the tabs and windows I had open when I previously logged out. This is in contrast to when Firefox crashes or is killed forcefully, as it will prompt me whether or not I want to restore the previous tabs/windows. It is also different from when I manually close Firefox with multiple tabs open, as it gives me an option of saving the tabs.

Put simply, when I logout of Ubuntu while Firefox is open, it automatically acts as though the "Save and Quit" option has been chosen. I have verified that this is the default behavior on a clean install of Ubuntu, and not the result anything settings I have changed.

What I would like to do, is have it, on logout/shutdown, act as though the "Quit" option had been chosen.

---

### Post by yeaitsdark on 2009-07-11
Try this:
[http://ubuntuforums.org/showthread.php?t=736908](http://ubuntuforums.org/showthread.php?t=736908)
Or this:
[http://www.mydigitallife.info/2008/06/19/disable-firefox-3-auto-save-tabs-on-close-to-prompt-for-choice/](http://www.mydigitallife.info/2008/06/19/disable-firefox-3-auto-save-tabs-on-close-to-prompt-for-choice/)

Hope that helps.

---

### Post by LucasHenderson on 2009-07-11
> **yeaitsdark said:**
> Try this:
[http://ubuntuforums.org/showthread.php?t=736908](http://ubuntuforums.org/showthread.php?t=736908)
Or this:
[http://www.mydigitallife.info/2008/06/19/disable-firefox-3-auto-save-tabs-on-close-to-prompt-for-choice/](http://www.mydigitallife.info/2008/06/19/disable-firefox-3-auto-save-tabs-on-close-to-prompt-for-choice/)

Hope that helps.

Sorry, it did not. Under preferences, "When Firefox starts:" is already set to "Show my Home Page", on both my regular computer, and the clean install on a spare computer.

To clarify, I'm wanting to change what is apparently a default behavior of Ubuntu.

---

### Post by yeaitsdark on 2009-07-11
All right. I just underwent the process to be in your position.

I have resolved it by doing the following. In a new tab, open the address
```
about:config
```
Accept "I'll be careful I promise"

We will change 3 values here. There is a filter bar to make this easy.

First type, "warnon". Double click these two lines line to make them say TRUE. (If already True, leave them)
```
browser.tabs.warnOnClose: true
```
```
browser.warnOnQuit: true
```

Second, clear the filter and type: startup.page. Change this value to 1.
```
browser.startup.page: 1
```

---

### Post by LucasHenderson on 2009-07-11
[IMG]http://img21.imageshack.us/img21/6332/screenshot7jlz.png[/IMG]
[IMG]http://img249.imageshack.us/img249/4043/screenshot6r.png[/IMG]
[IMG]http://img25.imageshack.us/img25/6226/screenshot5mgc.png[/IMG]

Thanks, but I just checked(and double-checked) about:config; the preferences you mentioned are all already set set to their default values, the ones you posted.

Here's the steps to replicate the behavior I'm speaking of:
1. Login to Ubuntu.
2. Open Firefox.
3. Open a few tabs. For testing, I used Google, Yahoo, and MSN.
4. Go to the upper-right corner of the screen, where it has your name, drag down the menu, and choose "Log Out".
5. Login to Ubuntu.
6. Open Firefox.
7. Observe as Firefox opens with the same tabs from before, in this case, Google, Yahoo, and MSN.

---

### Post by yeaitsdark on 2009-07-11
Humm... I will do more research. For details, which version of Ubuntu are you using? Which version of Firefox are you using?

(Help > About)

Mine is 3.0.11

Also, just a guess - try setting the ```
browser.startup.page: 1
``` to 2 (3 was what was forcing the save on close, hence 1 was working for me but the site suggested 1 or 2). 

Also, close Firefox after this change, and it *should* prompt you to "Quit/Save and Close/Cancel". You would chose "Quit" and if the check mark is checked, this would become the new default action.

Instead of logging out of your user account, simply close and re-open only Firefox. (File > Exit). Logging out completely vs closing the application will often cause the new values not to come into play because it has a sort of safety switch for crashes.

I believe that has something to do with it. In the mean time I'll look into it more, I'm only surprised because I just tested that and it worked rather nicely.

However, I was playing around setting the options to "false" then closing Firefox. Then setting them back to "true", which MAY have had something to do with "resetting" the values in some way. (I doubt this but worth a shot ya?)

Try these things, and then yea get back to me. In the meantime however I will do more searching.

---

### Post by LucasHenderson on 2009-07-12
I'm having no problem when closing firefox regularly. It's always prompted me then, just as it should. I wasn't logging out because of any changes I've made. I was logging out because the problem I'm talking about only occurs when I'm logging out. Follow the steps I provided earlier, and you'll see what I mean.

Rather than continue trying to explain myself. I made a video explaining exactly what I'm talking about.
[http://www.youtube.com/watch?v=AGu_tZFUjKw](http://www.youtube.com/watch?v=AGu_tZFUjKw) (You may have to turn your volume up a bunch to hear the audio, sorry)

---

### Post by yeaitsdark on 2009-07-13
I watched the video. I do understand what you mean. Simply exiting the Firefox application does not exhibit the same behavior as logging out?

To be honest I'm quite unsure how to proceed with this one. Perhaps deleting the data for Firefox in your /home folder may remove some persistent setting that is causing this trouble.

You could accomplish this by issue this command. **Do note that this would be all of your personal data associated with your Firefox profile. Bookmarks, cookies etc.**
```
rm -rfd .mozilla/firefox/
```

It's all I can really think of, sorry I can't be of more help to you.

---

### Post by LucasHenderson on 2009-07-13
There are no persistent settings. What you saw in the video was a *clean install*. Prior to me launching firefox in the video, there was *no profile*.
It might not even be a setting on Firefox that's causing this. It's some Ubuntu feature, which, when you log out, automatically saves the Firefox tabs that are currently open.
If I log out of Ubuntu, it saves my tabs, regardless of the settings on Firefox.
I'm tired of turning on my computer, logging in, starting firefox, and seeing every web page I had open when I last logged out. I've been using Ubuntu and other Linux distros for years. I know many of the ins and outs of Linux. This is just a simple feature that has come to annoy me over the past few months.

Anyway. I solved the problem, sort of. Not so much solved as circumvented. I couldn't figure out a way to disable the automatic saving while retaining manual saving, which was my original goal, so I just added the following to /etc/gdm/PostSession/Default:
rm /home/lucas/.mozilla/firefox/[profile folder]/sessionstore.js
So, basically, if the session save is present on logout, it gets rid of it. The only downside is if I actually want it to save my tabs prior to logging out, then too bad. This is better than just disabling session saving entirely, as at least I will be able to save manually...so long as I don't log out.

---

### Post by Andy06 on 2009-07-13
Your solution may have more to do with session restore feature than with browser start up pages and warning dialog boxes. In about:config, type "session" into filter and change this value:

browser.sessionstore.resume_from_crash to false.
See if that helps.

---

### Post by LucasHenderson on 2009-07-13
I believe I already tried that, too. It used to be an issue, that when you logged out of Ubuntu, firefox treated it as a crash/kill, and next time you started it up, it would say.."Your last Firefox session closed unexpectedly..." and so on. That issue was fixed in the last release or so(but replaced by the feature which I wish to disable). 

Changing that key you mentioned would make it so it never resumes from crashes, which isn't really satisfactory either.

---

### Post by CatKiller on 2009-07-13
I suspect that logging out sends a kill signal to Firefox, like a normal close would, but then there is no input to confirm whether to save the session or not, so Firefox does so,  just to be on the safe side. Since you've already killed the ability to save the session by your "circumvention," I would be tempted to remove your rm line and instead disable the save session dialogue. That way, when you **do** want to save your session you still can, by selecting the "windows and tabs from last time" option. And when you don't, you'll have your normal clean setting, even when you log off without closing Firefox.

---


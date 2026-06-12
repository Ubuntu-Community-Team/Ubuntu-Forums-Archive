---
title: "System Back Up"
date: 2012-04-26
forum: General Help
---

### Post by gennatolls on 2012-04-26
Is there a way to back up my full filesystem? I would like to use Deja Dup with its automated backup. I was running 11.10 ( I know I should stick with a LTS for this computer) on my primary desktop which I use as a file server to backup all the other computers in my house to as well as stream all my movies from it. One of the latest updates messed up my system. I lost the Ambiance theme in Firefox, thunderbird, and any open or save as dialog box for any program. I also lost the ability to control my music with the media keys on my keyboard which I have used on other installs back to 9.10 without issue. I have alot of apps installed that are not in the Software Center as well as some custom config files to allow macs to backup on this pc as well. It requires alot of time to get everything set back up properly and would like this to be the last time.

Could this be accomplished by simply running a gksudo instance of Deja and backing up the system? Im also unsure which folders should be backedup up to backup the full filesystem. I wish this was a simple as using TimeMachine in OSX. I'm willing to learn though. Any advice?

Thanks,

On a side note, I upgraded to 12.04 now to see if it would be an easy fix but didn't fix my issues.

[COLOR=Red]ETA: I was finally able to fix all the problems mentioned above. 
I ran the following 
```
rm -r ~/.config/ ~/.cache/
```I now have regained my ability to control my music via the media keys on the keyboard, also fixed the theme issue. Hopefully that will help others with similar problems.[/COLOR]

---

### Post by gennatolls on 2012-04-26
Now to figure out how to properly do a complete backup...

---


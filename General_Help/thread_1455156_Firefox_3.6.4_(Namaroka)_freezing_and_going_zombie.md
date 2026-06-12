---
title: "Firefox 3.6.4 (Namaroka) freezing and going zombie"
date: 2010-04-15
forum: General Help
---

### Post by eldonkr on 2010-04-15
For the past week or so every time I've tried to launch Firefox it would freeze within a few seconds and the process 'firefox-bin' would go Zombie. I would force quit FF and then try and reboot the machine. Then I would get an error before restarting informing me that 'firefox-bin' is nonresponsive and it gives me the options to cancel or reboot anyway.

I'm not entirely sure what's causing this, however I have an inkling suspicion that it's being caused by Netvibes and/or Google Voice, which doesn't make sense because I've been using both services for quite some time now and this is the first time I've encountered any problems.

Has anyone out there encountered somethingt similar?

Update: I've been browsing for about ten minutes now without launching google voice or netvibes and I haven't had any issue yet, so I'm pretty sure those two are causing the problems. But why?

Update2: There's a chance that I could be wrong, but I do know that GV and Netvibes are causing the crash as well as a whole slew of other random websites. I was browsing a website earlier (can't remember the name of it anymore) That also caused my browser to freeze.

To the best of my knowledge I haven't done anything different since this issue started, all I know is that I can no longer safely and conveniently brows the web on this laptop anymore.

---

### Post by lovinglinux on 2010-04-15
> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn’t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]namoroka 3.6.4pre crash flash problem[/color]]("http://www.google.com/search?q=namoroka+3.6.4pre+crash+flash+problem+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by eldonkr on 2010-04-17
Ok, I have the lorentz thing, it's extracted. Now what do I do with it?

---

### Post by lovinglinux on 2010-04-17
> **eldonkr said:**
> Ok, I have the lorentz thing, it's extracted. Now what do I do with it?

[http://tinyurl.com/y48wb7x](http://tinyurl.com/y48wb7x)

---

### Post by eldonkr on 2010-04-17
What if I don't want to leave the extracted lorentz folder in /home?

Where in Filesystem would I relocate it to make everything work?

Or if I follow the instructions in that link, would it still work if I made the lorentz folder hidden?

---

### Post by lovinglinux on 2010-04-17
> **eldonkr said:**
> What if I don't want to leave the extracted lorentz folder in /home?

Where in Filesystem would I relocate it to make everything work?



Usually, it's installed in the **/opt** folder. I have removed the information on how to extract to **/opt** because extracting to home is simpler for beginners, since it doesn't require to use sudo.

The only advantage of extracting to /opt is that it will be available to other users on your machine.

> **eldonkr said:**
> Or if I follow the instructions in that link, would it still work if I made the lorentz folder hidden?

Yes.

---

### Post by eldonkr on 2010-04-17
Thanks, it worked a whole bunch. As soon as someone makes an app for ubuntu that allows people to send cookies to others over the internet expect some from me. :)

---

### Post by lovinglinux on 2010-04-18
Np.

BTW, it seems Namoroka has been fixed today.

---

### Post by eldonkr on 2010-04-18
Srsly? Just my luck, go figure.

---


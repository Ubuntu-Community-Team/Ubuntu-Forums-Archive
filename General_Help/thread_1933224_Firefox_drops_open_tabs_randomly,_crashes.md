---
title: "Firefox drops open tabs randomly, crashes"
date: 2012-02-28
forum: General Help
---

### Post by Bucky Ball on 2012-02-28
Hi all,

Sometimes when I open Firefox, whether it be on a restart, coming out of suspend (open laptop lid), or simply just starting Firefox, I get the 'Well, this is embarrassing!' message and Firefox has dropped all my open tabs! The tab with the error message is the only tab open. 

Other times it just crashes randomly and gives me a small error window asking if I'd like to report and it will attempt to restore my tabs. It never can, just takes me to the above message when it opens and, again, all my tabs are gone ...

This is becoming extremely frustrating as I research a lot and there is no way of getting back the open tabs (sometimes a dozen or more) that may have taken me days to accumulate (unless I save every tab to Zotero or bookmarks which I really don't want/shouldn't need to do). All was fine until the second to last Firefox update from memory.

Using 10.10, Firefox 10.0.2.

All help/suggestions greatly appreciated. Ask for additional info. 

Just getting back to uni studies for the year and this definitely is not acceptable. Ubuntu is rock solid for me in every other way (and was for the entire five years of my Bachelor degree, including Firefox until now).

---

### Post by lovinglinux on 2012-02-29
Well, I am not sure about the crashes and why it is losing sessions. However, I have experienced that in the past and I don't use the built-in session manager anymore. I use [Session Manager](https://addons.mozilla.org/en-US/firefox/addon/session-manager/) extension, which works great. It has many options and you can even save multiple sessions like Opera. You can also configure a particular session to auto-save. However you don't need to use that feature to restore the lost tabs. Session Manager also create backups of your sessions.

Also suggest using an extension like [Textarea Cache](https://addons.mozilla.org/en-US/firefox/addon/5761/) to save text you are entering on a text area.

---

### Post by Bucky Ball on 2012-02-29
Thanks for that lovinglinux, may try that out as a back up. But think I may have found the problem. May have!

Checked my Firefox extensions and was telling me Novell Moonlight 3.99.0.3 is incompatible with Firefox 10.0.2. So I removed it, went to the Moonlight download page, downloaded and installed the very same version and it is sitting quite happily in my extensions, no message about incompatibility. Go figure. I will try this out for awhile and see if it changes anything before calling this solved, naturally. 

All my other add-ons showed no error/incompatibility messages so fingers crossed. Hopefully just a glitch with the Firefox update. Cheers. ;)

---

### Post by Bucky Ball on 2012-03-01
Nope, just happened again as I clicked my shortcut to the Ubuntu forums so reinstalling Moonlight wasn't the fix. I have noticed something though. Skype was open and from memory has been when this has happened in the past. I'll keep digging for a connection but if anyone has any ideas, feel free to chime in ...

---

### Post by lovinglinux on 2012-03-01
I always recommend starting Firefox in safe mdoe to see if it is an add-on causing the crashes.

```
firefox -safe-mode
```

If that doesn't help, try creating a new profile.

```
firefox -P
```

Let me know if the problem persists.

---

### Post by Bucky Ball on 2012-03-01
It happens randomly (only every now and then - once a day or two or three) so not sure if I'd glean much from safe mode unless I opened Firefox in safe mode for a week.

I will try the new profile option. Cheers.

---

### Post by Bucky Ball on 2012-03-01
Well, started the machine this morning, logged on, did nothing else but opened Firefox to be greeted by 'Well, this is embarrassing!' message, etc. I can think of other things it is but to print them here would be breaking forum etiquette! 

I will try the new profile as you suggested, lovinglinux, and see how it goes ...

* Have run the new profile command and also cleared all cookies and  everything from the cache in case there was something not nice in there.  Here's hoping ... I really need to get this sorted before the semester gets serious!

* Also, discovered;

```
firefox -no-remote -P
```... pops up a GUI so I can see what profiles I have there. I have me and 'default'. Is that all correct? Should I delete me and create me again, if you follow, or does your previous command do that already?

---

### Post by lovinglinux on 2012-03-02
> **Bucky Ball said:**
> Well, started the machine this morning, logged on, did nothing else but opened Firefox to be greeted by 'Well, this is embarrassing!' message, etc. I can think of other things it is but to print them here would be breaking forum etiquette! 

I will try the new profile as you suggested, lovinglinux, and see how it goes ...

* Have run the new profile command and also cleared all cookies and  everything from the cache in case there was something not nice in there.  Here's hoping ... I really need to get this sorted before the semester gets serious!

* Also, discovered;

```
firefox -no-remote -P
```... pops up a GUI so I can see what profiles I have there. I have me and 'default'. Is that all correct? Should I delete me and create me again, if you follow, or does your previous command do that already?

Don't delete youir default yet, otherwise tyou will lose saved passwords, bookmarks and settings. Just create a new one.

The command *-no-remote* you mention above is to execute two profiles subcutaneously. If you execute *firefox -P* without closing Firefox first, then you need to use the *-no-remote* option.

---

### Post by Bucky Ball on 2012-03-02
Yep, I did close Firefox before issuing 'firefox -P' and creating a new profile but made no difference. Things are worse now. Firefox just crashes without warning for no reason I can see. Just did it then but I have installed Session Manager and that saved the day. This is really not ideal. My machine has been doing some weird things of late so maybe there are other things going on. 

I'd like to be using 10.04 LTS rather than 10.10 (have always used the LTS releases as I need stability/reliability but 10.04 can't use the drivers for my Toshiba Satellite. They just won't install in that. Can't remember why.

But ... point is 10.10 has actually been rock solid up until a few updates ago (2-3 weeks from memory) from what I can gather ...

I'll battle on til 12.04 LTS is stable (which is usually a couple of months after release). :(

---

### Post by lovinglinux on 2012-03-02
> **lovinglinux said:**
> The command *-no-remote* you mention above is to execute two profiles **subcutaneously**.

I just saw that my spelling corrector did something really weird. Is not **subcutaneously**, but **simultaneously**. :D

---

### Post by lovinglinux on 2012-03-02
> **Bucky Ball said:**
> Yep, I did close Firefox before issuing 'firefox -P' and creating a new profile but made no difference. Things are worse now. Firefox just crashes without warning for no reason I can see. Just did it then but I have installed Session Manager and that saved the day. This is really not ideal. My machine has been doing some weird things of late so maybe there are other things going on. 

I'd like to be using 10.04 LTS rather than 10.10 (have always used the LTS releases as I need stability/reliability but 10.04 can't use the drivers for my Toshiba Satellite. They just won't install in that. Can't remember why.

But ... point is 10.10 has actually been rock solid up until a few updates ago (2-3 weeks from memory) from what I can gather ...

I'll battle on til 12.04 LTS is stable (which is usually a couple of months after release). :(

Try a LiveCD without the updates to see if the problem persists.

Also, start Firefox from terminal and post if you get any error messages when it crashes.

---


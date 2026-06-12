---
title: "Firefox on top when clicking links from other apps?"
date: 2010-04-23
forum: General Help
---

### Post by StuartN on 2010-04-23
Clicking on a web link in an application used to open Firefox in the foreground, on top of the calling application in previous versions of Ubuntu (i.e. whatever versions of applications shipped by default).

In Ubuntu 10.04 if I click on a link in an email message then it opens the page within Firefox 3.6.3, but leaves Firefox behind the calling application. I would prefer to have Firefox take the focus and load the web page on top of my email.

I have tried the usual fixes (setting browser.tabs.loadDivertedInBackground and disabling the Ubuntu extensions), but I can not make Firefox take the focus. Funnily enough, most of the threads I see refer to preventing Firefox from opening on top.

Is there any other setting to set?

---

### Post by sunk8 on 2010-04-23
Hmm...
In Edit >> Preferences, do you have *Open new windows in a new tab instead* checked?

---

### Post by lovinglinux on 2010-04-23
> **StuartN said:**
> Clicking on a web link in an application used to open Firefox in the foreground, on top of the calling application in previous versions of Ubuntu (i.e. whatever versions of applications shipped by default).

In Ubuntu 10.04 if I click on a link in an email message then it opens the page within Firefox 3.6.3, but leaves Firefox behind the calling application. I would prefer to have Firefox take the focus and load the web page on top of my email.

I have tried the usual fixes (setting browser.tabs.loadDivertedInBackground and disabling the Ubuntu extensions), but I can not make Firefox take the focus. Funnily enough, most of the threads I see refer to preventing Firefox from opening on top.

Is there any other setting to set?

I could write an extension to do that. Give me a couple of days, because I'm finishing a new version of another extension and I'm kind of going crazy with it ](*,)

---

### Post by StuartN on 2010-04-23
> **sunk8 said:**
> Hmm...
In Edit >> Preferences, do you have *Open new windows in a new tab instead* checked?

The behaviour is the same with either setting - links will open Firefox on top of the calling application if Firefox is not already open, but links open in Firefox beneath the active application once Firefox has been started. Previously Firefox would be raised on top of the calling application, which is a behaviour I would prefer.

---

### Post by guivho on 2010-05-14
I have also been looking around to find a way to revert this behaviour to the karmic approach, but have not come up with anything.
This must be some mysterious setting somewhere deep down. I find a lot of questions about it, but no answers.
Answers from any reader? I really would like to know how one of both behaviours is selected, and how this can be modified.

---

### Post by StuartN on 2010-05-14
> **guivho said:**
> Answers from any reader?

There seem to be options for focus management in the Configuration editor for Compiz and for Metacity, but inadequate labelling to make sense of the settings.

Certainly it seems to be a window management issue, rather than specifically a Firefox issue - applications like VLC and AviDemux also open underneath the calling application, which can be confusing when there is a hidden dialog requiring human intervention to continue.

---

### Post by raccoonone on 2010-06-05
Anyone find a solution to this? I just upgraded, and it's very annoying to have links from Thunderbird open in the background.

---

### Post by harryc on 2010-06-19
I'm also looking for a solution to this.

---

### Post by StuartN on 2010-06-20
> **harryc said:**
> I'm also looking for a solution to this.

I have got used to it at this stage, but it is still annoying that the behaviour is not consistent between applications - if I double-click a *.txt file in Nautilus, then gedit is raised to the foreground with the file opened in a new window. If I double-click a *.html file, then it is opened in the background in Firefox - unless Firefox is not open, in which case it is opened in the foreground.

I assume the different behaviour means that it is a Firefox issue and not a window manager issue.

---

### Post by thol4u on 2010-07-05
Is there any fix for this issue? I have the same problem..

---

### Post by muschiosauro on 2011-01-27
Hello. If you are using Compiz, try to open compiz settings manager and loook  under "general" settings. There's an option for "focus stealing  prevention level". Change that to "none". That solved the problem for me

---

### Post by harryc on 2011-01-31
@muschiosauro, nice find. Your solution works for me. Thanks!

---


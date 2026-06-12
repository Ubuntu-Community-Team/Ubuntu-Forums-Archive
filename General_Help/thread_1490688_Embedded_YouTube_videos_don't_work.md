---
title: "Embedded YouTube videos don't work"
date: 2010-05-22
forum: General Help
---

### Post by Zeikcied on 2010-05-22
Since the start of April, I've had some problems with embedded YouTube videos, no matter the site.  I click Play, and I get a message saying "An error has occurred.  Please try again later."  (I may be paraphrasing the message a bit.)

I've purged and reinstalled the flashplugin-installer package at least five times, and it hasn't helped.  I turned off AdBlock and FlashBlock, and the error message still happens.

I can view the videos without error on YouTube itself, so I never thought much of it.  I figured it might have been due to the redesign around April 1st, but people and sites keep using embedded videos and I've seen no one else complain about errors, so I'm assuming it's a more isolated problem.

I'm using Kubuntu 10.04 with Firefox 3.6.3.  Though the problem started in 9.10 and Firefox 3.5.x.

---

### Post by johngreth on 2010-05-23
you need to install the flash RC from the adobe website. I think it will be in the repository soon. Also, I don't think it works with 64bit.
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by lovinglinux on 2010-05-23
If you have 64bit, then you need the 64bit beta plugin to solve this issue.

Install [FLASH-AID](http://ubuntuforums.org/showthread.php?t=1491268) extension for Firefox. It will remove any conflicting plugins and install the proper version of Flash according to your browser architecture.

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

You might also like [FlashVideoReplacer](http://ubuntuforums.org/showthread.php?p=9323038#post9323038).

---

### Post by Zeikcied on 2010-05-24
> **lovinglinux said:**
> If you have 64bit, then you need the 64bit beta plugin to solve this issue.

Install [FLASH-AID](http://ubuntuforums.org/showthread.php?t=1491268) extension for Firefox. It will remove any conflicting plugins and install the proper version of Flash according to your browser architecture.

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

You might also like [FlashVideoReplacer](http://ubuntuforums.org/showthread.php?p=9323038#post9323038).

Thanks, but Flash-Aid didn't help.

Since I started the thread, I tried disabling all my add-ons.  That didn't help.  I did install Opera, and found that Opera can play the embedded videos just fine.  Only Firefox can't.  So it's not a problem with Flash.  Also, I use the 32-bit version of Kubuntu (despite having an AMD Athlon 64 CPU).

Embedded videos have worked before.  They just suddenly stopped working around the first of April.  I don't know if it happened before then and I just didn't notice, or if it did coincide with the YouTube redesign.  I doubt the redesign is the cause, as it doesn't seem like anyone else is having this particular issue.

---

### Post by lovinglinux on 2010-05-24
See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

---

### Post by Zeikcied on 2010-05-24
> **lovinglinux said:**
> See the fifth item on [this list](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html).

Disabling IPv6?  Didn't help. :(

---

### Post by lovinglinux on 2010-05-24
Does it happen with any YouTube embedded video? Can you see the videos on my web site?

---

### Post by Zeikcied on 2010-05-24
> **lovinglinux said:**
> Does it happen with any YouTube embedded video? Can you see the videos on my web site?

Any embedded videos.

Just tried one on your site.  Same error message.

---

### Post by lovinglinux on 2010-05-25
Try to delete the cache and YouTube/Google cookies.

---

### Post by Zeikcied on 2010-05-25
> **lovinglinux said:**
> Try to delete the cache and YouTube/Google cookies.

Tried that already.  It doesn't help. :(

---

### Post by lovinglinux on 2010-05-25
Try to create and launch a new Firefox profile and see if the problem persists:

```
firefox -P
```

---

### Post by Zeikcied on 2010-05-25
> **lovinglinux said:**
> Try to create and launch a new Firefox profile and see if the problem persists:

```
firefox -P
```

The problem doesn't exist on the new profile.  The videos work as they should.

So then something went wrong in my Firefox profile, huh?  How should I go about finding and fixing it?  I don't want to lose all my configurations. :(

---

### Post by lovinglinux on 2010-05-25
> **Zeikcied said:**
> The problem doesn't exist on the new profile.  The videos work as they should.

So then something went wrong in my Firefox profile, huh?  How should I go about finding and fixing it?  I don't want to lose all my configurations. :(

See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Zeikcied on 2010-05-25
> **lovinglinux said:**
> See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Ah, it was the prefs.js file.  Something happened at some point.  Now everything works fine.

Thanks for helping me figure this out. :)

EDIT: Or at least it was working.  One of my settings must be throwing it off.  Maybe having the cache set to 1MB is too low.  I'll try that.

EDIT #2: This seems oddly simple.  I can't believe I didn't figure it out.  Apparently YouTube embedded videos started requiring third-party cookies enabled, and I've had them turned off.  While I hate having those enabled, even with the "Ask every time" setting, I at least know my problem.

---

### Post by lovinglinux on 2010-05-25
> **Zeikcied said:**
> Ah, it was the prefs.js file.  Something happened at some point.  Now everything works fine.

Thanks for helping me figure this out. :)

You are welcome.

---

### Post by lovinglinux on 2010-05-25
> **Zeikcied said:**
> EDIT: Or at least it was working.  One of my settings must be throwing it off.  Maybe having the cache set to 1MB is too low.  I'll try that.

Possibly.

---

### Post by Zeikcied on 2010-05-25
> **lovinglinux said:**
> Possibly.

I made a second edit.  It was third-party cookies this whole time.  I hate third party cookies, and would rather they stay disabled, but at least I know what the cause is.

---

### Post by lovinglinux on 2010-05-25
> **Zeikcied said:**
> I made a second edit.  It was third-party cookies this whole time.  I hate third party cookies, and would rather they stay disabled, but at least I know what the cause is.

That is weird, because I have third-party cookies blocked and it works for me.

---

### Post by lovinglinux on 2010-05-25
For the sake of curiosity, I have deleted all my cookies and blocked them all. The videos still work, even without getting any youtube or google cookie.

---

### Post by Zeikcied on 2010-05-25
> **lovinglinux said:**
> For the sake of curiosity, I have deleted all my cookies and blocked them all. The videos still work, even without getting any youtube or google cookie.

That's odd.

I turn off third-party cookies, and the error shows up.  I turn them on, and the error goes away.  So I'm positive that's what it is.  I don't know why it's not doing the same thing for you.

You have "Accept third-party cookies" unchecked, right?  I'm sure that's what you mean by you have them blocked, but I want to be sure.

---

### Post by lovinglinux on 2010-05-25
> **Zeikcied said:**
> You have "Accept third-party cookies" unchecked, right?  I'm sure that's what you mean by you have them blocked, but I want to be sure.

Yes, but I also tested with ALL cookies blocked and deleted all stored cookies to make sure. Nevertheless, I only tested on my site, which is hosted by Blogger (Google).

---

### Post by Zeikcied on 2010-05-25
Well, I at least have a workaround, but now I can't help but wonder why the error is only happening for me and not you or anyone else.  Sure, it works with the third-party cookies enabled, but based on what you're saying it seems like I should be able to have them disabled without any errors.

---

### Post by Zeikcied on 2010-05-26
> **Zeikcied said:**
> Well, I at least have a workaround, but now I can't help but wonder why the error is only happening for me and not you or anyone else.  Sure, it works with the third-party cookies enabled, but based on what you're saying it seems like I should be able to have them disabled without any errors.

I went back to the new "Test" profile that you had me create.  I went into the preferences and set it to exactly what I have in my default profile (cache 1MB, third-party cookies off, etc.).  I tried an embedded video, and it worked.  So while the workaround with the cookies is functional, there is still a problem that exists that has not been solved.

I'm sure you know way more about Firefox than me.  Do you have any idea what would cause an issue like this?  I'm guessing it's a file in my profile folder, but I don't know which one (if any) to try deleting first.

Also, I just cleared out all my cookies (not the Allow/Block list, though) just to test, and that didn't help.

---

### Post by lovinglinux on 2010-05-26
> **Zeikcied said:**
> I went back to the new "Test" profile that you had me create.  I went into the preferences and set it to exactly what I have in my default profile (cache 1MB, third-party cookies off, etc.).  I tried an embedded video, and it worked.  So while the workaround with the cookies is functional, there is still a problem that exists that has not been solved.

I'm sure you know way more about Firefox than me.  Do you have any idea what would cause an issue like this?  I'm guessing it's a file in my profile folder, but I don't know which one (if any) to try deleting first.

Also, I just cleared out all my cookies (not the Allow/Block list, though) just to test, and that didn't help.

I'm not sure what could be causing this, but I guess the easiest way to fix it is to copy only the things you really need into the new profile. Install [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) extension on both profiles, then create a selective backup of the old profile (not the full backup) choosing only the things you need like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158278&stc=1&d=1274854130[/IMG]

To backup your extensions, use the quick backup feature and select the "Create single xpi" option like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158279&stc=1&d=1274854369[/IMG]

It will generate a single installation xpi file with all your extensions.

When restoring these backups to your new profile, don't restore everything at once. Restore each file one-by-one, always testing the profile after restoring each file. This will probably allow you to pinpoint where the problem really is.

Let me know after which restoration the browser starts to behave badly.

---

### Post by Zeikcied on 2010-05-26
I backed up my prefs, bookmarks, cookies, and username/passwords.  None of those files were apparently the issue.  I think I have most things back to normal, although I'm going to have to redo my AdBlock whitelist.  Unless I can import the AdBlock preferences somehow.  I'll see if I can figure that out on my own.  (Seems like I have to go to the old profile, export my custom filters, and then import them in the new profile.  Seems easy enough.)

So I'm in a fresh profile and everything seems to be working properly.  Thanks again. :)

---

### Post by lovinglinux on 2010-05-26
> **Zeikcied said:**
> (Seems like I have to go to the old profile, export my custom filters, and then import them in the new profile.  Seems easy enough.)

Yes, that's how you can backup your AdBlock settings.

---

### Post by Zeikcied on 2010-05-30
The problem has come back in the new profile now.

I really wish I knew the cause right now.

The only thing I can think of that I changed was setting up the .amz file type to open automatically with the Amazon MP3 Downloader.  I don't remember if I set or changed a Mimetype around the start of April or not.  I don't think I did...  Would an error with the Mimetype settings really cause an error like this?

I don't think I did anything else beyond that.

---

### Post by lovinglinux on 2010-05-30
> **Zeikcied said:**
> The problem has come back in the new profile now.

I really wish I knew the cause right now.

The only thing I can think of that I changed was setting up the .amz file type to open automatically with the Amazon MP3 Downloader.  I don't remember if I set or changed a Mimetype around the start of April or not.  I don't think I did...  Would an error with the Mimetype settings really cause an error like this?

I don't think I did anything else beyond that.

I'm not sure, but you could delete the file mimeTypes.rdf to check it out.

---

### Post by Zeikcied on 2010-05-30
> **lovinglinux said:**
> I'm not sure, but you could delete the file mimeTypes.rdf to check it out.

Didn't help.

It confuses me why it's only happening to embedded YouTube videos.  The videos work fine on YouTube itself.  And no other embedded videos from other sites (Viddler, DailyMotion, etc.) are having problems.  Only YouTube embedded videos.  It makes no sense to me.

---

### Post by lovinglinux on 2010-05-30
> **Zeikcied said:**
> Didn't help.

It confuses me why it's only happening to embedded YouTube videos.  The videos work fine on YouTube itself.  And no other embedded videos from other sites (Viddler, DailyMotion, etc.) are having problems.  Only YouTube embedded videos.  It makes no sense to me.

Can you still use the cookie workaround?

---

### Post by PinchedNerve on 2010-05-30
> **Zeikcied said:**
> Didn't help.

It confuses me why it's only happening to embedded YouTube videos.  The videos work fine on YouTube itself.  And no other embedded videos from other sites (Viddler, DailyMotion, etc.) are having problems.  Only YouTube embedded videos.  It makes no sense to me.

Try this. I posted this a little while back & it seems to have been ignored but it fixed my issues totally with exactly the same issue you have....

[http://ubuntuforums.org/showthread.php?t=1491482](http://ubuntuforums.org/showthread.php?t=1491482)

---

### Post by lovinglinux on 2010-05-30
> **PinchedNerve said:**
> Try this. I posted this a little while back & it seems to have been ignored but it fixed my issues totally with exactly the same issue you have....

[http://ubuntuforums.org/showthread.php?t=1491482](http://ubuntuforums.org/showthread.php?t=1491482)

Thanks for sharing. I saw your thread a while a go, but totally forgot about it. Is hard to keep tabs on so many threads and issues ;)

---

### Post by Zeikcied on 2010-05-30
> **PinchedNerve said:**
> Try this. I posted this a little while back & it seems to have been ignored but it fixed my issues totally with exactly the same issue you have....

[http://ubuntuforums.org/showthread.php?t=1491482](http://ubuntuforums.org/showthread.php?t=1491482)

I use KDE4, not Gnome, so I assume the equivalent is to turn off Desktop Effects (System Settings - Desktop - Desktop Effects).  But that didn't help.

The problem is "fixed" if I make a new Firefox profile.  And while it was fine for three days, it came back.

I don't know if an extension I have installed is causing a misconfiguration or if it's something else entirely.  I think if it was an extension that more people would be reporting a problem, though.

Again, the fact that it's only embedded YouTube videos boggles my mind.  I can't fathom how a corrupt or misconfigured file would only affect embedded YouTube videos and nothing else.  Especially when turning on third-party cookies is an acceptable workaround.

---

### Post by charper_99 on 2010-06-08
I found this thread while searching for a solution to this problem.  I recently upgraded from 9.04 to 10.04 via a 100% clean install (reformatted, imported nothing but non-app files back in).  I think this puts me in a somewhat unique situation for this problem.  I currently only have xmarks installed - other than that I'm working off the firefox defaults.  I do have the official nvidia (restricted) driver, and full effects + compiz enabled.  

I can watch youtube videos from the youtube site, but *any* embedded videos fail.  Clicking play (either main window or control bar) does nothing.  The GUI responds as if it is receiving a button down command, but other than that does nothing.  Embedded YouTube videos from all sites, even locally-opened html files fail.  Right-clicking and selecting "Watch on YouTube" is a workaround, but obviously slightly inconvenient.

---

### Post by Zeikcied on 2010-06-08
> **charper_99 said:**
> I found this thread while searching for a solution to this problem.  I recently upgraded from 9.04 to 10.04 via a 100% clean install (reformatted, imported nothing but non-app files back in).  I think this puts me in a somewhat unique situation for this problem.  I currently only have xmarks installed - other than that I'm working off the firefox defaults.  I do have the official nvidia (restricted) driver, and full effects + compiz enabled.  

I can watch youtube videos from the youtube site, but *any* embedded videos fail.  Clicking play (either main window or control bar) does nothing.  The GUI responds as if it is receiving a button down command, but other than that does nothing.  Embedded YouTube videos from all sites, even locally-opened html files fail.  Right-clicking and selecting "Watch on YouTube" is a workaround, but obviously slightly inconvenient.

That's not quite the same problem.  If the Flash buttons aren't working, you can hold Shift or Ctrl while you click, and it will work.  It doesn't always fail to register clicks.

My problem is that when I click Play, or when the video tries to auto-play, it gives an error saying "An error has occurred, please try again later."  And it only happens with YouTube embedded videos.  Viddler, DailyMotion, etc. work fine, despite the occasional button issues.

---

### Post by Cavsfan on 2010-06-08
See this post for the workaround. I had the same problem and only had to do step 3 to fix my problem.
_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

---

### Post by Zeikcied on 2010-06-08
> **Cavsfan said:**
> See this post for the workaround. I had the same problem and only had to do step 3 to fix my problem.
_[http://ubuntuforums.org/showpost.php?p=9380613&postcount=2](http://ubuntuforums.org/showpost.php?p=9380613&postcount=2)_

Another work around is to simply hold down Ctrl or Shift when clicking the buttons.

Those workarounds will work for charper_99's problem, but that's not what my problem is.  My problem is an error message, not a simple lack of response from the buttons.

---

### Post by Zeikcied on 2010-07-30
At this point I'm at a complete and total loss.

I set up yet another new profile and I copied over only my bookmarks (via the HTML export file) and my saved usernames and passwords.  A couple extensions also had export features which let me copy their preferences.

Other than that, it was a fresh profile.  I downloaded each add-on fresh from the Mozilla site, I redid my preferences, and everything was fine.  Just like the last time I started a new profile, the embedded YouTube videos were working without any error.

Then today I notice they're giving that "An error has occurred, please try again later" message.  *sigh*  I don't know what I can do at this point.  Pretty much everything I can think of hasn't worked, short of purging and reinstalling Firefox.

---

### Post by lovinglinux on 2010-07-30
> **Zeikcied said:**
> At this point I'm at a complete and total loss.

I set up yet another new profile and I copied over only my bookmarks (via the HTML export file) and my saved usernames and passwords.  A couple extensions also had export features which let me copy their preferences.

Other than that, it was a fresh profile.  I downloaded each add-on fresh from the Mozilla site, I redid my preferences, and everything was fine.  Just like the last time I started a new profile, the embedded YouTube videos were working without any error.

Then today I notice they're giving that "An error has occurred, please try again later" message.  *sigh*  I don't know what I can do at this point.  Pretty much everything I can think of hasn't worked, short of purging and reinstalling Firefox.

You need to consider the possibility of being an issue with YouTube. They changed the site code on July 22nd and I had to update one of my extensions, just like all the other video download extensions. Perhaps it is failing on you because of these new changes.

---

### Post by Cavsfan on 2010-07-30
I cannot imagine what the problem is. I have been watching youtube videos for a while now trying to see if I get any errors.
And I have no problem whatsoever. 
I hope you get it figured out soon as I know how frustrating it can be.

But, I am having no problems with Youtube. There was one that didn't play any sound and I think I'll try that again to see what happens...mmmm

---

### Post by Zeikcied on 2010-07-30
> **lovinglinux said:**
> You need to consider the possibility of being an issue with YouTube. They changed the site code on July 22nd and I had to update one of my extensions, just like all the other video download extensions. Perhaps it is failing on you because of these new changes.

But you know I've been having these issues ever since around April 1st, when the big redesign went live.  I've been silent for over a month on this issue because I gave up trying to find a solution.  Finally I decided to try with a fresh start, and it still came back.

Yeah, it may be some sort of issue with YouTube, but has anyone complained about the same problem?  I have a hard time believing I'm the only one with this problem.

I don't think it's an extension issue, as I ran in safe mode and still had the error.

It goes away when I start a fresh profile, but gets corrupted somewhere along the lines within a few days.  I wouldn't think an extension would continue to cause trouble once it's disabled.

Could an extension mess with profile files?  Would running ext4 make any difference?

FlashBlock and UnPlug are the only extensions relating to Flash or YouTube that I was running when these problems started, and continue to run now.  There's also AdBlock Plus, but I don't think that's the issue.  The rest are for other various purposes (1-Click Weather, BlockSite, Download Statusbar, GMail Manager, and Linkification), and one I installed after my issues started (YouTube MP3, since UnPlug was having some trouble for a while there).  And at one point I did uninstall UnPlug, and that didn't help. :(

---

### Post by lovinglinux on 2010-07-30
> **Zeikcied said:**
> But you know I've been having these issues ever since around April 1st, when the big redesign went live.  I've been silent for over a month on this issue because I gave up trying to find a solution.  Finally I decided to try with a fresh start, and it still came back.

Yeah, it may be some sort of issue with YouTube, but has anyone complained about the same problem?  I have a hard time believing I'm the only one with this problem.

I don't think it's an extension issue, as I ran in safe mode and still had the error.

It goes away when I start a fresh profile, but gets corrupted somewhere along the lines within a few days.  I wouldn't think an extension would continue to cause trouble once it's disabled.

Could an extension mess with profile files?  Would running ext4 make any difference?

FlashBlock and UnPlug are the only extensions relating to Flash or YouTube that I was running when these problems started, and continue to run now.  There's also AdBlock Plus, but I don't think that's the issue.  The rest are for other various purposes (1-Click Weather, BlockSite, Download Statusbar, GMail Manager, and Linkification), and one I installed after my issues started (YouTube MP3, since UnPlug was having some trouble for a while there).  And at one point I did uninstall UnPlug, and that didn't help. :(

You are not the only one, but this is not a common issue and I don't know bulletproof solution.

Extensions could cause this. For instance, AdBlock is preventing videos with ads from running recently. I need to disable it on my ISP video portal. This wasn't happening until recently.

---

### Post by Zeikcied on 2010-07-30
> **lovinglinux said:**
> You are not the only one, but this is not a common issue and I don't know bulletproof solution.

Extensions could cause this. For instance, AdBlock is preventing videos with ads from running recently. I need to disable it on my ISP video portal. This wasn't happening until recently.

I know about the AdBlock thing, but YouTube doesn't play ads.

You mean I'm not the only one getting the "An error has occurred, please try again" message?  That's a bit of a relief, I guess.  I'm still at a loss as to why enabling third-party cookies is a work-around.

I guess it's not a terribly important issue.  I usually just click on the YouTube logo or video title and watch it on YouTube itself.  It's just annoying.  Though I've gotten used to it.

---

### Post by lovinglinux on 2010-07-30
> **Zeikcied said:**
> I know about the AdBlock thing, but YouTube doesn't play ads.

I know, but it could be blocking authentication, since the video is embedded on a different site. Just guessing.

---

### Post by Cavsfan on 2010-07-31
> **Zeikcied said:**
> I know about the AdBlock thing, but YouTube doesn't play ads.

You mean I'm not the only one getting the "An error has occurred, please try again" message?  That's a bit of a relief, I guess.  I'm still at a loss as to why enabling third-party cookies is a work-around.

I guess it's not a terribly important issue.  I usually just click on the YouTube logo or video title and watch it on YouTube itself.  It's just annoying.  Though I've gotten used to it.

Youtube does have embedded ads in some of their videos. At least that is what I see and I click on the x on the right to close them. 

> **lovinglinux said:**
> I know, but it could be blocking authentication, since the video is embedded on a different site. Just guessing.

I would bet that those extensions are causing your problem. Here are the only ones I have: 1-ClickWeather from the weather channel (toolbar), 
BetterPrivacy, Flash-Aid and Ubuntu Firefox Modifications. I haven't had any problems with Youtube that I can tell at least, except slow loading video sometimes.

---

### Post by Zeikcied on 2010-07-31
> **lovinglinux said:**
> I know, but it could be blocking authentication, since the video is embedded on a different site. Just guessing.

But I can disable all my extensions and it will still give the error. :(

---

### Post by Cavsfan on 2010-07-31
> **Zeikcied said:**
> But I can disable all my extensions and it will still give the error. :(

That is weird! I wish I could help, but this is **lovinglinux**'s specialty and if he can't fix it, no one can. 
Hopefully he will figure it out.

---

### Post by lovinglinux on 2010-07-31
> **Zeikcied said:**
> But I can disable all my extensions and it will still give the error. :(

Perhaps the extension itself doesn't affect flash directly, but for some reason, cause a file corruption after a while. 

I don't think I have suggested this, but try to delete **secmod.db** file from your profile. I have no idea if it could influence your problem, but several users are having issues with it since Firefox 3.6.7 and the behavior is similar to your situation. Firefox works for a while, then simply stops loading.

---

### Post by Cavsfan on 2010-07-31
**lovinglinux**, I seen that Mozilla is using your latest version of Flash-Aid for their add-ons. Cool!
I installed it myself. Thanks and keep the good work! :D

---

### Post by lovinglinux on 2010-07-31
> **Cavsfan said:**
> **lovinglinux**, I seen that Mozilla is using your latest version of Flash-Aid for their add-ons. Cool!
I installed it myself. Thanks and keep the good work! :D

Thanks. Just to clarify,  anyone can submit add-ons to be included in the AMO site. There is a review process tho, in which all extensions are manually checked for errors,  malicious code and relevance. If approved, then they recieve the green download button and the extension users are provided with automatic updates through Firefox add-on manager. 

All [my public extensions are hosted there]("https://addons.mozilla.org/en-US/firefox/user/4352153"), because I have submitted them and they got approved. There is [one that hasn't been approved]("http://foxmediacenter-extension.blogspot.com") tho, due to several javascript warnings and perfromance. The extension was the first one I designed and since the code is huge and badly written, I decided to re-write it, but this time splitting it's function between three new extensions, currently under development. They are looking good so far and I'm sure they will get approved this time :)

---

### Post by lovinglinux on 2010-07-31
I know is not a fix, but it could be a solution for you. I just found an extension that allows you to poup out videos from youtube and other sites: [OCP VideoPOPOUT]("https://addons.mozilla.org/en-US/firefox/addon/197221/"). 

I have tested with embedded videos on my blog and it works.

---

### Post by Zeikcied on 2010-12-05
I got a new computer, and am now running a 64-bit Kubuntu.  I made sure that in transferring over my files that I deleted the .mozilla folder and only exported the settings most important to me (bookmarks and settings for two add-ons).  I figured I'd never see this error again.

Oh, how wrong I was.

It came back, defying all logic.  So today I decided to get to the bottom of things.  I found a site with an embedded YouTube video and I went through each of my option changes and add-on installs until the error happened.  One by one I changed settings and refreshed the page (or restarted Firefox in the case of add-ons).  I got through all the add-ons I installed on the new computer that I also had before the error started, and none caused the problem.

Then I finally encountered the error, and did my best to figure out what it was.  In the end, it was my cookie settings.

I started from a fresh profile.  The embedded video worked.  I turned off third-party cookies and set the cookies to "Ask me every time."  I tried again, and the video played.  I went to YouTube, and I accepted the [www.youtube.com](www.youtube.com) cookie.  Then I refreshed the page, and the error occurred.  I turn third-party cookies on, and the error goes away.  Now, the video worked when third-party cookies were disabled and when my cookies were set to "Until they expire."  I even went to the YouTube page so that the cookies would be set, and it still worked just fine.  But turning off third-party cookies AND clicking "Ask me every time" (while keeping [www.youtube.com](www.youtube.com) as an Allow exception) causes the error.

Needless to say, I'm still bloody confused.

---

### Post by lovinglinux on 2010-12-20
> **Zeikcied said:**
> I got a new computer, and am now running a 64-bit Kubuntu.  I made sure that in transferring over my files that I deleted the .mozilla folder and only exported the settings most important to me (bookmarks and settings for two add-ons).  I figured I'd never see this error again.

Oh, how wrong I was.

It came back, defying all logic.  So today I decided to get to the bottom of things.  I found a site with an embedded YouTube video and I went through each of my option changes and add-on installs until the error happened.  One by one I changed settings and refreshed the page (or restarted Firefox in the case of add-ons).  I got through all the add-ons I installed on the new computer that I also had before the error started, and none caused the problem.

Then I finally encountered the error, and did my best to figure out what it was.  In the end, it was my cookie settings.

I started from a fresh profile.  The embedded video worked.  I turned off third-party cookies and set the cookies to "Ask me every time."  I tried again, and the video played.  I went to YouTube, and I accepted the [www.youtube.com](www.youtube.com) cookie.  Then I refreshed the page, and the error occurred.  I turn third-party cookies on, and the error goes away.  Now, the video worked when third-party cookies were disabled and when my cookies were set to "Until they expire."  I even went to the YouTube page so that the cookies would be set, and it still worked just fine.  But turning off third-party cookies AND clicking "Ask me every time" (while keeping [www.youtube.com](www.youtube.com) as an Allow exception) causes the error.

Needless to say, I'm still bloody confused.

YouTube cookies are driving me crazy recently, because of ione of my extensions.

Try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com)

This is not a third party site, it is from YouTube, but it doesn't save cookies.

---

### Post by Zeikcied on 2010-12-20
> **lovinglinux said:**
> YouTube cookies are driving me crazy recently, because of ione of my extensions.

Try [http://www.youtube-nocookie.com](http://www.youtube-nocookie.com)

This is not a third party site, it is from YouTube, but it doesn't save cookies.

Thanks, but I don't think that would help.  I mean, I like being signed in and having access to my channel subscriptions and stuff.

It would be nice to know why the YouTube cookies are causing this error and have it fixed somehow.  I don't know if it's an issue I should bring to YouTube or Mozilla, though.  I'd say YouTube, as it started for me on their April 1st redesign, but I'm shocked that it's not a "known issue" after all these months.  You'd think that someone would have reported it, as from your comments I'm not the only one having this issue.

---

### Post by humandraydel on 2011-01-11
I've had this problem for months also.  I was running Ubuntu 8.10 until a week ago - now I'm running 10.04 and I still have the same problem.  My solution for months (on 8.10) was to just use a different browser for youtube.  It's stupid, I know, but it is an easy solution.


EDIT:  Ok, my fix makes me look stupid.  I just add to add youtube to the "exception" list for cookies.  I can't believe I never tried that - I was sure I had already added it to the list but apparently not.

---

### Post by Zeikcied on 2011-01-16
> **humandraydel said:**
> I've had this problem for months also.  I was running Ubuntu 8.10 until a week ago - now I'm running 10.04 and I still have the same problem.  My solution for months (on 8.10) was to just use a different browser for youtube.  It's stupid, I know, but it is an easy solution.


EDIT:  Ok, my fix makes me look stupid.  I just add to add youtube to the "exception" list for cookies.  I can't believe I never tried that - I was sure I had already added it to the list but apparently not.

o_o

Holy crap.  Adding "youtube.com" with no www or any other subdomains to "Allow" under Exceptions fixes the bug.  I cannot believe how simple that is.

---

### Post by Carambakaracho on 2012-02-12
Hey there, 
some late thanks. Your fix worked for me. I had the same error for almost a year now. However, my girlfriend was using this computer most of the time and actually never cared too much. I just happened to find your thread today and it solved the issue. 

Thank you so much for a workaround for this annoying bug, especially as I watch almost all youtube videos embedded into some other site.

C.

---


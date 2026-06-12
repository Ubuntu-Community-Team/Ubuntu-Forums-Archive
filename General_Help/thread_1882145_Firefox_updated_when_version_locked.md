---
title: "Firefox updated when version locked?"
date: 2011-11-16
forum: General Help
---

### Post by MrGrey1 on 2011-11-16
Hi all,
A while back I got sick of the ridiculous update cycle that the /expletive devs at Mozilla have started using. It was consistently breaking add-ons so I decided to lock the version number in synaptic and stick with the version I was on. That was V6. 
So V7 came along and my Firefox still updated. I did a double take, was rather surprised but thought I must not have locked it properly or done something stupid. So I went back into synaptic and made doubly sure I locked it properly.
V8 has just come out and guess what? It updated! It's still a locked package in Synaptic but it's now version 8.
My question is WTF? How does that work? The whole point of locking the package is to prevent updates. How is it that Firefox is still updating? Is Synaptic broken or is it some Mozilla hack? Can anyone tell me how to STOP Firefox updating?

Better yet can anyone tell me if there's another browser around that has the equivalent of No-Script, Ghostery and Grease Monkey?

---

### Post by lovinglinux on 2011-11-17
I am not sure why Synaptic is not locking your package version, but is certainly not a Mozilla hack.

Why don't you download the version you want from Mozilla, extract it to your home directory and launch it from there? This way it will remain the same version as long as you want.

That being said, add-on compatibility has improved a lot lately. I am using Firefox 9.0b1 and from 70 add-ons I have installed, only 2 are not compatible. Nevertheless, they still work with compatibility check disabled. You can do that using [Add-on Compatibility Reporter](https://addons.mozilla.org/en-US/firefox/addon/15003/) extension. 

Perhaps the reason why you are experiencing issues with add-ons is that you are using add-ons from the repository. Get rid of those and install directly from Mozilla, so the add-on manager will take care of updating them. BTW, don't forget to set the add-on manager to update your add-ons automatically.

Another reason could be that the add-ons your are using are not updated frequently by the developers. If that is the case, let me know which add-ons you use and can try to find better alternatives.

To finalize, some people like me loves the new update cycle, because we get awesome new features and improvements a lot faster than before.

---

### Post by dcstar on 2011-11-18
> **MrGrey1 said:**
> Hi all,
A while back I got sick of the ridiculous update cycle that the /expletive devs at Mozilla have started using. It was consistently breaking add-ons so I decided to lock the version number in synaptic and stick with the version I was on. That was V6. 
So V7 came along and my Firefox still updated. I did a double take, was rather surprised but thought I must not have locked it properly or done something stupid. So I went back into synaptic and made doubly sure I locked it properly.
V8 has just come out and guess what? It updated! It's still a locked package in Synaptic but it's now version 8.
My question is WTF? How does that work? The whole point of locking the package is to prevent updates. How is it that Firefox is still updating? **Is Synaptic broken** or is it some Mozilla hack? Can anyone tell me how to STOP Firefox updating?
.........

Have a look at how long this embarrassing bug has been around:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178?comments=all](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/42178?comments=all)

---

### Post by MrGrey1 on 2011-12-20
Sorry for slow reply. Thread replies hit my filters.

AHHH! FF updated to V9 when locked in synaptic... again!

@ lovinglinux
"Why don't you download the version you want from Mozilla?"
I don't download another version of firefox because I just want it to work the way it is supposed to. I don't have the time or inclination to d**k around when things should do what they are supposed to from the start. 
Having updates work as intended and the browser conform to my specifications is the most basic requirement of my OS.

I install most of my add-ons straight through firefox. I don't install them from the package manager.
Broken add-ons are not the cause of my issues however. They are a symptom. Fix the cause not the symptom.
I'm pissed off because I have apparently LOST CONTROL of the updates on my own machine. Nothing upsets me more with a computer then not being in control and having someone else dictate what happens on MY machine! It's an invasive and infuriating feeling and the main reason I left Windows behind years ago. My machine. My way.

"because we get awesome new features and improvements a lot faster than before." 
Not true. Really this line sounds like it's straight off a script written by the marketing department at Mozilla. 
The truth is you would have got the same updates, "features," and "improvements" via incremental patches anyway. All you are really getting from this new update regime is a new VERSION number and a guarantee of regularly broken add-ons. The new update cycle is an obvious example of hipster marketing BS winning out over programming best practise and a sure sign that the Mozilla organisation has lost it. Judging from the 1000's of similar threads about the firefox update cycle all over the net, I'm certainly not alone in my sentiments. And it shows in the browser usage stats... 
I don't mean to be rude, and I apologise if it's not the case, but the way you are talking about firefox seems like astroturfing from where I'm sitting.

@ dcstar
"Have a look at how long this embarrassing bug has been around:"

Thanks for the link. Read that thread. "2006-04-30" Good lord... It's hard to believe that such a MAJOR bug has been left for so long... /shakes head and dreams of a day when Dev's FIX bugs rather then adding "improvements" and "features."

SOL. :(

---

### Post by lovinglinux on 2011-12-21
> **MrGrey1 said:**
> 

@ lovinglinux
"Why don't you download the version you want from Mozilla?"
I don't download another version of firefox because I just want it to work the way it is supposed to. I don't have the time or inclination to d**k around when things should do what they are supposed to from the start. 
Having updates work as intended and the browser conform to my specifications is the most basic requirement of my OS.

I install most of my add-ons straight through firefox. I don't install them from the package manager.
Broken add-ons are not the cause of my issues however. They are a symptom. Fix the cause not the symptom.
I'm pissed off because I have apparently LOST CONTROL of the updates on my own machine. Nothing upsets me more with a computer then not being in control and having someone else dictate what happens on MY machine! It's an invasive and infuriating feeling and the main reason I left Windows behind years ago. My machine. My way.

First, I think you should report the Synaptic bug on launchpad, because this is a Ubuntu issue and not a Firefox issue.

Second, you could turn off automatic updates and set the update manager to just warn you about the updates, so you can select which updates to apply. This won't fix the Synaptic issue, but it is a decent workaround. Besides, if you are so worried about CONTROL, that is the way you should setup your updates. To do that, open Software Center, click "Edit >> Software Sources", then click the "Updates" tab and change the settings accordingly.

> **MrGrey1 said:**
> 
"because we get awesome new features and improvements a lot faster than before."
Not true. Really this line sounds like it's straight off a script written by the marketing department at Mozilla.
The truth is you would have got the same updates, "features," and "improvements" via incremental patches anyway. All you are really getting from this new update regime is a new VERSION number and a guarantee of regularly broken add-ons. The new update cycle is an obvious example of hipster marketing BS winning out over programming best practise and a sure sign that the Mozilla organisation has lost it. Judging from the 1000's of similar threads about the firefox update cycle all over the net, I'm certainly not alone in my sentiments. And it shows in the browser usage stats...
I don't mean to be rude, and I apologise if it's not the case, but the way you are talking about firefox seems like astroturfing from where I'm sitting.

First of all, let me clarify that I am a volunteer member of the Mozilla's Featured Add-on Advisory Board, but I don't work for Mozilla and certainly don't get paid by them to promote Firefox in forums. Essentially, I help to choose which add-ons are featured in the Mozilla add-on web site each month. In addition to that, I am also a Firefox add-on developer. The add-ons I develop are mostly designed to help Ubuntu users and to help me doing stuff I want.

Although I have such connection with Mozilla in the last 7 months, I have been helping Firefox users here, following Firefox development and talking about Firefox releases and features long before I joined the Advisory Board. I have been using Firefox since version 0.9, except for a brief period before Firefox 4 release, in which I started using Opera because of frustration with broken add-ons, fact that I was very vocal about in these forums. So, as you can see, I can relate to your feelings.

I test and I use a lot of add-ons and can sincerely say that the new release cycle was a blessing to me. When Firefox 4 Beta was released, I had to wait months before all my add-ons were compatible. Now, most of the time only a couple of add-ons I use are not compatible with the latest Firefox Beta and they all work with compatibility check disabled.

From Firefox 10 onwards, add-ons will be considered compatible by default, unless flagged due to incompatible code. I am using this version and this new feature works great. I have 74 add-ons installed today and they all work with the latest Firefox Aurora. No compatibility hacks needed.

This implementation was the last step to solve the issue with add-ons in the new development cycle. Things will be a lot smoother from now on.

About new features being pushed trough incremental patches, that wouldn't happen. As before the new release cycle, Mozila only adds new features in major releases. The changes you see from Firefox 3.6.23 to 3.6.24 are essentially security and stability patches. New features were developed and tested during the long period of development of a new major release, which could take more than a year. Now, new features can land on Firefox every six weeks. That doesn't mean these features are things you can actually see. Currently, they have been implementing a lot of things under the hood. Some important features have been delayed and they do not hold the release anymore. Before the fast release cycle, they would not release the new Firefox version until all planned new features were ready, which usually resulted in many delays in the release schedule. Now they simply disable/remove the new feature and release Firefox on schedule.

Anyway, let's focus on fixing your problem, if want to complain about the Firefox fast release cycle, please do at [http://ubuntuforums.org/showthread.php?t=1818283](http://ubuntuforums.org/showthread.php?t=1818283)

If you still believe my comments are astroturfing, you can report my post, using the report button, so other moderators will look at it.

---


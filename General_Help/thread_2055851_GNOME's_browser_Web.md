---
title: "GNOME's browser: Web"
date: 2012-09-10
forum: General Help
---

### Post by vasa1 on 2012-09-10
Anyone use it? I understand it will be the only browser to ship with the GNOME-flavor of 12.10. Of course, whether people will promptly replace it with their fave is another matter.
Right now, version 3.4.1 is available from the Ubuntu Software Center. [Wikipedia]("http://en.wikipedia.org/wiki/Web_(web_browser)") has a quite some detail about it including this:
> The built-in preference manager for Web is designed to present user only basic browser-specific settings. All the advanced configuration is done with the stand-alone GSettings configurator tools such as GNOME's default dconf (command line) and dconf-editor (graphical).

---

### Post by vasa1 on 2012-09-10
Still misbehaves on Stack Exchange pages :(
CPU usage takes off unpredictably while viewing askubuntu.com or superuser.com.

And the options in dconf-editor are very few. I think people used to Firefox won't stay with Web for long.

---

### Post by qamelian on 2012-09-10
I've recently started using it again on my 12.10 test machine. The current version is occasionally a bit flaky, but I like it well enough to stick with it for a while.

---

### Post by mc4man on 2012-09-10
At least here in 12.10 (atm on an Ubuntu install), by default it's so bad not inclined to even bother. screen 1 is what first is seen
screen 2 is the user preferences
When going into dconf-editor there appears to be things to set, some work, many don't like 'toolbars', can't get any.

After a bit it tends to start opening like in image

(plus like many things in gnome 3 (12.10), very plain, just now looking at getting shading in gtk boxes (buttons), atm I can get a 'full' shading or none, seems hard to fine tune..

---

### Post by qamelian on 2012-09-10
> **mc4man said:**
> At least here in 12.10 (atm on an Ubuntu install), by default it's so bad not inclined to even bother. 
I used to feel the same way about previous versions, but despite a little instability, I'm really enjoying the version in 12.10, so far. This new version even seems to remember the tabs I had open in my previous session and re-opens them for me next time I launch the browser. Lack of this feature was probably my biggest annoyance in previous versions.

---

### Post by afulldeck on 2012-09-10
Why do we need another browser type? What is the benefit?

---

### Post by qamelian on 2012-09-10
> **afulldeck said:**
> Why do we need another browser type? What is the benefit?
Web/Epiphany is the default Gnome browser. The Gnome remix is trying to keep as close to upstream Gnome as possible, hence the inclusion of Web/Epiphany. It's been around for quite a number of years, so it isn't like it's some johnny-come-lately browser. :)

---

### Post by vasa1 on 2012-09-10
> **qamelian said:**
> Web/Epiphany is the default Gnome browser. ...
Please try it on the sites I mentioned. I've had the issue of high CPU usage on both Web and Midori. The high usage doesn't occur immediately.

The nice thing is that like Midori, Web has caret browsing (which is off by default) whereas Chrome stubbornly refuses to provide it.

---

### Post by qamelian on 2012-09-10
> **vasa1 said:**
> Please try it on the sites I mentioned. I've had the issue of high CPU usage on both Web and Midori. The high usage doesn't occur immediately.
I'll check them out when I get home from work tonight. I haven't experienced high CPU usage on any of the sites I visit regularly, but I don't often visit the ones you've mentioned, so I'll give it a go!

The only browser(s) I've ever had this problem with is Chrome/Chromium.

---

### Post by vasa1 on 2012-09-10
> **qamelian said:**
> I'll check them out when I get home from work tonight. I haven't experienced high CPU usage on any of the sites I visit regularly, but I don't often visit the ones you've mentioned, so I'll give it a go!

The only browser(s) I've ever had this problem with is Chrome/Chromium.
Thanks! My experience has been that Midori and Web gag on the same pages whereas Chrome, Firefox, Opera and Seamonkey do okay.

And do share if you figure out how to watch YouTube's non-HTML5 content.

---

### Post by qamelian on 2012-09-10
> **vasa1 said:**
> Thanks! My experience has been that Midori and Web gag on the same pages whereas Chrome, Firefox, Opera and Seamonkey do okay.

And do share if you figure out how to watch YouTube's non-HTML5 content.
will do! :)

---

### Post by vasa1 on 2012-09-10
One thing I don't get is that the horizontal space to the right of "Web" isn't being utilized at all.
I wonder why they can't move "Web" down to the left of < >.

---

### Post by vasa1 on 2012-09-10
Any feedback on the **epiphany extensions** will be welcome as well! I've just installed them from the USC and will try a few out tomorrow.

In particular, I want to know if the "adblock" can handle exceptions. Sometime ago, Midori's adblock couldn't. I don't know if things are different for Midori now because it was on the dev's to-do list.

---

### Post by coldjeanz on 2012-09-10
It's way too basic. 

I see absolutely no reason to use anything other than Chrome/Chromium or Firefox. 

Midori, Epiphany, Qupzilla...all nice looking browsers but they lack way too many features to be usable browsers. Without smooth scrolling I find web browsing an impossible task and none of those browsers currently support it. Flash is also a pain in the *** since none of those support it very well. Qupzilla is probably the best out of those three, but it still has problems with Flash.

---

### Post by qamelian on 2012-09-10
> **vasa1 said:**
> One thing I don't get is that the horizontal space to the right of "Web" isn't being utilized at all.
I wonder why they can't move "Web" down to the left of < >.

You seem to get something different from me here. On my machine, Web appears at the very top of the screen next to Activities and uses no extra space.

---

### Post by qamelian on 2012-09-10
> **vasa1 said:**
> Please try it on the sites I mentioned. I've had the issue of high CPU usage on both Web and Midori. The high usage doesn't occur immediately.

The nice thing is that like Midori, Web has caret browsing (which is off by default) whereas Chrome stubbornly refuses to provide it.

For the last 40 or so minutes, I've had both the sites you mention open, plus iGoogle, Facebook, and Ubuntu Forums at the same time in different tabs. Epiphany is idling at about 4-5.5 % CPU, but it does briefly spike to 18-20% periodically when new activity registers on Ask Ubuntu and/or Super User. This doesn't seem particularly high to me when I compare it to what I see in Firefox or Chrome/Chromium.

---

### Post by qamelian on 2012-09-10
> **vasa1 said:**
> Thanks! My experience has been that Midori and Web gag on the same pages whereas Chrome, Firefox, Opera and Seamonkey do okay.

And do share if you figure out how to watch YouTube's non-HTML5 content.

For Flash-only content, we're out of luck at the moment. See this bug report for details:
[https://bugs.launchpad.net/bugs/904505](https://bugs.launchpad.net/bugs/904505)

---

### Post by vasa1 on 2012-09-10
> **qamelian said:**
> For the last 40 or so minutes, I've had both the sites you mention open, plus iGoogle, Facebook, and Ubuntu Forums at the same time in different tabs. Epiphany is idling at about 4-5.5 % CPU, but it does briefly spike to 18-20% periodically when new activity registers on Ask Ubuntu and/or Super User. This doesn't seem particularly high to me when I compare it to what I see in Firefox or Chrome/Chromium.

Did you actively view content on those sites? In others words, did you click on questions and view the answers or did you just have the tabs open while viewing other pages. I have both askubuntu and superuser open right now without problems for about 15 min but these tabs aren't active in the browser. By that I mean I've opened them in the background and left them there. I do see the number of "newest questions" increasing in the browser's tab text.

My feeling is that you may see the CPU usage rise if you view content and navigate those sites' pages. **I wouldn't leave the computer unattended while doing that**. 

([SIZE="1"]Now I need to get rid of those animated smilies to the right of the reply text box[/SIZE].)

---

### Post by vasa1 on 2012-09-10
> **qamelian said:**
> You seem to get something different from me here. On my machine, Web appears at the very top of the screen next to Activities and uses no extra space.
Thanks for looking into that :)
I'm on 12.04. Plus I'm running Xfce 4.10 and not GNOME. So I guess I should accept that there will be differences and that non-GNOME environments may not get the best out of Web.

---

### Post by claracc on 2012-09-11
Using epiphany browser 3.4.1 in both my laptops:

hp compaq 6720s ubuntu 12.04, desktop gnome fallback

pentium III, 1 GHz CPU, lubuntu 12.04

Working well, no as well ( quick, responsive and low resources consumption) as gecko version ( very long time ago), but completely usable, being a certain alternative for firefox in my old pIII laptop.

Using nspluginrapper to see flash videos and I can also see java applets (using oracle java)

Blocking ads, tab's state, greasymonkey scripts, HTML5Tube, all of them working, except HTML5 which exhaust resources in my old pIII.

The only thing I miss, is to change automatically to new tab.

I attached an image of my desktop where you can see 4 tabs openned (askubuntu and superuser among them), and CPU consumption is on average 3%, memory usage 6 %.

---

### Post by vasa1 on 2012-09-11
> **claracc said:**
> Using epiphany browser 3.4.1 in both my laptops:
...
I attached an image of my desktop where you can see 4 tabs opened (askubuntu and superuser among them), and CPU consumption is on average 3%, memory usage 6 %.
@claracc, thanks for your reply :)

I see you have the same blank space that I see to the right of "Web" in the row just below the title bar.

Re. askubuntu and superuser, may I ask if you're signed in? Maybe the problem is seen only after signing up? Even I don't see the very CPU usage all the time, but it definitely happens after a while and I then **have** to close the browser. Just closing the tab isn't enough. I can't relate it to any single event so far.

Re. the adblocking, can you check if you can create an exception rule? I don't seem to be able to do so. I suspect that Web and Midori have a lot in common. Here's some code from a [Midori page]("http://git.xfce.org/apps/midori/tree/extensions/adblock.c#n1198"):
```
     * TODO: @@ is currently ignored by Midori.
```

---

### Post by claracc on 2012-09-11
You are very welcome.

No, I haven't signed in askubuntu or superuser. I'll try when come back of working and post.

No I cannot create an exception rule in adblock, only I can do is to add a preconfigured filters list to block ads (I have easylist)

Attach image of configuring adblock:

---

### Post by qamelian on 2012-09-11
> **vasa1 said:**
> Did you actively view content on those sites? In others words, did you click on questions and view the answers or did you just have the tabs open while viewing other pages. I have both askubuntu and superuser open right now without problems for about 15 min but these tabs aren't active in the browser. By that I mean I've opened them in the background and left them there. I do see the number of "newest questions" increasing in the browser's tab text.

My feeling is that you may see the CPU usage rise if you view content and navigate those sites' pages. **I wouldn't leave the computer unattended while doing that**. 

([SIZE=1]Now I need to get rid of those animated smilies to the right of the reply text box[/SIZE].)
Yes, I viewed about a dozen questions on each site and it didn't make any difference. I only saw the CPU rise when refreshing or updating the page, and it still never went above 20%. I tested for another 90 minutes or so after posting here and still no change.

---

### Post by vasa1 on 2012-09-11
> **qamelian said:**
> Yes, I viewed about a dozen questions on each site and it didn't make any difference. I only saw the CPU rise when refreshing or updating the page, and it still never went above 20%. I tested for another 90 minutes or so after posting here and still no change.
Thanks for looking into this! So it looks that there's something funky going on for just me :(
BTW, if I disable javascript, I don't have the problem!

---

### Post by claracc on 2012-09-11
This afternoon I have been surfing the web with epiphany. Not memory or CPU big consumption observed.

With 6 tabs openned (one of them ask ubuntu), cpu consumption is 12 %, memory usage 12 %. The npviewer program ( to see flash content) can become to take 65 % CPU when watching flash videos.

Watching different questions an answers in askubuntu, don't watching an important increase in CPU usage.

---

### Post by vasa1 on 2012-09-11
> **claracc said:**
> ...
Watching different questions an answers in askubuntu, don't watching an important increase in CPU usage.
Do you have an account and did you log in? Perhaps additional javascripts are running for those who sign in?
Guess the Venn intersection consisting of those who view this thread, use Web and sign into things like Askubuntu or superuser is close to null ;)

---

### Post by vasa1 on 2012-09-12
Okay, I have the problem even without logging in. So it seems it's something about my set-up that I need to fix. I've tried with Midori as well, which is very, very much like Web but maybe a little friendlier. Same story.

---


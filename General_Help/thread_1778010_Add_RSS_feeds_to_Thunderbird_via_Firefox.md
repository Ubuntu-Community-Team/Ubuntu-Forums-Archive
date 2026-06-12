---
title: "Add RSS feeds to Thunderbird via Firefox?"
date: 2011-06-08
forum: General Help
---

### Post by darthpenguin on 2011-06-08
Hey guys, I'm a huge fan of Mozilla Thunderbird and Firefox. I have used Thunderbird to handle all my email accounts and rss feeds on every system I've ever used. One thing that has always bothered me was that Thunderbird never shows as an option on Firefox's "Subscribe to this feed using.." screen. On Windows this is easily fixed by "choosing another program" and pointing to the Thunderbird.exe file. But, common, seriously, wtf? I mean, sure Firefox's "live bookmarks" should be the default reader -- makes perfect sense. But what is all the other junk in that dropdown menu and where the hell is Thunderbird? I don't expect every web browser to connect with Thunderbird but, Mozilla, you guys should really make your stuff compatible with each other. And here is the worst part. On Linux, IT DOESN'T WORK AT ALL. I try to subscribe to a feed, choose another application, point to /usr/share/applications/Thunderbird.desktop and get ... NOTHING. Not even an error message.

If I were using any other web browser I wouldn't think twice about this. "Oh, Opera can't add feeds to Thunderbird? That's fine, why should you expect it to? I'll just copy and paste the url. Done. What's for breakfast?" It's bad enough that Mozilla's top applications do not connect with each other out-of-the-box, what's worse is it can work in WINDOWS! These are OPEN-SOURCE applications Mozilla, you guys LIVE in Linux. Making your stuff available on other platforms is little more than common curtsey. and they work better OVER THERE?! WTF?

If Google Chrome didn't, by default, add feeds to Google Reader wouldn't you think there was something drastically, seriously, wrong? I mean that would be real Twilight Zone $h!t, right? Maybe Chrome doesn't add feeds to Google Reader. I don't know, I've never used it. But if anyone had asked me if Chrome has this feature I'd have said, "Yes, of course, wth kinda question is that?" then put a dunce cap on their head and tell them to sit in the corner until their IQ climbed a point or two. 

Guys, Thunderbird is my only application of choice for email and rss feeds. If I *absolutely must* I'll add feeds manually. But there has simply GOT to be a way to add feeds to Thunderbird from Firefox in one, easy, click. It works on Windows (*face-palm*).

Any ideas? Thank You.

---

### Post by lovinglinux on 2011-06-08
The problem is that you are using the wrong Thunderbird path. The correct is /usr/bin/thunderbird.

For a permanent solution, do this:

[[IMG]http://www4.picturepush.com/photo/a/5841937/640/5841937.png[/IMG]](http://picturepush.com/public/5841937)

When setting the option in the pic, choose "Use other" then find the *thunderbird* executable, using the correct path provided above. This method will be permanent and automatic. No need to choose Thunderbird every time you access a feed url. After doing that, all you need is to click the RSS icon to launch Thunderbird and automatically subscribe to the new feed. To revert that, simply choose "Preview in Firefox". This will revert to the current method that asks what you want to do every time you click a feed.

BTW, this is not a Mozilla board. Complaining about Mozilla products here won't get you anywhere. Additionally, you could have obtained the solution by simply asking "How to open rss feeds from Firefox in Thunderbird?" You would have spared me the trouble of reading all that rant.

---

### Post by darthpenguin on 2011-06-09
I didn't know about changing settings in the Applications tab, thanks. I did know there was a difference between a *.desktop file and the actual binary executable. Of course it's /usr/bin/thunderbird. That is actually very obvious. I feel so stupid. I think I'll be waring the dunce cap. Jeez, I leave Linux for a few months and even the most basic stuff is lost to me. I can't believe I did that. Thank you, lovinglinux

And I do apologize for the rant. This, as you said, is not a Mozilla forum. Complaining about problems will not get us anywhere. We need to work to fix the problems. 

I'm told that Thunderbird may be the default email client in Ubuntu 11.10. First let me say, THAAAAAAANK YOOOUUUUU THANK YOU THANK YOU THANK YOU. Thunderbird is not perfect but it's the only client that doesn't completely suck. So, if Thunderbird is going to ship in Ubuntu by default, let's make it the default rss reader in Firefox (or, at least, an obvious choice). Common, if the Mozilla guys arn't gonna stop smokin' whatevertheF%^# their smokin' then someone has gotta pick up the slack.

---


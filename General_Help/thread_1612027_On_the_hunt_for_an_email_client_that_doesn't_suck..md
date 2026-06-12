---
title: "On the hunt for an email client that doesn't suck..."
date: 2010-11-02
forum: General Help
---

### Post by Roasted on 2010-11-02
There seems to be two apps here that are viable email clients. Thunderbird and Evolution.

My requirements are simple. An email application that easily integrates Google Calendar. LOL! That's it! That's all I want! Really!

Looking onto Ubuntu's help page, I found specific links to each version of Thunderbird with their corresponding add-ons, which to integrate Google Calendar you need the gdata add-on as well as the lightning add-on. Well, lightning adds fine, but their posted version of gdata does not work, noting to me it's an incompatible version. Yet uh... it's what Ubuntu's help topic told me to grab...

Okay fine. So Thunderbird struck out. But then there's Evolution. The fully functional Outlook replacement. It works fantastic. Sure, it crashes quite a bit, it freezes up at random times, often times opening a new email causes it to hesitate for 5-8 seconds as it brings the email down and into view, but it would at least work, and my Google Calendar was always there and easily accessible.

BUT whenever I add things to my calendar, it just grays out and freezes up. Not all of the time. But frequently enough it sends me into a rage. Thunderbird's speed far exceeds Evolution's... but the lack of calendar is really a downer. At one point I had Thunderbird running with Google Calendar. It was great. Then I did an update (I think I had the mozilla PPA activated) and it broke my add-ons, and ever since I can't seem to get it working...

Come on... I'm not asking for much. Or.. am I? Any ideas of alternatives here or perhaps programs that do the job I am looking for? Anything? At all? :(

EDIT - On second thought, perhaps using Google Calendar's Prism for Ubuntu + Thunderbird will just make more sense...

---

### Post by ellgor on 2010-11-03
Hi,

Check out Korganiser, does all the functions you have mentioned.

Regards, Ellgor.

---

### Post by scouser73 on 2010-11-03
Try [[COLOR="Red"]**Zimbra E-mail Client**[/COLOR]]("http://www.zimbra.com/products/desktop.html"), or [[COLOR="red"]**Other Ubuntu E-mail Clients**[/COLOR]]("https://help.ubuntu.com/community/EmailClients")

---

### Post by SgtPepperKSU on 2010-11-03
> **Roasted said:**
> Okay fine. So Thunderbird struck out.

No, the ubuntu help documentation (probably - without a link to the documentation to see it, I can't *rule out* reading comprehension issues) struck out.

Thunderbird + Lightning + Provider for Google Calendar work amazingly well.  You just need to get the right version.  Rather than relying on documentation that can get out of date, just get it from the addon page: [https://addons.mozilla.org/en-US/thunderbird/addon/4631/](https://addons.mozilla.org/en-US/thunderbird/addon/4631/)

---

### Post by Roasted on 2010-11-03
> **SgtPepperKSU said:**
> No, the ubuntu help documentation (probably - without a link to the documentation to see it, I can't *rule out* reading comprehension issues) struck out.

Thunderbird + Lightning + Provider for Google Calendar work amazingly well.  You just need to get the right version.  Rather than relying on documentation that can get out of date, just get it from the addon page: [https://addons.mozilla.org/en-US/thunderbird/addon/4631/](https://addons.mozilla.org/en-US/thunderbird/addon/4631/)

That gives me the error it is incompatible with my version of Thunderbird, which is 3.0.10. Even on the Ubuntu help documentation it specifies for THIS version of Thunderbird, download *this* and *this*, one of those two things is gdata extension, which fails to be compatible.

I'm sorry, but even if this WAS do-able, it's a royal PITA to have a different add-on version for every little version change Thunderbird goes through. 3.0 to 4.0, okay fine. but 3.0.9 to 3.0.10, etc? Really?

That being said... Thunderbird stuck out. :(

---

### Post by Roasted on 2010-11-03
I think part of my problem with Evolution is Google Calendar in itself. Maybe it just doesn't fly that well. Evolution, mail wise, seems to work relatively fine for the most part. Is there any alternatives to online calendars besides Google Calendar that would make sense to use? Maybe if I try another I'll get some better results...


EDIT


Further messing with Evolution has really painted the picture above. I simply cannot get Evolution to act up if I disable my Google Calendar integration. This got me thinking... is there a way I can synchronize a personal calendar on Evolution to Google instead of using my Google Calendar as a "live" copy when running Evolution? That way I can work off of Evolution without headache and when I choose to sync, I hit it, blam it moves up to Google and that's done. That way I wouldn't have to deal with slowness and frequent issues when I'm USING Evolution.

Also - can I do the above, but with Thunderbird?? I'd like to do this at home since I don't use Evolution at home...

---

### Post by jrarrmy on 2010-12-08
Why does evolution even have the google calendar option, it doesn't seem anyone has it working? Where is this SSL option they speak of, it doesn't appear in my menu. Now everything keeps freezing after following their instructions...

---

### Post by philinux on 2010-12-08
> **jrarrmy said:**
> Why does evolution even have the google calendar option, it doesn't seem anyone has it working? Where is this SSL option they speak of, it doesn't appear in my menu. Now everything keeps freezing after following their instructions...


I've got google calendar running in evo. Not had a problem.

New>Calendar>Google.

Real simple. You might have to login at google itself and then logout.

---

### Post by jrarrmy on 2010-12-08
Weird, mine didn't work at all.
It kept freezing every time I tried to do anything.

Just had to reboot, pick a calendar from the retrieve list, and then sign into gmail -> calendar in a browser...

So far no more errors.
Thanks

---

### Post by Megaptera on 2010-12-08
Have you looked at runing Gmail through Prism along with Google calendar through Prism? All are in repos.Prism is an application that lets users split web applications out of their browser and run them directly on their desktop.

Like it's done in linux Peppermint Ice [http://peppermintos.com/2010/07/peppermint-ice-faster-lighter-aiming-for-the-clouds/](http://peppermintos.com/2010/07/peppermint-ice-faster-lighter-aiming-for-the-clouds/)

---

### Post by brookie on 2010-12-08
+1 for this > **SgtPepperKSU said:**
> 
Thunderbird + Lightning + Provider for Google Calendar work amazingly well.  You just need to get the right version.  Rather than relying on documentation that can get out of date, just get it from the addon page: [https://addons.mozilla.org/en-US/thunderbird/addon/4631/](https://addons.mozilla.org/en-US/thunderbird/addon/4631/)...with one exception. 

You need to get the latest version of Thunderbird (now 3.1.6) for the addons to be compatible. Regular ubuntu repos don't offer the latest versions of TB in a timely fashion so by adding a 3rd party ppa you can get it.

I would completely remove any previous versions of TB, including the TB profile in your home directory before installing a new version.

There are a few ppa's that offer the current TB. I use [Roberto's]("https://launchpad.net/%7Eferramroberto/+archive/thunderbird"), but you can use Ubuntzilla, or search for others.

It's simple and it works. Remember to only add ppa's from trusted sources or inquire on the forums about them, or ask the developer himself about their ppa. 

Anyhow, hope this helps and you can get your email on. 

Cheers, 
brook

---

### Post by jrarrmy on 2010-12-08
Both of those sound complicated, good ideas though. 

I'm trying to stick with best compatibility due to syncing on many platforms for now. I was scared to make the switch from thunderbird to evolution but things seem okay now... hopefully.

---


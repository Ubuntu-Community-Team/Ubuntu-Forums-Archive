---
title: "Official Mozilla build performance&gt;Ubuntu Firefox build [not the usual FF thread]"
date: 2009-07-12
forum: General Help
---

### Post by Andy06 on 2009-07-12
This thread has nothing to do with how to update, install etc.

With the new Ubuntu build of Firefox, I am having trouble with some very common and popular websites:

1.The facebook chat does not work anymore. [pop out chat might still function but the integrated pop-in feature does not]

2.Hotmail has issues, there are rendering and misalignment problems (for example the sign out below the name area). Also while typing a new email, the rich text options are not accessible and the font size and type cannot be changed. Furthermore, the font in the inbox for unread messages is exceptionally bold.

However, FFv3.5 is perfect in windows (also in terms of all round performance and UI snappiness), so I downloaded the OFFICIAL Mozilla tar.gz package and unzipped it, tried it out and as I expected, it works perfectly with none of the problems above.

So what does the ubuntu build change that breaks it? And that too for two of the most popular websites, both of which would easily be in the list of top 10 websites worldwide. I haven't tested others such as Yahoo extensively but it seems it occurs wherever heavy javascript, ajax etc are used.

I thought the Ubuntu build has minimal modifications to change a few settings and integrate it with the package management system but it would seem the changes go beyond that, but why?

Just for knowledge, is the Ubuntu firefox team a team of Ubuntu people working on Firefox or a team of Firefox people trying to adjust it for Ubuntu?

---

### Post by kartiksinghal on 2009-07-13
Another problem that I am facing with Shiretoko:

Some pictures are rendered incorrectly, mainly a lot of png and jpg files are displayed in grayscale instead of in color.

---

### Post by Andy06 on 2009-07-13
Try going to the Firefox website, download the Linux tar.gz package and then unzip it somewhere. It will unzip to a firefox folder in the directory where the tar.gz package is located. Then go into this folder and run firefox by double clicking on the "firefox" file. Run through your tests and see if there is a difference.

I have differences in mine for fonts, speed, flash performance and page rendering and compatibility. 

BTW, I think FF3.5 uses new colour profiles....which are meant to display pictures better.

---

### Post by renbla on 2009-07-13
Yeah, FF 3.5 works perfectly for me :guitar:

---

### Post by Andy06 on 2009-07-13
Ummm....which ones, the "official" Mozilla one or the "official" Ubuntu one or some other one in between?

---

### Post by Andy06 on 2009-07-13
Ok here is the solution,

Go to about:config,

filter:           general.useragent.extra.firefox
Value (Default):  Shiretoko/3.5
Value (Modified): Firefox/3.5

Apparently, the ubuntu team did not change the user agent (or couldn't because of branding?), the ubuntu build also has a different about:config config than the stock vanilla build, most of the web has no idea what is looking at them, so they render incorrectly..........

---

### Post by philinux on 2009-07-13
This is odd as I'm not seeing any problems with the sites I visit except they load faster.

---

### Post by Andy06 on 2009-07-13
How did you install your FFv3.5 and what is your user agent?
And are you talking about sites in general or the specific ones I mentioned?

Largely, you shouldn't have any problems even with the affected build on regular sites like [www.google.com](www.google.com), which is well......not that hard to render. Even on affected sites, the issues can often be small and negligible but they're there. On facebook and hotmail though, there were entire categories of functionality missing. Then again, there really is no OFFICIAL OFFICIAL 3.5 for 9.04, the version in the repos is not part of the Main repository and there is a disclaimer that says Canonical will provide no updates.

---

### Post by philinux on 2009-07-13
> **Andy06 said:**
> How did you install your FFv3.5 and what is your user agent?
And are you talking about sites in general or the specific ones I mentioned?

Largely, you shouldn't have any problems even with the affected build on regular sites like [www.google.com](www.google.com), which is well......not that hard to render. Even on affected sites, the issues can often be small and negligible but they're there. On facebook and hotmail though, there were entire categories of functionality missing. Then again, there really is no OFFICIAL OFFICIAL 3.5 for 9.04, the version in the repos is not part of the Main repository and there is a disclaimer that says Canonical will provide no updates.

Well I temporarily enabled to proposed repos. This upgraded 3.5 beta to 3.5. The user agent is:- see screenshot. By the way I did not do a user set to firefox for the general one. Also you can see my bookmarks bar and I use youtube. Hotmail looks fine too.

---

### Post by Andy06 on 2009-07-13
Your User agent is Shiretoko, you should be having the same problems, I've checked over 20 computers now, so unless you have tweaked something or an extension has tweaked settings, there should be no difference.

Have you checked those sites? Can you post a screenshot.

Thanks

---

### Post by philinux on 2009-07-13
Ok lets test this then. By the way I've not tweaked anything.

I dont use facebook but if you give me some sites to test we can compare them.

---

### Post by vinutux on 2009-07-13
Shiretoko works fine for me but official tar.gz is not dictected my internet connection don't know Y

---

### Post by Andy06 on 2009-07-13
Okay, post a screenshot of your hotmail inbox. You can shade the touchy bits :D
Also post it while showing your empty trash or the today page so you don't have to shade much.

---

### Post by Andy06 on 2009-07-13
Vinu, 
See lovinglinux's thread to troubleshoot your issues. Try disabling ipv6 as well.

---

### Post by lovinglinux on 2009-07-14
> **kartiksinghal said:**
> Another problem that I am facing with Shiretoko:

Some pictures are rendered incorrectly, mainly a lot of png and jpg files are displayed in grayscale instead of in color.

See **Solution** [*[COLOR="Red"]**FOT007**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT007).

> **vinutux said:**
> Shiretoko works fine for me but official tar.gz is not dictected my internet connection don't know Y

See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).



@Andy06

Sorry. I totally forgot to reply after spending a few hour creating the new script on the tutorial.

As you know, I'm using a compiled version of Mozilla's official build and it works like a charm. 

> **Andy06 said:**
> 1.The facebook chat does not work anymore. [pop out chat might still function but the integrated pop-in feature does not

Well, I don't use Facebook, so I can't comment on that.

> **Andy06 said:**
> 2.Hotmail has issues, there are rendering and misalignment problems (for example the sign out below the name area). Also while typing a new email, the rich text options are not accessible and the font size and type cannot be changed. Furthermore, the font in the inbox for unread messages is exceptionally bold.

I have the same misalignment, but if you didn't ask I would even notice it. What bothers me in Firefox Linux since I started to use it, it's that Microsoft Live doesn't remember my password and when I try to use the [Secure Login](https://addons.mozilla.org/en-US/firefox/addon/4429) extension, it doesn't recognizes the login forms. But I'm not sure if this is the fault of Ubuntu, Firefox, Windows Live or some extension blocking something.

I will make some additional tests using Shiretoko.

> **Andy06 said:**
> So what does the ubuntu build change that breaks it? And that too for two of the most popular websites, both of which would easily be in the list of top 10 websites worldwide. I haven't tested others such as Yahoo extensively but it seems it occurs wherever heavy javascript, ajax etc are used.

Javascript has been a problem for me on some websites since I started to use Linux (Ubuntu). Usually I don't have issues with layout or functionality, but some sites eat CPU like that little green monster from Ghostbusters movie.

Nerverthelss, I had a problem with java panoramic images that seems to be fix now.

> **Andy06 said:**
> Just for knowledge, is the Ubuntu firefox team a team of Ubuntu people working on Firefox or a team of Firefox people trying to adjust it for Ubuntu?

Where did you find that? I know about Ubuntu Mozilla Team. I guess they are just developers or community members working to make Mozilla applications more compatible with the Ubuntu desktop. I don't think they work for Mozilla.

> **Andy06 said:**
> I have differences in mine for fonts, speed, flash performance and page rendering and compatibility.

I haven't experienced differences in performance, flash or fonts. The only difference I could perceive was in regard to page loading times and download speed, but when comparing the default builds and Swiftfox or my compiled build. Nevertheless, it could be just a oscillation on my broadband service (some days it sucks).

---

### Post by lovinglinux on 2009-07-14
Just a heads up...

It seems to be a MIcrosoft or Ubuntu thing.

The "remember my password" on Windows Livw doesn't work on Firefox and Opera. The misalignment too. See screenshots.

---

### Post by Andy06 on 2009-07-14
No wonder you thought the misalignment was a small issue, you hardly have any at all :D

Check out mine. Compared to yours, mine is in a different postcode. Also notice the mispositioned Windows Live logo on the top left. I think we are comparing different builds. Mine is Shiretoko 3.5 from the repos, that's the one with issues.

I also notice you used Opera 10 Beta, I'm using the same, but it doesn't give any major problem, in fact no major browsers do, not even 'Mozilla's' Firefox, only Ubuntu Firefox does.

> I haven't experienced differences in performance, flash or fonts.

You had font troubles (wiry fonts) on some FFs right? You mentioned in the other thread. All problem in this thread I'm talking about are of Ubuntu Firefox (Shiretoko 3.5), other FFs are fine (Mozilla tar.gz, Mozilla manual install, Ubuntuzilla, Swiftfox). 

> What bothers me in Firefox Linux since I started to use it, it's that Microsoft Live doesn't remember my password

If you are talking about FFs own password manager and not the "Remember me" Hotmail option, then that is not a bug, that is actually a security feature implemented by Windows Live (and also Yahoo but not Gmail or Facebook) that has the autocomplete=off tag in the page source (you can Ctrl+U) and view it.

> Where did you find that? I know about Ubuntu Mozilla Team. I guess they are just developers or community members working to make Mozilla applications more compatible with the Ubuntu desktop. I don't think they work for Mozilla.

Din't understand :). Find what? I don't know, I was asking.

Everyone,
Pls post you exact build/source and user agent so we can be sure you are not using one of the many other builds. This is for problems with Shiretoko 3.5 from the 'official' repos.

---

### Post by Andy06 on 2009-07-14
Ok am on Windows now. You actually don't have a misalignment problem. That's the way it should be, which figures since you are using an official build compiled yourself.

Different browsers in Windows are handling it in different ways in Windows but IE8 itself handles it very much like your screenshot.

The "Remember my password" Checkbox isn't working at all in any of the browsers in windows either, not even IE8, so its Windows Live Hotmail problem, again not with your firefox. You should be very happy with your perfectly functioning 30% faster build :D

There is also a Windows Live sign in assitant, perhaps that is involved somehow.

But why rely on the remember my password? use FFs own password manager or extensions like secure login, lastpass or roboform.
There are bookmarklets, nsloginmanager.js tweaks and userscripts to get around the autocompelete=off tag.

---

### Post by vinutux on 2009-07-14
> **Andy06 said:**
> Ok am on Windows now. You actually don't have a misalignment problem. That's the way it should be, which figures since you are using an official build compiled yourself.

Different browsers in Windows are handling it in different ways in Windows but IE8 itself handles it very much like your screenshot.

The "Remember my password" Checkbox isn't working at all in any of the browsers in windows either, not even IE8, so its Windows Live Hotmail problem, again not with your firefox. You should be very happy with your perfectly functioning 30% faster build :D

There is also a Windows Live sign in assitant, perhaps that is involved somehow.

But why rely on the remember my password? use FFs own password manager or extensions like secure login, lastpass or roboform.
There are bookmarklets, nsloginmanager.js tweaks and userscripts to get around the autocompelete=off tag.


Ok plz mark thead SOLVED

---

### Post by lovinglinux on 2009-07-14
> **Andy06 said:**
> No wonder you thought the misalignment was a small issue, you hardly have any at all :D

Check out mine. Compared to yours, mine is in a different postcode. Also notice the mispositioned Windows Live logo on the top left. I think we are comparing different builds. Mine is Shiretoko 3.5 from the repos, that's the one with issues.

Oh, yes. You problem is worse than mine, but I have the same layout with Shiretoko or any other builds.

> **Andy06 said:**
> I also notice you used Opera 10 Beta, I'm using the same, but it doesn't give any major problem, in fact no major browsers do, not even 'Mozilla's' Firefox, only Ubuntu Firefox does.

Weird. Did you use a PPA?

> **Andy06 said:**
> You had font troubles (wiry fonts) on some FFs right? You mentioned in the other thread. All problem in this thread I'm talking about are of Ubuntu Firefox (Shiretoko 3.5), other FFs are fine (Mozilla tar.gz, Mozilla manual install, Ubuntuzilla, Swiftfox). 

Yes I have the font issue, but across all builds. They all look the same, including Shiretoko.

> **Andy06 said:**
> If you are talking about FFs own password manager and not the "Remember me" Hotmail option, then that is not a bug, that is actually a security feature implemented by Windows Live (and also Yahoo but not Gmail or Facebook) that has the autocomplete=off tag in the page source (you can Ctrl+U) and view it.

I hate those, because Secure Login cannot detect the form fields, so I have to open revelation manager and get the password to log in. I don't really care if the site remembers my password or not, actually I usually don't use this feature. The real problem is with the password manager.

> **Andy06 said:**
> Ok am on Windows now. You actually don't have a misalignment problem. That's the way it should be, which figures since you are using an official build compiled yourself.

Different browsers in Windows are handling it in different ways in Windows but IE8 itself handles it very much like your screenshot.

So I guess the problem is in your Shiretoko. Have you tried to re-install it? I don't think it will help, but who knows...

> **Andy06 said:**
> Ok am on Windows now. You actually don't have a misalignment problem. That's the way it should be, which figures since you are using an official build compiled yourself.

Different browsers in Windows are handling it in different ways in Windows but IE8 itself handles it very much like your screenshot.

The "Remember my password" Checkbox isn't working at all in any of the browsers in windows either, not even IE8, so its Windows Live Hotmail problem, again not with your firefox. You should be very happy with your perfectly functioning 30% faster build :D

There is also a Windows Live sign in assitant, perhaps that is involved somehow.

But why rely on the remember my password? use FFs own password manager or extensions like secure login, lastpass or roboform.
There are bookmarklets, nsloginmanager.js tweaks and userscripts to get around the autocompelete=off tag.

I use [Secure Login](https://addons.mozilla.org/en-US/firefox/addon/4429), but it doesn't recognize the forms. It's not a big issue tho, because I rarely enters hotmail or Yahoo. I forward Yahoo messages to GMail and I use Hotmail for "spam attractor beam" site registrations.

---

### Post by lovinglinux on 2009-07-14
> **vinutux said:**
> Ok plz mark thead SOLVED

As far as I see, is not solved. I don't have issues, but the OP still does.

---

### Post by Andy06 on 2009-07-14
> Ok plz mark thead SOLVED 

Yeah I still have issues :P
I mean I found a workaround. But that's just it, a workaround, there are sustained issues with Ubuntu's firefox builds behaving slightly different to the stock Mozilla builds. *Sometimes* this isn't a good thing.

The workaround was suggested by someone at Mozillazine forums and people there don't take too kindly to suggestions that there is something going wrong with "Firefox" when you are actually talking about a third party build such as the official Ubuntu Firefox. I guess this sort of explain why Mozilla became so adamant about protecting their branding and there was that big issue with it. I dare say that I see their position as being justified, after all, they still offer the entire source code and everything minus the artwork and name to make your own builds (such as Ubuntu's Firefox, Iceweasel, Abrowser, Swiftfox and many more based on their engine).

> Weird. Did you use a PPA?

For Opera or for Shiretoko? Opera 10 beta I installed from a .deb from the opera website whereas Shiretoko is from the repos.
Anyway like I said, there is no misalignment in your screen, a lot of browsers even on windows render it that way. So Opera isn't malfunctioning.

> Yes I have the font issue, but across all builds. They all look the same, including Shiretoko.

I am seeing wiry fonts in most FFv3.5s but only wiry fonts in text entry boxes on Shiretoko, however this is limited to my system and not the 2 dozen or so others I have access to which are displaying the other issues with Shiretoko.

> So I guess the problem is in your Shiretoko. Have you tried to re-install it? I don't think it will help, but who knows...

Did, din't help. The issues are on more than 20 computers, so it can't be just me. Perhaps people don't mind and are not noticing the small errors?

All of this can be solved by switching the user agent to Firefox and then the problem can be recreated by switching it back to Shiretoko. Upon entering the useragent filter in about:config, you can see the custom Ubuntu entries.

---


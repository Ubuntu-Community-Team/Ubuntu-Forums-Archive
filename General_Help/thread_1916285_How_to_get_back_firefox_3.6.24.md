---
title: "How to get back firefox 3.6.24?"
date: 2012-01-27
forum: General Help
---

### Post by l07 on 2012-01-27
Just ran aptitude dist-upgrade, which upgraded firefox to 9. I want 3.6.24, but trying to force version of "firefox" package in synaptic doesn't work. Upon reloading (since apply is greyed out) it says:
```
ould not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

E: Unable to correct problems, you have held broken packages.
E: Unable to lock the list directory


```So nothing changes.

It was suggested:
> **rsvancara said:**
> You could just download the version you want  from mozilla.org into your home directory, say into  /home/someuser/software/Firefox_xyz and then run:

```
sudo mv /usr/bin/firefox /usr/bin/firefox_orig
sudo ln -s /home/someusers/software/Firefox_xyz/bin/firefox  /usr/bin/firefox
```Then you only update your local version when you  want too. but this requires me to look for security updates manually, which I want to take place automatically. I just want the version to stay at 3.6.

---

### Post by snowpine on 2012-01-27
> **l07 said:**
> but this requires me to look for security updates manually

Firefox 9 **is** a security update. :)

---

### Post by l07 on 2012-01-27
I only want the updates to 3.6.

---

### Post by snowpine on 2012-01-27
> **l07 said:**
> I only want the updates to 3.6.

Canonical will not be providing any more updates to 3.6.

---

### Post by l07 on 2012-01-27
Ok, then how do I get the latest 3.6 ubuntu package and freeze upgrades on it?
Also, I would like to know how to properly install 3.6.25 from tar.bz from mozilla.

Both of the above alternatives are useful: the 3.6.24 is configured specifically for ubuntu, it should have apparmor profile configured for it. 3.6.25 is an update. However the difference between the two isn't so major, so the apparmor will still work with .25, I just need to know if it will work on its own or do I need to configure something if I install from tar.bz. I don't know all the ways the firefox is embedded in the system, that's why I need specific instructions on how to configure .25 to be maximally compatible with ubuntu, just as 3.6.24 is. I suppose I'm not deciding on either one because I'm not confident that installing from tar.bz makes full use of the system, so I need reassurance in this area.

---

### Post by lovinglinux on 2012-01-28
Firefox 3.6 will reach end-of-life on April 24th. This means there won't be any security updates for that version anymore, not from Mozilla, not from Ubuntu. You need to upgrade top 9.0.1 or you will be running an unsafe browser.

Please specify the reasons why you don't want Firefox 9 and perhaps we can solve the issues and customize it to your liking.

BTW, Firefox 9 is a lot faster than 3.6 and a much better browser.

---

### Post by RJARRRPCGP on 2012-01-28
There's a bug where updating fails with an error about being unable to acquire a lock or something else locking it, at seemingly random, even when applying security updates with a fresh Ubuntu install!

---

### Post by lovinglinux on 2012-01-28
> **RJARRRPCGP said:**
> There's a bug where updating fails with an error about being unable to acquire a lock or something else locking it, at seemingly random, even when applying security updates with a fresh Ubuntu install!

That is because you are executing two package managers at the same time. For instance, if you are trying to update via command-line, you need to close the Software Center.

---

### Post by fixitmanarizona on 2012-01-29
We don't like it because of all the changes, and how extensions don't  work. Change for the sake of change is not a good idea for users. Having  such frequent version changes, some of which go out of support before  people even download them is a poor idea.
Keeping up with Chrome, and making Firefox look and act like Chrome, is also a poor idea.
If we wanted Chrome, we'd use it and drop Firefox like a hot potato if  it did what we wanted it to do, and Firefox had evolved in a different  direction than it did.
Blending all these so that you don't have a choice isn't what the open source community is about.
Fortunately, Linux users are mostly open to new software and frequent  changes. Also, I've noticed, that on Linux, the latest Firefox browser  is at least usable, and less changes have been made than on the Windows  versions.
 The poor Windows users are totally lost with this thing, and those who  want a Chrome-like browser are switching to it, instead. 
The rapid release schedule will be the death of Firefox, as it will go  the way of Netscape (which is still usable and I, for one, still have it  installed.)
On my Windows install I also tried out Lunascape browser which uses all  three of the major browsing engines. It uses the older version of the  engine running Firefox, which is a great idea, as this software can't be  updated as often as Mozilla seems to think people should.
Mozilla has sold out to Google, you can't tell me they  haven't, as most  of their funding now comes from the giant corporation. This is NOT what  the foundations goals ever were, or should be.

---

### Post by d_venomous on 2012-02-09
"Please specify the reasons why you don't want Firefox 9 and perhaps we can solve the issues and customize it to your liking."

 
How's this?  I have what most people here would consider to be an unusual color scheme - whereas most folks would see black text on a white background, I (because my eyes are extremely light-sensitive) prefer white (actually, light cyan) text on a black background.  And I had configured FF to display in these colors, including link information (when you mouse over a link) and also pop-ups.

Starting with version 4.0, FF took this link information - and took the popup messages - and insisted on displaying them in white-on-black, no matter what my color scheme is.

You guys here on the forum may think that minutiae, but to me, it's effin' _ugly_.  I want the _entire_ browser to fit my color scheme, not just the parts that FF feels like matching.

 
"BTW, Firefox 9 is a lot faster than 3.6 and a much better browser."


In addition, I'm a PC tech for a very large city, and FF 9.0 broke the links in our ticketing system.  Click on 'em as much as the day is long - the browser just sits there and looks at you funny.  And I won't _even_ try 10.0, for fear of what else it might break.

Lemme know if you need screen shots - I can show you what I'm talking about.  (I have 10.0 on another Ubuntu machine, and it seems to run okay, but I still don't like not being able to customize the whole color scheme.)

---

### Post by lovinglinux on 2012-02-10
> **d_venomous said:**
> "Please specify the reasons why you don't want Firefox 9 and perhaps we can solve the issues and customize it to your liking."

 
How's this?  I have what most people here would consider to be an unusual color scheme - whereas most folks would see black text on a white background, I (because my eyes are extremely light-sensitive) prefer white (actually, light cyan) text on a black background.  And I had configured FF to display in these colors, including link information (when you mouse over a link) and also pop-ups.

Starting with version 4.0, FF took this link information - and took the popup messages - and insisted on displaying them in white-on-black, no matter what my color scheme is.

You guys here on the forum may think that minutiae, but to me, it's effin' _ugly_.  I want the _entire_ browser to fit my color scheme, not just the parts that FF feels like matching.

 
"BTW, Firefox 9 is a lot faster than 3.6 and a much better browser."


In addition, I'm a PC tech for a very large city, and FF 9.0 broke the links in our ticketing system.  Click on 'em as much as the day is long - the browser just sits there and looks at you funny.  And I won't _even_ try 10.0, for fear of what else it might break.

Lemme know if you need screen shots - I can show you what I'm talking about.  (I have 10.0 on another Ubuntu machine, and it seems to run okay, but I still don't like not being able to customize the whole color scheme.)


Have you tried a different theme? There are many dark themes on Mozilla site. You can probably find some stylesheet for Stylish extension to match your theme.

Please post a picture of which elements you want dark and I can try to make a stylsheet for them.

---

### Post by d_venomous on 2012-02-11
"Have you tried a different theme? There are many dark themes on Mozilla site. You can probably find some stylesheet for Stylish extension to match your theme."

Perhaps, but I tend to favor mine.  I've had it for many years; it's a custom jobber I brought over from my Windoze installations.  It employs favorite colors with a dark scheme that's easier on my eyes.

"Please post a picture of which elements you want dark and I can try to make a stylsheet for them."

Here you go (hopefully, I'm able to attach it where you can see it).  Note the overall appearance, contrasted with the white confirmation pop-up, plus link info (in the lower left corner) corresponding to the sidebar link over which I have my mouse hovering.

In 3.6.25, these areas blended in as part of my customized color scheme.  Beginning with version 4.0, this is how they appear now.  Like I said previously, you (and everyone else here) may consider it trivial, but it ruins the Firefox look for me, and doesn't make me want to upgrade.

Any help you can provide is gratefully received, and thanks in advance.


[IMG]http://www.spatulacitybbs.net/stuff/Screenshot.png[/IMG]
[IMG]http://www.spatulacitybbs.net/stuff/Screenshot.png[/IMG]

---

### Post by d_venomous on 2012-02-11
> **lovinglinux said:**
> Have you tried a different theme? There are many dark themes on Mozilla site. You can probably find some stylesheet for Stylish extension to match your theme.

Actually, after I posted my response & screenshot, I did just that - went & looked at some themes, and even tried out a couple.

And seeing as my particular issue appeared to be fixed inside those themes, that got me to thinking:  My problem areas look like they might be elements that are configurable, perhaps using the about:config sub-module.

Is that, in fact, the case - and if so, what are those element names?  If I can get that info from you, I can probably go fix this myself, spare you guys the hassle, and get out of y'all's hair about it.

Please advise, and again - thanks in advance.

---

### Post by lovinglinux on 2012-02-11
> **d_venomous said:**
> "Have you tried a different theme? There are many dark themes on Mozilla site. You can probably find some stylesheet for Stylish extension to match your theme."

Perhaps, but I tend to favor mine.  I've had it for many years; it's a custom jobber I brought over from my Windoze installations.  It employs favorite colors with a dark scheme that's easier on my eyes.

"Please post a picture of which elements you want dark and I can try to make a stylsheet for them."

Here you go (hopefully, I'm able to attach it where you can see it).  Note the overall appearance, contrasted with the white confirmation pop-up, plus link info (in the lower left corner) corresponding to the sidebar link over which I have my mouse hovering.

In 3.6.25, these areas blended in as part of my customized color scheme.  Beginning with version 4.0, this is how they appear now.  Like I said previously, you (and everyone else here) may consider it trivial, but it ruins the Firefox look for me, and doesn't make me want to upgrade.

Any help you can provide is gratefully received, and thanks in advance.


[IMG]http://www.spatulacitybbs.net/stuff/Screenshot.png[/IMG]
[IMG]http://www.spatulacitybbs.net/stuff/Screenshot.png[/IMG]


I couldn't reproduce that dialog here. I am not sure why, because I remember seeing a similar alert dialog in the past. What happens here is that I get the old style dialog, with correct colors. Since I am using gnome 3 instead of Unity I also tested on Unity.

Perhaps you could try to disable Ubuntu Firefox Modifications extension and see if you get the old dialog. I suspect it could be a Ubuntu feature and not a Firefox feature.

BTW, Firefox doesn't have an option to prevent bookmark deletion. I suspect you are using an extension for that. So it could also be an issue with the extension.

If that doesn't help, create a new profile with the profile manager:

```
firefox -P
```

Then install [NASA theme](https://addons.mozilla.org/pt-br/firefox/addon/nasa-night-launch/) and test it. Let me know if the problem also occurs with that theme. This is just a test, to see if your theme is the culprit.

---

### Post by lovinglinux on 2012-02-11
> **d_venomous said:**
> Actually, after I posted my response & screenshot, I did just that - went & looked at some themes, and even tried out a couple.

And seeing as my particular issue appeared to be fixed inside those themes, that got me to thinking:  My problem areas look like they might be elements that are configurable, perhaps using the about:config sub-module.

Is that, in fact, the case - and if so, what are those element names?  If I can get that info from you, I can probably go fix this myself, spare you guys the hassle, and get out of y'all's hair about it.

Please advise, and again - thanks in advance.

You need to use DOMInspector extension to find out the ID of the dialog and then create a rule for Stylish or userChrome. I could do it for you, but I can't reproduce that dialog. My advice would be to find another theme, one that is updated. Keeping old themes can cause other issues.

---

### Post by d_venomous on 2012-02-15
> **lovinglinux said:**
> You need to use DOMInspector extension to find out the ID of the dialog and then create a rule for Stylish or userChrome. I could do it for you, but I can't reproduce that dialog. My advice would be to find another theme, one that is updated. Keeping old themes can cause other issues.

Hmmm.  After re-reading the thread, I tend to think I may have not (read:  probably wasn't) been clear on a couple things.

I'm not using a theme, per se, save for the default created by FF.  The color scheme comes from the one I've installed in Ubuntu, plus the custom colors within FF itself (Edit > Preference > Content > Color).

I do note that these two elements look different in various themes from the way I have them in.  Would DOMInspector tell me the names of at least one of those elements, then?  Or, alternatively, is this something that could be configured in about:config?

Appreciate your help to this point very muchly.   Even if I don't eventually get FF to look the way I want it to, the learning experience is invaluable.

---

### Post by lovinglinux on 2012-02-20
> **d_venomous said:**
> Hmmm.  After re-reading the thread, I tend to think I may have not (read:  probably wasn't) been clear on a couple things.

I'm not using a theme, per se, save for the default created by FF.  The color scheme comes from the one I've installed in Ubuntu, plus the custom colors within FF itself (Edit > Preference > Content > Color).

I do note that these two elements look different in various themes from the way I have them in.  Would DOMInspector tell me the names of at least one of those elements, then?  Or, alternatively, is this something that could be configured in about:config?

Appreciate your help to this point very muchly.   Even if I don't eventually get FF to look the way I want it to, the learning experience is invaluable.

DOMInspector would tell you the ID of those elements. 

There isn't any option in about:config to control what you want.

---

### Post by d_venomous on 2012-02-25
> **lovinglinux said:**
> DOMInspector would tell you the ID of those elements. 

There isn't any option in about:config to control what you want.


Perhaps I'll get to use it at some point.

However, since my last message to you, two things have happened:  1) my workload has increased to the point where I no longer have time to worry about this, and 2) Mozilla came out with 3.6.27.  So I just said "screw it", did an apt-get purge on firefox and manually installed 3.6.27.

Not that that solution comes problem-free - the stable Flash release won't work on it  now, forcing me to run with an unstable beta, which makes YouTube look like crap (everything's pretty much in blue) - but at least it works.

Thank you again for all your help & efforts.  Learned quite a bit from this.

---

### Post by l07 on 2012-03-17
There are multiple reasons for me to use 3.6. Some of which are "all the changes, and how extensions don't work."

While using download from mozilla works, it's not integrated into the system, how do I achieve that? I still don't know what constitutes integration into the system (besides being able to just type firefox and launch the proper application without specifying the full path) because it hasn't been explained here how the ubuntu firefox package differs from mozilla tar.bz and what installation steps it performs.

The concerns I expressed previously and inserted below are still important for me, and I'd like to know the answers to the questions I posed. 3.6.25 below stands for the latest available 3.6 from mozilla, while 3.6.24 stands for that available as an ubuntu package.

How do I get the latest 3.6 ubuntu package and freeze upgrades on it?
Also, I would like to know how to properly install 3.6.25 from tar.bz from mozilla. That is, not just run it, but integrate it into the system as an ubuntu firefox package would be.

Both of the above alternatives are useful: the 3.6.24 is configured specifically for ubuntu, it should have apparmor profile configured for it. 3.6.25 is an update. However the difference between the two isn't so major, so the apparmor will still work with .25, I just need to know if it will work on its own or do I need to configure something if I install from tar.bz. I don't know all the ways the firefox is embedded in the system, that's why I need specific instructions on how to configure .25 to be maximally compatible with ubuntu, just as 3.6.24 is. I suppose I'm not deciding on either one because I'm not confident that installing from tar.bz makes full use of the system, so I need reassurance in this area.

---

### Post by lovinglinux on 2012-03-20
Download the version you want from Mozilla, extract it to your home directory and run these commands:

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s $HOME/firefox/firefox /usr/bin/firefox
```

To revert to the original use this:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
```


You won't get perfect integration. For instance, the Global Menu integration extension won't work. Not much of a problem if you are using Gnome-Shell tho.

Again, I strongly advise you not to do this, because you will be running an unsafe version of Firefox soon.

If your extensions doesn't work, then most likely they are abandoned by the developers, because most extensions under active development are compatible with Firefox above 4. So, is not Mozilla's fault that they don't work anymore.

I am not sure if AppArmor will work with the code above, but I suppose it will, since it relies on the firefox bin path. However I can't be sure, because I don't use AppArmor. Put the firefox profile in complain mode, launch Firefox and check if AppArmor is actually producing entries for Firefox.

---


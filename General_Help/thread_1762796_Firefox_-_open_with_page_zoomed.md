---
title: "Firefox - open with page zoomed"
date: 2011-05-19
forum: General Help
---

### Post by benerivo on 2011-05-19
I like text and graphics large so i've used about:config in Firefox to set both the min and max zoom level at 120%, but want to firefox start using these settings. Once opened i can press ctrl and + to jump to 120% zoom and once i'm there my settings make me stay there no matter what. What i want is for Firefox to open at these settings. Any help aprctd.

---

### Post by lmn. on 2011-05-19
[https://addons.mozilla.org/en-US/firefox/addon/nosquint/](https://addons.mozilla.org/en-US/firefox/addon/nosquint/) ?

---

### Post by benerivo on 2011-05-19
I'm using Firefox 6.0a1 and it's not available for that version. Firefox can do it by itself, but i'm getting slightly tired of pressing Ctrl and + everytime i start it.

---

### Post by benerivo on 2011-05-19
EDIT - this is offered by default by chrone and opera. Firefox does it as well but i just want it to happen when i open it -- rather than having to press a shortcut key.

---

### Post by Larkspur on 2011-05-19
> **benerivo said:**
> EDIT - this is offered by default by chrone and opera. Firefox does it as well but i just want it to happen when i open it -- rather than having to press a shortcut key.

Yes, but you might end up having to zoom out again, because while a certain zoom setting works on one site, it may make another an unreadable mess.  That was my experience with opera's default zoom (you can't set it per site).  Nosquint is the best at this, sad to hear it doesn't work in FF6.  I thought Mozilla was asking add-on devs to bump version compatibility up to 7 to avoid this?  How is FF6, by the way?

---

### Post by benerivo on 2011-05-19
FF6 is fine but i don't use any addons other than adblock, so i can't give much info.

120% zoom is fine for every site i visit, and i just want it to start at that zoom level. The thing is that i've set the minumum zoom to be 120% (in about:config) but it still starts at 100%.

---

### Post by wojox on 2011-05-19
Maybe it's Firefox 6. I just tried in Firefox 4 and it always remembers the different zoom % for each site I set.

---

### Post by lithopsian on 2011-05-19
You can achieve a permanent increase in size by changing the DPI setting for your monitor.  Of course this will affect not just the content in Firefox, but the size of the toolbars, scrollbars etc, and also the size of other applications.

---

### Post by benerivo on 2011-05-19
> **wojox said:**
> nv

What's nv mean?

---

### Post by benerivo on 2011-05-19
> **lithopsian said:**
> You can achieve a permanent increase in size by changing the DPI setting for your monitor.  Of course this will affect not just the content in Firefox, but the size of the toolbars, scrollbars etc, and also the size of other applications.
Thanks, but it's just the text. Text appears small on many websites, and although i can read it, i would like it to be larger. Pressing Ctrl and + is perfect, but would just like Firefox to honour the setting i give it when opening :-)

---

### Post by wojox on 2011-05-19
> **benerivo said:**
> What's nv mean?

nv=nevermind

I just tested it.

---

### Post by benerivo on 2011-05-19
> **wojox said:**
> Maybe it's Firefox 6. I just tried in Firefox 4 and it always remembers the different zoom % for each site I set.

Yeah, i think that works (from my own memory), but i don't want to set it for each site. I want a global default of 120% from startup. I can get 120% set for the whole Firefox session, but only by pressing Ctrl and +, at each startup. This is obviously a minor prob for me, but i have set 120% as a minimum zoom in about:config so just want Firefox to open at that setting.

---

### Post by matey3 on 2011-05-19
I thought firefox latest ver was 4.1 the reason is that I like the 3.x a lot better.4.1 seems to have a more plain look but I like my tools in front of me and not having to go search for them.

---

### Post by benerivo on 2011-05-19
> **matey3 said:**
> I thought firefox latest ver was 4.1 the reason is that I like the 3.x a lot better.4.1 seems to have a more plain look but I like my tools in front of me and not having to go search for them.

I'm not sure about quoting latest version numbers. I'm using [http://nightly.mozilla.org/](http://nightly.mozilla.org/) but my prob is with all versions.

---

### Post by wojox on 2011-05-19
> **benerivo said:**
> Yeah, i think that works (from my own memory), but i don't want to set it for each site. I want a global default of 120% from startup. I can get 120% set for the whole Firefox session, but only by pressing Ctrl and +, at each startup. This is obviously a minor prob for me, but i have set 120% as a minimum zoom in about:config so just want Firefox to open at that setting.

browser.zoom.siteSpecific = false 

That allows zoom level to be consistent from site to site.

---

### Post by benerivo on 2011-05-19
> **wojox said:**
> browser.zoom.siteSpecific = false 

That allows zoom level to be consistent from site to site.

That setting just keeps all pages at 100% (Ctrl+/- doesn't do anything at all)

What i think i'm looking for is a launch command such as...> firefox --zoom=120

---

### Post by Merovius on 2011-05-19
Will this one run on your version?

[https://addons.mozilla.org/en-US/firefox/addon/default-fullzoom-level/](https://addons.mozilla.org/en-US/firefox/addon/default-fullzoom-level/)

Good Luck.

---

### Post by Larkspur on 2011-05-19
If Default Zoom Level doesn't work, try going to Preferences>Content>Fonts & Colours and setting a default text size.  It's not exactly what you're looking for, but it could work.

---

### Post by benerivo on 2011-05-19
> **Merovius said:**
> Will this one run on your version?

[https://addons.mozilla.org/en-US/firefox/addon/default-fullzoom-level/](https://addons.mozilla.org/en-US/firefox/addon/default-fullzoom-level/)

Good Luck.

Unfortunately not :-(

It seems as is the functionality is there by default (no addons required), but i can't get it to enforce the about:config user settings on startup.

---

### Post by benerivo on 2011-05-19
> **Larkspur said:**
> If Default Zoom Level doesn't work, try going to Preferences>Content>Fonts & Colours and setting a default text size.  It's not exactly what you're looking for, but it could work.

That's okay, but a different thing from what i'm looking for. It jumps the text up but not the pics. Any firefox user can press Ctrl and + twice to get the look i want. I'm going to downgrade to an earlier version of Firefox to see if any of the addon suggestions work for me...

---

### Post by mc4man on 2011-05-19
Something seems off you then  - both firefox  and opera should remember the zoom setting when closed and then use that when re-opened
Both do here where I also use 120%,  - have never had to do any editing or whatnot, just set the zoom as desired and close with that setting
Both always open at 120% ( for firefox I just zoom twice which I figure is 120% or so

This includes firefox 6 which I'm using right now..

---

### Post by benerivo on 2011-05-19
> **mc4man said:**
> Something seems off you then  - both firefox  and opera should remember the zoom setting when closed and then use that when re-opened
Both do here where I also use 120%,  - have never had to do any editing or whatnot, just set the zoom as desired and close with that setting
Both always open at 120% ( for firefox I just zoom twice which I figure is 120% or so

This includes firefox 6 which I'm using right now..

How do you set your zoom level?

---

### Post by mc4man on 2011-05-19
I use either the view > zoom twice or Ctrl+ twice.

Myself don't know the inner workings of firefox - do now this has never been an issue here
On this 13" laptop no way can I read most text @100%, have always just set once
(maybe once and a rare while it's gone back to 100%, but I mean rare

Hopefully someone like lovinglinux catches ahold of this - he/she knows firefox quite well

If you were to go -
 view > zoom > reset, close firefox, then re-open and go 
view > zoom - zoom in twice,  close and yet again re-open firefox it doesn't open zoomed?

---

### Post by benerivo on 2011-05-20
> **mc4man said:**
> ...If you were to go -
 view > zoom > reset, close firefox, then re-open and go 
view > zoom - zoom in twice,  close and yet again re-open firefox it doesn't open zoomed?
Yes, but only for the site i was on when i set the zoom level. Any other site opens at 100%. I often visit new sites, and would prefer to have the zoom set globally rather than on a per site basis. The minimum zoom setting in about:config sounds as if it should work, but does so only after you've used the keyboard shortcut to zoom!

Also, the NoSquint addon works beautifully, but it's not compatible with the current alpha version of Firefox. I'm sure it will be one day :-)

---

### Post by mc4man on 2011-05-20
> **benerivo said:**
> Yes, but only for the site i was on when i set the zoom level. Any other site opens at 100%. I often visit new sites, and would prefer to have the zoom set globally rather than on a per site basis. The minimum zoom setting in about:config sounds as if it should work, but does so only after you've used the keyboard shortcut to zoom!

Also, the NoSquint addon works beautifully, but it's not compatible with the current alpha version of Firefox. I'm sure it will be one day :-)

Your right - i was being 'stupid' - I mainly  use opera except for a few sites like here where I use firefox instead, looks better for some reason. 
(as far as text, like FF for videos better) - must have previously zoomed them and firefox remembers per site where opera is for all.
(sorry about that

---


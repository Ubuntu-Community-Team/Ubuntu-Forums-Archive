---
title: "Dash Functionality"
date: 2011-07-12
forum: General Help
---

### Post by ddjolley on 2011-07-12
It is my understanding that the role of the Dash is to replace access to the Places, System and Applications functionality that was provided in a drop down menu in Ubuntu Classic.  Access to Places and System functionality is available outside of the Dash.  Is there a way to get at the Applications functionality outside of the Dash?  Thanks for any input.

           ... doug

---

### Post by FormatSeize on 2011-07-12
If you are talking about 11.04, then you have to search for them. Hope you know the name of what you are after. Or, you can use Gnome-Classic, which has the menu that you may be more accustomed to.

---

### Post by ddjolley on 2011-07-12
> If you are talking about 11.04, then you have to search for them.
> Hope  you know the name of what you are after. 

Well, I don't think that you *HAVE* to search for them.  You can use

"Dash" => "More Apps" => "Installed" and click on "See XX more resjults".

As you may have guessed, I'm no fan of the Dash.  "System" amd "Places" are both available outside of the Dash.  I'm wondering if there isn't also a way to get at "Applications" outside of the Dash; then, I could just blow the whole thing off.

Thanks for the input.

          ... doug

---

### Post by bturrie on 2011-07-12
This adds a new AppMenu Launcher to the Unity Bar. Right click anywhere on the desktop and select Create Launcher. In the Name box enter Menu.desktop. In the Command box enter /usr/lib/gnome-main-menu/application-browser. Click on the icon box and browse to /usr/share/icons/Breathe/scalable/places/gnome-main-menu.svg. 

Then move the resulting launcher to ~/.local/applications/share. After you have moved it, drag the launcher from there to your Unity Bar.

That's what I have on my system for now.

see: [http://turriebuntu.wordpress.com/ubuntu-pages/natty-tweaks-draft/](http://turriebuntu.wordpress.com/ubuntu-pages/natty-tweaks-draft/)

The post there is still a work in progress

---

### Post by ddjolley on 2011-07-12
> see: [http://turriebuntu.wordpress.com/ubu...-tweaks-draft/]("http://turriebuntu.wordpress.com/ubuntu-pages/natty-tweaks-draft/")

I have a feeling that this may be what I'm looking for.  My problem is that the directory /usr/lib/gnome-main-menu does not seem to be present on my system.  Do, I need to install a package?  Thanks.

          ... doug

P.S. - Some of your other solutions are of interest.  I'll want to look at those when I get this problem resolved.  We seem to share a lot of the same concerns. :)

---

### Post by wildmanne39 on 2011-07-13
Hi, here is a link that I have for that same type of thing.
[http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html](http://www.webupd8.org/2011/06/use-classic-menu-in-unity-classicmenu.html)

I also use the awn launcher from synaptic and put an applet on it called yet another menu applet and it is exactly the same as the gnome2 menu, then I put the launcher at the bottom of the screen, here is a screenshot.

---

### Post by bturrie on 2011-07-13
No idea what added /usr/lib/gnome-main-menu/ or where it came from. It's on my Natty HTPC machine and on my Lucid Main Desktop but not on my Lucid desktop that hosts apt-mirror. I tried installing Docky, AWN, and Dockbarx on that machine none of them added the folder. 

I know it got added two days after I first installed AWN on my main desktop. I'll check Screenlet and gdesklet applets when I get the chance to see if somehow they added the folder. Meanwhile I'm going to take a look at Caradapio since I'm having icon size problems with classicmenu-indicator. Not sure I don't like wildmanne39's approach best.

My overall concern is that gnome 3 stability may turn out like kde4 did early on and the next LTS could suffer as a result.

---

### Post by 3rdalbum on 2011-07-13
> **bturrie said:**
> 
My overall concern is that gnome 3 stability may turn out like kde4 did early on and the next LTS could suffer as a result.

KDE 4.0 was an almost-total rewrite of KDE. Gnome 3 is basically Gnome 2.x but with a new graphical shell - most of the surrounding infrastructure and Gnome programs are just the usual "evolution from the previous Gnome version" that happened during the Gnome 2.x cycle. In short, the UI might be a little unstable (possibly) but everything else should be as solid as in Gnome 2.

The next Ubuntu LTS will be 12.04 LTS, and it will not use the Gnome 3 UI. It will use the Unity UI with the stable and solid Gnome 3 infrastructure. Unity is shaping up nicely and should be in really good form come 12.04.

---

### Post by bturrie on 2011-07-13
Turns out there's a package named gnome-main-menu at least in the Lucid repository that adds the folder. I tested it on my Lucid system that was missing the folder and it got added when I installed the package. Still need to make sure it's in the Natty repository, but the package didn't get removed during the upgrade so I'm thinking it's there.

I also need to add that bit to my blog write-up.

---

### Post by bturrie on 2011-07-13
Yes, gnome-main-menu shows up in my Natty repositoris.

---

### Post by ddjolley on 2011-07-13
> Then move the resulting launcher to ~/.local/applications/share.

~/.local/applications/share does not exist.  Is it important that I create it?  For the moment I have moved the icon to ~/.local/share.  What do you think about me just leaving it there?  Thanks.

          ... doug

---

### Post by bturrie on 2011-07-13
I think in terms of dragging it to the Unity Launcher that should be fine--though I haven't tried it myself. Not sure Dash will be able to find it if it's not in the ~/.local/applications folder. Don't imagine that would be a problem though. 

BTW: I tried cardapio and like it. I liked it enough to stop AWN form launching automatically at startup. Not planning to delete it for a while though.

---

### Post by wildmanne39 on 2011-07-13
Hi, I took a screenshot to show you the menu, just in case you continue to have problems with the other method.

If you want to do it this way I will post how to make the side launcher stay hidden. You can put this dock anywhere you want even on top of the side launcher after it is set to stay hidden.

---

### Post by bturrie on 2011-07-13
My bad! The correct location is ~/.local/share/applications...I had the last two in reverse order which is incorrect.

BTW: I do like wildmanne39's approach quite a lot. The resulting style is similar to the desktop on my primary desktop (running Lucid right now). The biggest difference I see is that I've removed the Top Bar from my machine and use an AWN applet for the systray.

My desktop is here:

[https://turriebuntu.wordpress.com/](https://turriebuntu.wordpress.com/)

If that's at all of interest. Anyway, the only way I can think of duplicating that is if I use the Natty Classic Desktop.

---

### Post by wildmanne39 on 2011-07-13
> **bturrie said:**
> My bad! The correct location is ~/.local/share/applications...I had the last two in reverse order which is incorrect.

BTW: I do like wildmanne39's approach quite a lot. The resulting style is similar to the desktop on my primary desktop (running Lucid right now). The biggest difference I see is that I've removed the Top Bar from my machine and use an AWN applet for the systray.

My desktop is here:

[https://turriebuntu.wordpress.com/](https://turriebuntu.wordpress.com/)

If that's at all of interest. Anyway, the only way I can think of duplicating that is if I use the Natty Classic Desktop.Hi, that is a nice desktop.

---

### Post by ddjolley on 2011-07-13
>The correct location is ~/.local/share/applications...
> I had the last two in reverse order which is incorrect.

The problem is that I don't have an applications directory in ~/.local/share.  I'm not quite sure why you would have it and I wouldn't.  However, the issue is whether I should create it and then move the icon into it before copying it to the Launcher; or, just leavie it where it is (i.e., in ~/.local/share) and copyingi directly to the Launcher from there.  FYI, I have already done the latter and it seems to work just fine..  So, is there some reason that I shouldn't be happy with this?  Thanks.

         ... doug

---

### Post by bturrie on 2011-07-13
No reason that I can think of to create the folder...but I sure didn't create mine, at least not intentionally. As far as the applications folder is concerned, I believe that's where Dash looks  for user applications when it's doing a search. Can't imagine why you'd care if Dash can find your Applications Menu since the whole point is so you won't need Dash to find applications.

---

### Post by ddjolley on 2011-07-14
> No reason that I can think of to create the folder...
> but I sure didn't  create mine, at least not intentionally.

Understood.  It was not present for me.  In your blog post you may want to make mention of the fact that the applications directory may have to be created.  I note that you have already modified your post to reflect the fact that the gnome-main-menu packages may need  to be installed.

> As far as the applications  folder is concerned, I believe that's where Dash looks  for user
> applications when it's doing a search. Can't imagine why you'd care if  Dash can find your 
> Applications Menu since the whole point is so you  won't need Dash to find applications.

Your point is well taken; and, as a practical matter I can't imagine why it would make a difference either.  However, the menu has to reside somewhere; so, I might as well create the "applications" directory and store it there.  That way, apparently, I will at least be following convention.

Here's the problem though, even after I created the "applications" directory and placed the menu in it, it still doesn't show up in the Dash.  Any comments on that?

Thanks.

          ... doug

---

### Post by bturrie on 2011-07-15
You are right that's where Dash looks for user applications. Mine has over 80 files, mostly for wine programs. Regarding why Dash might not be finding your launcher, is it set as executable? That's the only reason I can think of.

---

### Post by bturrie on 2011-07-15
BTW, I decided I liked Natty enough to upgrade my primary desktop machine. Actually upgrade is the wrong word, the upgrade failed because Update Manager said it had problems it could not resolve. Maybe because I had upgraded to a kernel backported from Maverick. I spent a couple hours downgrading packages to no effect before I gave up and did a fresh install of Natty.

It wasn't too bad because I had a separate home folder as well as a recent copy of /etc. That meant I could keep all of my files and recover most of my package configurations post upgrade.

---

### Post by wildmanne39 on 2011-07-16
> **bturrie said:**
> BTW, I decided I liked Natty enough to upgrade my primary desktop machine. Actually upgrade is the wrong word, the upgrade failed because Update Manager said it had problems it could not resolve. Maybe because I had upgraded to a kernel backported from Maverick. I spent a couple hours downgrading packages to no effect before I gave up and did a fresh install of Natty.

It wasn't too bad because I had a separate home folder as well as a recent copy of /etc. That meant I could keep all of my files and recover most of my package configurations post upgrade.Hi, thats good when I tried to upgrade to natty it also failed I had to do a fresh install.

---

### Post by ddjolley on 2011-07-17
> You are right that's where Dash looks for user applications

I don't know what to say.  All of the sudden it seems to be working just fine.  I didn't change anything.  Anyway, I think that we're good on all fronts.  Thanks a batch for the input.

        ... doug

---


---
title: "Solution for an interface for a linux media computer?"
date: 2010-02-10
forum: General Help
---

### Post by Garnett on 2010-02-10
I want to make a media PC for the living room. it's going to be for:

Catch Up TV
Recording TV programs
Watching downloaded programs
Spotify (in WINE)
Other music
Torrenting
Internet Browsing (watching Youtube etc)

Ideally I'd like to have it set up some it's fairly clear how to watch films and programs and listen to music - like a dedicated machine - so my girlfriend (who has no interest in computers) can use it.

Internet browsing and torrenting is less important and could be hidden away.

Any ideas how I could set this up? Thanks a lot for any assistance. One day hopefully I'll know something worth passing on!

---

### Post by Just_SomeGuy on 2010-02-10
Not sure if this would work for you, but this is what I have:

A mythtv server in my office which records tv and has my movies, music, and pictures.

Three WD TV Live boxes on the tvs in the house. Very small, light,low power, and perfectly silent. They put out perfect 1080p and run ~$120.
They aren't perfect, but I've been through three generations of media devices and they are by far the best I've owned.

That would take care of most of your requirements except torrents, web browsing, and spotify. Youtube is built in but you won't get a full browser.

---

### Post by Garnett on 2010-02-10
Thanks for that. I was just starting to look into MythTV.

I can't really justify two boxes in our small flat. I think aI need to go for one machine.

I realise I'm going to have to compromise but I was hoping either for a happy medium or a basic setup at start up which provided fast access to TV, films, music, and internet and an option to go to a more familiar desktop setup if I need to torrent or do anything else

---

### Post by warfacegod on 2010-02-10
Maybe Dual boot with Mythbuntu then?

[http://www.mythbuntu.org/]("http://www.mythbuntu.org/")

---

### Post by Garnett on 2010-02-10
> **warfacegod said:**
> Maybe Dual boot with Mythbuntu then?

[http://www.mythbuntu.org/]("http://www.mythbuntu.org/")Thanks a lot for that suggestion. Trying to get my head around the various options: MythTV, Mythbuntu,  Ubuntu with MythTV and Mythbuntu Control Centre as installed packages...

I'm pretty new to Linux, so I'm not explaining myself very well.

I'd rather not have to reboot to switch between "simple" (quick links to films, music etc) and "advanced" (standard ubuntu desktop) interface.

I wonder if I could use mythbuntu, install gnome-desktop, disable it from loading at start up, and write a small script to switch between the standard mythbuntu interface and the gnome-desktop...

I plan to use a Wireless KeySonic HTPC Keyboard/TouchPad to control it.

---

### Post by warfacegod on 2010-02-10
> **Garnett said:**
> Thanks a lot for that suggestion. Trying to get my head around the various options: MythTV, Mythbuntu,  Ubuntu with MythTV and Mythbuntu Control Centre as installed packages...

I'm pretty new to Linux, so I'm not explaining myself very well.

I'd rather not have to reboot to switch between "simple" (quick links to films, music etc) and "advanced" (standard ubuntu desktop) interface.

I wonder if I could use mythbuntu, install gnome-desktop, disable it from loading at start up, and write a small script to switch between the standard mythbuntu interface and the gnome-desktop...

I plan to use a Wireless KeySonic HTPC Keyboard/TouchPad to control it.

I'm sure you could do that just fine. Mythbuntu is basically just Xubuntu with MythTV preinstalled. I think there's a Mythbuntu sub-forum around here somewhere. Maybe you should find it and have a look before diving in. I had it for about a week and liked it allot but got rid of it because my video card wasn't up to snuff for running my TV very well.

---

### Post by Garnett on 2010-02-10
> **warfacegod said:**
> Mythbuntu is basically just Xubuntu with MythTV preinstalled.Ah. Thanks a lot. It's these sort of off-the-cuff comments that reeally help to get a better overall understanding of the situation.

It looks like I could load Ubuntu with MythTV and Mythbuntu Control Centre as installed packages (read that someone did that somewhere) and possibly toggle between the interfaces then.

Fantastic.

---

### Post by warfacegod on 2010-02-10
> **Garnett said:**
> Ah. Thanks a lot. It's these sort of off-the-cuff comments that reeally help to get a better overall understanding of the situation.

It looks like I could load Ubuntu with MythTV and Mythbuntu Control Centre as installed packages (read that someone did that somewhere) and possibly toggle between the interfaces then.

Fantastic.

Yup, should work that way too.

---

### Post by Just_SomeGuy on 2010-02-10
> **Garnett said:**
> 

It looks like I could load Ubuntu with MythTV and Mythbuntu Control Centre as installed packages (read that someone did that somewhere) and possibly toggle between the interfaces then.

That's how mine is set up: regular ubuntu with mythtv installed.
You can just launch mythfrontend whenever you fell like using it.
Myth control center isn't really all that useful except for installing plugins. The rest of the interface is just duplicates of things you already have in the regular admin interface.

---

### Post by Garnett on 2010-02-10
> **Just_SomeGuy said:**
> That's how mine is set up: regular ubuntu with mythtv installed.
You can just launch mythfrontend whenever you fell like using it.
Myth control center isn't really all that useful except for installing plugins. The rest of the interface is just duplicates of things you already have in the regular admin interface.Ah - awesome. Good to know.  SO I could set mythfrontend to launch at start up. Is it easy to kill?

---

### Post by warfacegod on 2010-02-10
> **Garnett said:**
> Ah - awesome. Good to know.  SO I could set mythfrontend to launch at start up. Is it easy to kill?

When I had Mythbuntu, it exited quite easily. I don't remember how to do it but it was easy. Esc. maybe?

---

### Post by Garnett on 2010-02-10
> **warfacegod said:**
> When I had Mythbuntu, it exited quite easily. I don't remember how to do it but it was easy. Esc. maybe?Sweet

---

### Post by Just_SomeGuy on 2010-02-10
> **warfacegod said:**
>  Esc. maybe?

Yep. Just hit esc a couple of times.

---


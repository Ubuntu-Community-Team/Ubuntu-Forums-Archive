---
title: "Automatix-ish app for Kubuntu"
date: 2006-05-20
forum: General Help
---

### Post by walking is still honest on 2006-05-20
(origional post [here]("http://kubuntuforums.net/forums/index.php?topic=5292.msg20801#msg20801"))

Ok, first off, I'm totally non-existant on the Ubuntu forums. I'm a developer by profession though, and have been a linux user for the last three years, and have been using ubuntu since warty. Recently I switched to KDE, gave Kubuntu a shot, and now it is my distro of choice.

I've been using (and recommending) Automatix pretty much since its first release. It isn't that I can't do everything there, it's that I have better things to do with my time then spend another two hours configuring my OS after install. The benefit to me however, is totally dwarfed by the benefit to newbs. A friend of mine was a WinZealot for years, it was a combination of Automatix and the Ubuntu forums that  has him as a full time linux user now.

So, the benefits of a post-install automator are astronomical compared to the effort to do this kinda thing. So here's the deal, I want to put something like automatix together, with a few differences.

1) Ubuntu already has automatix, this will be Kubuntu oriented. For example, automatix installs all sorts of stuff for gstreamer. We'll keep that, but we'll also have xine-extracodecs (or whatever it is). I'm still a bit of a KDE newb though, so I am not completely aware of what would be needed. In the next week or so I'll go through the forums here to see whats interesting, but you guys need to let me know what you want to see in something like this.

2) Automatix uses something called Zenity to display its dialogs. Zenity is this wonderful command line app that lets you display GTK dialogs based on the arguments you pass it. I'm not 100% sure on this, but I'm pretty sure KDialog has feature parity, and is Qt based. If thats the case, the first step is gonna be porting automatix to KDialog.

3) Bash scripting is easy. I mean, insanely easy. Most people could script the how-tos they post without that much effort. What I'm thinking of is to create an automator engine, with the emphasis being on simplicity rather then on functionality, so the average user can add to it without too much difficulty. What we could do is a bit of encapsulation, by moving the functionality of the individual tasks to a script folder. That way if John Q. Newbie wants to add a plugin, all he needs to do is add an executable script to the plugin folder. We could keep zenity in there too, so all it would take is an additional argument if you want qt or gtk. Honestly, I think there is a need for this. A friend of mine put together a tutorial on printer drivers, and was blown away by how easy it was to automate.  

Anyways, this is something fairly off the cuff, I don't even know if I'm stepping on anyones toes here. There is an AutomatiKs by a german fellow called BeeWee, however that uses Kommander, which im both not familiar with, and I want something simple enough to understand and extend, that even non-developers can use it. There is Automatix-Kubuntu, but really, its still totally gnome-oriented. Arnieboy seems to be the origional maintainer, however it seems like he's doing everything he can to pass the buck, and I want to take it a little further then he did. If something like this is already in the works, I would be more then happy to help out if the maintainers would get in touch with me.

So, please tell me what you think. Is this even a good idea? Do you have a better idea for the technology used? What would you like to see in it? What would be a good name for this little project?

---

### Post by adamkane on 2006-05-20
Anyone could create an application to improve on automatix, if they wished. arnieboy has been doing a decent job keeping automatix up-to-date and functional for breezy, so no one has bothered to write another script.
[http://beerorkid.com/automatix/]("http://beerorkid.com/automatix/")

Automatix still doesn't do all that it should, and there isn't enough documentation to keep new users out of trouble, and there is no uninstall option, so there's plenty of work to be done by anyone with enough free time.

I think most people are waiting for dapper, before a new auto-install script is created. I also think the easylinux team is doing a superior job showing people how to obtain all the automatix functionality without automatix in any case:

[http://easylinux.info/wiki/Ubuntu]("http://easylinux.info/wiki/Ubuntu")
[http://easylinux.info/wiki/Ubuntu_dapper]("http://easylinux.info/wiki/Ubuntu_dapper")

---


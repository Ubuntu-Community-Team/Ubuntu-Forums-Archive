---
title: "iPod Support is Everywhere, and None of it Works"
date: 2006-03-16
forum: General Help
---

### Post by dpaint4 on 2006-03-16
That's what it seems like. Virtually all my audio players have some sort of iPod option. Well, I've been putting off trying to use my iPod with Ubuntu because I feared it would be a nightmare, and so far, that's been true.

I have a Video iPod, though I'm not asking for video support. All I'd really really like is fot Banshee to not crash immediately as soon as I plug it in, which is what it does, every single time. Amarok (which I hate) dosen't see it at all. GtkPod dosen't see it at all.

It's a Fat32 iPod I believe. Prior to this I used it in Windows XP with iTunes. Hated both of those of course, so I'm glad to be using Ubuntu. And I got a 30BG Vorbis player just in case, but nothing I can find has a synching option for that. 

My dream scenario would be getting to use my iPod with Banshee. What do you guys do to make this work?

---

### Post by Zelut on 2006-03-16
I use Gtkpod with my iPod shuffle with no problems.  It sounds like you've tried that though already.. The only issue I have is that I need to manually 'sudo eject ipod' before I remove it.  Other than that everything is just Breezy.

---

### Post by aysiu on 2006-03-16
A Video iPod is a fairly new one.

My wife has an old G3 iPod, and it works just fine with GtkPod.

It usually takes Linux applications a little while to catch up with Apple (not that Apple's terribly cooperative in this endeavor).

Note that in Breezy, Banshee is 0.9.7.1. In Dapper, it'll be 0.10.8.

---

### Post by dpaint4 on 2006-03-16
[QUOTE=aysiu]A Video iPod is a fairly new one.

My wife has an old G3 iPod, and it works just fine with GtkPod.

It usually takes Linux applications a little while to catch up with Apple (not that Apple's terribly cooperative in this endeavor).

Note that in Breezy, Banshee is 0.9.7.1. In Dapper, it'll be 0.10.8.[/QUOTE]

That's absolutely fine. It's not like Apple makes it easy on anyone not running their own OS, or Windows with iTunes.

I'll just sit on it for a while and see if it hatches sometime after the dust settles from Dapper.

---

### Post by terranz on 2006-03-16
I've just last night got my ipod playing music in ubuntu.

I installed amarok which I knew (from mandriva) works with ipods.  I haven't tried putting music onto my ipod but it plays from it.

For some reason amarok crashed on ubuntu until I installed kmail.  Both I got from synaptic package manager.

I'm looking for calendar support (apart from sunbird).

---

### Post by terranz on 2006-03-16
forgot to subscribe

---

### Post by dpaint4 on 2006-03-16
Thanks. I installed Amarok as a last ditch attempt to get my ViPod up and working but alas, it is not seen by Amarok, and anyway I really really don't like that application. It's just so huge and in-the-way. And the interface is all glitchy and bad under Gnome because it wasn't built for it (so no offence Mr. Amarok developer).

I'll try your strange Kmail trick. That's really weird. Wonder why that matters at all.

---

### Post by terranz on 2006-03-16
considering I didn't want kmail, I wish I knew.  This is my first time running it on a system with only gnome.

What's your fav audio player?

---

### Post by dpaint4 on 2006-03-16
[QUOTE=terranz]considering I didn't want kmail, I wish I knew.  This is my first time running it on a system with only gnome.

What's your fav audio player?[/QUOTE]

Well on Windows I used exclusively Foobar2000, which runs under Wine, a little glitchy though and can't encode -- fails in writing the output file with errors like:
```

Error writing to file (I/O error (win32 #233)) : file://c:\windows\profiles\curtis\Desktop\CD track 01.ogg
```
(Incidentally, anyone who knows what's going on with that is my hero.)

I'm currently trying to like Banshee (but I don't). It's the closest to the interface and the functionality that I want, but it is horribly buggy in the release that I'm running from the Breezy repositories.

That and I'd like seperate encoders. Not having to hack/modify/update Gstreamer to whatever my favorite Lame/Vorbis is at the moment. In foobar, you could just point the app to a cute little self-contained command line encoder and it'd use it without actually altering the codecs that the OS uses. That would be AWSOME if there was something like that.

So, that's my Christmas list, basically. Hope it wasn't too strange or cryptic. I get a little excited when I start talking about this stuff.

---

### Post by dpaint4 on 2006-03-16
Wow. So I figured the Foobar issue out. I have to run it as root to be able to write files from it.

So I launch it now like:

sudo wine /path/to/foobar.exe

And then I can encode with standard .exe command-line encoders like the latest aoTuV and LAME without changing my system or anything outside of the app. Isn't that stinkin' awsome. I hope lots of people like me find this thread because this was just the best ever to learn!

So now I'll encode from Foobar2000 in Wine and I'll play and sych with Gnome apps. Assuming I can find one that likes my iPod or some good update comes with Dapper or something.

---

### Post by dpaint4 on 2006-03-16
Hmmm. Still get the same error with Vorbis. But LAME works. I wonder why it does that thing with the path:

file://c:\windo...

Seems like it should either be file:// or c:\ but certainly not both. Wish that was something I could change.

---

### Post by terranz on 2006-03-16
being home for lunch I've just installed gtkpod and set amarok as the assoiated player \\:D/

---

### Post by dpaint4 on 2006-03-16
Works for you then? That's good news. I'll try that. After I install that strange mail program that seems to be needed. :P

---

### Post by terranz on 2006-03-16
On the up side kmail is a very small download.

Just before comming back to work for the afternoon I made a script containing
```
sudo eject ipod
```
and an ipod icon

Almost ready for the wife to use

---

### Post by dpaint4 on 2006-03-16
[QUOTE=terranz]On the up side kmail is a very small download.

Just before comming back to work for the afternoon I made a script containing
```
sudo eject ipod
```
and an ipod icon

Almost ready for the wife to use[/QUOTE]

That's smart. Does that code work for all removeable media? I try to unmount things and they usually 'fail' and sit there, forcing me to just disconnect the USB. I want to try your way.

---

### Post by briguy on 2006-03-16
I've got amaroK syncing with my iPod and it's fantastic!  Couple of things - have you installed libgpod?  sudo apt-get install libgpod-common libgpod0

I installed amarok from svn - there is an automated script which made it very easy.  Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=80492&highlight=libgpod+svn]("http://www.ubuntuforums.org/showthread.php?t=80492&highlight=libgpod+svn")


There's a lot there, make sure you build libgpod from source, again not difficult.

---

### Post by dpaint4 on 2006-03-16
[QUOTE=briguy]I've got amaroK syncing with my iPod and it's fantastic!  Couple of things - have you installed libgpod?  sudo apt-get install libgpod-common libgpod0

I installed amarok from svn - there is an automated script which made it very easy.  Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=80492&highlight=libgpod+svn]("http://www.ubuntuforums.org/showthread.php?t=80492&highlight=libgpod+svn")


There's a lot there, make sure you build libgpod from source, again not difficult.[/QUOTE]

This evening I seem to have gtkpod up and running WITH video support, which is insane. Never expected that. Now all I have to do is wait for Vive to improve and I'm basically in business again.

I'm bookmarking your link. I really do have a strong distaste for the enormous interface of amarok, but I guess it could be an aquired taste, right? :P

---

### Post by terranz on 2006-03-16
when you use amarok with gtkpod then amarok defaults to a small interface.

I've had the same problem with unmounting usb devices and found ```
sudo eject ipod
``` while browsing the forums.

just replace ipod with the name of your usb drive

---

### Post by dpaint4 on 2006-03-16
[QUOTE=terranz]when you use amarok with gtkpod then amarok defaults to a small interface.

I've had the same problem with unmounting usb devices and found ```
sudo eject ipod
``` while browsing the forums.

just replace ipod with the name of your usb drive[/QUOTE]

Wow. That's really effective and simple. I wonder why that's not the command that's used by the GUI to do the same thing, when you 'unmount' things and then have to deal with their ghosts never wanting to get lost untill you shut down.

I'd much rather have an integrated 'eject' option for all my devices that throughly removes them.

Thanks for the handy command.

---


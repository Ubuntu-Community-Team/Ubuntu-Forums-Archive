---
title: "gksudo nautilus changes background"
date: 2010-06-24
forum: General Help
---

### Post by J V on 2010-06-24
gksudo nautilus sets the background to default (Because nautilus is rendering the desktop)

I set the gconf key to stop it rendering the desktop, but this only affects the icons.

How can I get it to give me back my background?

Edit: Fixed the desktop (--no-desktop option on nautilus command) - need to find how to kill the nautilus process automatically when I close it...

---

### Post by realzippy on 2010-06-24
...cannot reproduce,backround persists.
Nautilus *renders* the desktop ???How does this work??

---

### Post by J V on 2010-06-24
Well, no...

Nautilus used to only render the icons, I think metacity did the background. But now in Lucid whenever I run gksudo nautilus it not only changes the background, but that dangerous sudo nautilus process keeps running after I close the window...

I can get it back after killing the root process and changing the background in the appearances configuration though...

---

### Post by J V on 2010-06-25
Bump: Anyone know what causes this behaviour?

---

### Post by yetiman64 on 2010-06-25
I've never actually noted the desktop change you mention, but with regards to 
> ...but that dangerous sudo nautilus process keeps running after I close the  window...In the terminal you launched "gksudo nautilus" with, use CTRL + C to end the process and get your prompt back.

It's good you're using gksudo here, though I've ceased "sudoing" nautilus altogether nowadays and have reverted to terminal use as is much safer.

Is there any particulay reason or actions that needs nautilus as root that can't otherwise be done in the terminal for you ?

---

### Post by J V on 2010-06-25
> In the terminal you launched "gksudo nautilus" with, use CTRL + C to end  the process and get your prompt back.Actually, it's mapped to a shortcut so I can quickly do something as root, no terminal that I know of.

> It's good you're using gksudo here, though I've ceased "sudoing"  nautilus altogether nowadays and have reverted to terminal use as is  much safer.I know more about terminal use now, but it's still quicker to hit the shortcut and drag/drop files...

> Is there any particulay reason or actions that needs nautilus as root  that can't otherwise be done in the terminal for you ?Not really, it's just for convinience (And the ability to start any large array of programs on different files without having to type my pass in every 15 minutes)

---

### Post by Leppie on 2010-06-25
if you only want to open the nautilus file manager part, it's better to use it like this:
```
gksudo nautilus --no-desktop --browser
```

---

### Post by J V on 2010-06-25
> **Leppie said:**
> if you only want to open the nautilus file manager part, it's better to use it like this:
```
gksudo nautilus --no-desktop --browser
```
Boom! Looks great, but for some reason, it won't run that command from the shortcuts... Anyone know where I could find the error codes for gnome shortcuts?

GKsudo is throwing the error:
```
gksudo: unrecognized option '--no-desktop'
```Edit: Fixed by quoting it... Now the desktop doesn't get changed, but the process continues...

Also of note: Ctrl C in the terminal doesn't kill the root nautilus process, only the gksudo process...

---

### Post by philinux on 2010-06-25
> **J V said:**
> gksudo nautilus sets the background to default (Because nautilus is rendering the desktop)

I set the gconf key to stop it rendering the desktop, but this only affects the icons.

How can I get it to give me back my background?

I'm not seeing this at all. Have you tweaked something?

And yes ps aux show root nautilus still there.

---

### Post by yetiman64 on 2010-06-25
> Also of note: Ctrl C in the terminal doesn't kill the root nautilus  process, only the gksudo process... Have noted this now for future reference-- Thanks J V

---

### Post by J V on 2010-06-25
@Yeti: It must be using subProcess... I wrote a frontend for an application in a similar way, but if users input things just wrong, it would crash the backend (Nothing to do on my end) - killing the frontend left the backend running at 100% cpu... was a pita :)

@Phillinux: No tweaks pertaining to the desktop (Other than the aforementioned icon removal key) - could be I dragged something along from my last install (Kept home partition)

---

### Post by philinux on 2010-06-25
> **J V said:**
> @Yeti: It must be using subProcess... I wrote a frontend for an application in a similar way, but if users input things just wrong, it would crash the backend (Nothing to do on my end) - killing the frontend left the backend running at 100% cpu... was a pita :)

@Phillinux: No tweaks pertaining to the desktop (Other than the aforementioned icon removal key) - could be I dragged something along from my last install (Kept home partition)

Maybe see if anything in .nautilus or another config file for it and delete them.

---

### Post by J V on 2010-06-25
Well I fixed that problem with --no-desktop... but it still runs as subprocess... Either need a tweak to gksudo... or use sudo and hardcode my password (Not liking that idea)

---

### Post by philinux on 2010-06-25
> **J V said:**
> Well I fixed that problem with --no-desktop... but it still runs as subprocess... Either need a tweak to gksudo... or use sudo and hardcode my password (Not liking that idea)

Another solution is to install nautilus-gksu then logout login. You'll then have "Open as Administrator" in context menu right click. ;)

---

### Post by J V on 2010-06-25
Tried that, doesn't work if the default open is the wrong app (Hate wine with it's overriding everything...)

---

### Post by blur xc on 2010-06-25
I think when you run nautilus as root (or any other program) you will load the root users theme.  There's was a thread a while ago about why the update manager didn't match your user's theme settings, and the fix was kinda easy.  I think you just make a symlink form your theme settings to the root users theme folder, dunno...  it was a while ago.  I might have to look that one up again.

BM

---

### Post by J V on 2010-06-25
Ok, for the fourth time in a row: We fixed that part of the problem... putting it into #1...

---

### Post by J V on 2010-06-26
How to get a process ID...

I could kill the gksudo and the nautilus if I knew only one of their IDs...

---

### Post by yetiman64 on 2010-06-26
> **J V said:**
> How to get a process ID...

I could kill the gksudo and the nautilus if I knew only one of their IDs...

Try

```
ps -A | grep nautilus && ps -A | grep gksudo
```and see if it suits your needs, the PID is the first number in each line of the output.

---

### Post by kerry_s on 2010-06-26
**gksudo "nautilus --no-desktop"**

should work from shortcut. i have a launcher of it.

---

### Post by J V on 2010-06-26
@Yetiman: I guess I'll have to go for something like this yes... Unfortunately: ```
ps -AU root | grep -E "nautilus|gksudo" | kill
```Is the best I've got, and kill won't take stdin... Plus, with "&&" it would wait until the command closed before running, which is the problem: It won't close... I did however find that apparently root runs nautilus from the start (At least on this system) - Don't know why, maybe the process just doesn't do anything unless a window is up... Either way, it's impractical (And apparently unnecessary)  to kill the process... I'll just leave it up there...

@kerry: Read 4 posts up...

---

### Post by Leppie on 2010-06-26
have you tried checking gconf?
```
gconftool-2 -R /apps/nautilus/preferences | grep show_desktop
```
if it's set to true, metacity is not handling your desktop.

---

### Post by kerry_s on 2010-06-26
> @kerry: Read 4 posts up...


my bag, i was eating & reading, so i missed that. :lolflag:

theres a command called "pidof" that i use in scripts from time to time. it might be simpler for what you want.

example:
**pidof nautilus**

---


---
title: "Multimedia Keys on Keyboard"
date: 2006-06-10
forum: General Help
---

### Post by aoberoi on 2006-06-10
I just finished updating to Dapper from Brezy and started up Rhythmbox to find that the next/prev keys on my Logitched Cordless Pro (itouch) didn't do anything. I set my keyboard layout to Logitech Itouch in the Keyboard settings and I went to Keyboard shortcuts in the System->Preferences Menu. I  reprogrammed the Sound keys in the dialog. Now the Volume up will not work but the Volume Down will, the next/prev keys still dont work, and the play/pause and stop keys don't work.

Is there a way i can make all the keys work normally the way they had in Breezy?

I didn't have to install anything extra in Breezy for this to work so I'm guessing its just a matter of setting some values back to those defaults.

Any help is appreciated.

(Sorry I'm pretty new to linux in general so i may need detailed guidance)

---

### Post by jan247 on 2006-06-10
System -> Preferences -> Keyboard shortcuts.

Checked that out yet?

---

### Post by twstokes on 2006-06-10
When you type this in console:

```
xmodmap -pke > xmodmap.conf
```

and load xmodmap.conf, do you have any numbers set to XF86AudioNext and XF86AudioPrev?

You can always run ```
xev
``` and then press your Next and Previous buttons to find their code. If they weren't in your xmodmap.conf file that you generated, you can map them by adding them to xmodmap.conf and typing:

[HTML]xmodmap xmodmap.conf[/HTML] at console.

You will have to create a script and run this command at every boot also. If you use KDE, you put it in your ~/.kde/Autostart directory. If you use Gnome, you'll have to search, I have no clue.

There might be a simpler way of doing this, but it's how I get mine to work (I have a Dell Multimedia Keyboard).

You also want to make sure they are properly mapped in your music application, which could be the problem all along.

---

### Post by aoberoi on 2006-06-11
i ran the code you gave and checked the contents of xmodmap.conf

i found the numbers for those buttons already in the file

```
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
```

does that mean it should have been working? What is the next step from there?

---

### Post by nalmeth on 2006-06-11
> System -> Preferences -> Keyboard shortcuts.

Checked that out yet? 
:KS

EDIT: nevermind, I wasn't paying attention, sorry.

---

### Post by aoberoi on 2006-06-11
Okay for some reason unknown to me...

today all the buttons work EXCEPT Volume Up

i went through the xmapmod.conf that you helped me make and i found something interesting...

> keycode 174 = XF86AudioLowerVolume
keycode 175 = XF86AudioRaiseVolume
keycode 176 = XF86AudioRaiseVolume

the RaiseVolume is defined to 2 keys it seems... what should i do about this to get rid of the conflict?

---

### Post by francf on 2006-06-11
Easy way, for all your buttons.
[http://keytouch.sf.net](http://keytouch.sf.net)

---

### Post by aoberoi on 2006-06-11
Okay now i used xev and found out that the keycode when i used the raise volume button was key 176

so i erased the XF86AudioRaiseVolume from the like that has keycode 175

after that i ran

```
xmodmap xmodmap.conf
```

like it was suggested previously

i restarted the computer (i figured i had to restart x somehow but i dont know how to do that manually) and the Volume Up still doesnt work. Something else i should look into?

this keytouch application looks interesting and i'll try it out...

but in the spirit of linux id still like to know how to solve this problem the way we are progressing now

---

### Post by aoberoi on 2006-06-11
keytouch is not what im looking for....

first of all the graphical display that ubuntu has is not coming up when i raise the volume... although the effect is still made

second of all it launches a specific media player for the play, stop, prev, and next buttons... the way ubuntu was doing it on its own before would just tellw hichever media app that was open (or at least i know it worked for Rhythmbox) to switch tracks, play, etc. 

Its a cool app its just not what im looking for

so i guess i want to figure out how exactly to map the key correctly the way ubuntu does it for the rest of the keys in the first place

---

### Post by aoberoi on 2006-06-11
sorry for posting so much...

now that i did completely remove the keytouch package (i did remove configuration files too from synaptic package manager) the effects that it made are still there... XMMS launches when i press next, the volume still goes up wihtout displaying the volume bar, etc

i want to remove those changes and go back to the way it worked when i pressed the buttons originally

---

### Post by twstokes on 2006-06-11
First of all, you don't have to reboot after running xmodmap. Second of all, if you haven't created any start up script that runs xmodmap at boot, then you haven't changed anything permanently, and should be back to square one. If you have created a start up script, just remove it, and you'll be back to where you were when you started posting.

I could help you out more if I used Gnome, but I don't. I use amaroK and always set the DCOP triggers from my keyboard to control it. On the other hand when it comes to volume, I don't go through amaroK, instead I go through Kmix so that I can mute, volume up, volume down the whole system and not just the audio player.

I'm just a linux newbie myself so I wish I could be more help.

---

### Post by aoberoi on 2006-06-11
thanks for your help... after soem more reading i found that if i just copy the contents of xmodmap.conf to the hidden file ~/.xmodmap, gnome will load that into xmodmap on startup (i think thats right?)

and after running xmodmap xmodmap.conf without the button defined twice, i checked the output of xmodmap -pk and found that it was only defined for key 176 the way i wanted.

now the volume does increase when i press the button on the keyboard

the question remains that is that some sort of remnant from the keypress program or is it due to modifying the xmodmap?

I think what i need to find now is where is the command run when the XF86AudioRaiseVolume event is fired. Then i need to know what the values of all the XF86* events were default before i installed keypress.

if anyone could help me find that info it would help a lot.

---

### Post by aoberoi on 2006-06-11
so i restarted and the keypress events are gone.. that is good news...

and now i just went in and removed the duplicate key in my xmodmap and redid the keyboard shortcuts in System -> Preferences -> Keyboard Shortcuts and it works!

i tried the keys in XMMS and apparently they have no effect

im satisfied now.. but i still want to know where the commands are stored that get launched why you press Volume Up or Volume Down or any of ther other Multimedia keys for that matter... is there something specific to gnome?... is it something i can modify myself and view exactly what the commands currently do?

its interesting that play doesnt LAUNCH Rhythmbox but only effects Rhythmbox when its already open... i want to know how i can modify this behavior through whatever command is already being run

and also.. how do i map the rest of the keys i have on the keyboard? i have 4 or 5 keys that dont produce any keypresses in xev... i dont want to lose the Volume Bars again but add to whatever commands are being run now

---

### Post by chenel on 2006-06-14
aoberoi-

To fix the volume-key problem there's a better solution than using Xmodmap.  Since it's the X keyboard mapping that's messed up in the first place, all you need to do is correct the keyboard map and the problem will be fixed.

The X keyboard mappings for "internet" keyboards (the ones with all the extra buttons like yours) are stored in the file /etc/X11/xkb/symbols/inet.  Edit this file and search for the "Logitech" entry.  You should see a list something like this:

```

// Logitech

// Logitech common definitions
partial hidden alphanumeric_keys
xkb_symbols "logitech_base" {

    key <I01> {	[ XF86AudioMedia ] };
    key <I02> { [ XF86WWW ] };
    key <I10> { [ XF86AudioPrev ] };
    key <I15> { [ XF86Community ] };
    key <I16> { [ XF86ScrollClick ] };
    key <I19> { [ XF86AudioNext ] };
    key <I20> { [ XF86AudioMute ] };
    key <I21> {	[ XF86VendorHome ] };
    key <I22> { [ XF86AudioPlay, XF86AudioPause ] };
    key <I24> { [ XF86AudioStop ] };
    key <I2E> { [ XF86AudioLowerVolume ] };
[COLOR="Red"]    key <I2F> {	[ XF86AudioRaiseVolume ] };
    key <I30> { [ XF86AudioRaiseVolume ] }; [/COLOR]
    key <I32> { [ XF86HomePage ] };
    key <I3B> { [ XF86New ] };
    key <I3C> { [ XF86Reply ] };
    key <I43> { [ XF86MyComputer ] };
    key <I44> { [ XF86Documents ] };
    key <I57> { [ XF86Pictures ] };
    key <I58> { [ XF86Music ] };
    key <I5F> { [ XF86Standby ] };
    key <I65> { [ XF86Search ] };
    key <I66> {	[ XF86Favorites	] };
    key <I6A> { [ XF86Back ] };
    key <I6C> { [ XF86Mail ] };
    key <I6D> { [ XF86AudioMedia ] };
};

```

You said that the right key scancode as reported by xev for the volume-raising key is 176, which is defined in the scan-code mappings in /etc/X11/xkb/keycodes/xfree86 to be key <I30>.  That means that any other key that is mapped to the same action is a usuper ;)  So, if you comment out the line that defines the other key, like so:
```

//   key <I2F> {	[ XF86AudioRaiseVolume ] };

```
and then restart X by logging out and pressing Ctrl-Alt-Backspace, all should be well.

Hope this helps.

-Jeremy

P.S. This is apparently a bug that has been reported to the Debian developers.  Hopefully the Ubuntu folks will incorportate the fix soon too.

---

### Post by chenel on 2006-06-14
[QUOTE=aoberoi]
i tried the keys in XMMS and apparently they have no effect
[/QUOTE]

I'm not positive, but I'm pretty sure that XMMS doesn't look for the XF86* events.  There might be a plugin you can get for it somewhere, but I don't remember XMMS ever supporting those keys (or events) natively.  I've heard of people reconfiguring the XF86* events to correspond to command-line options for XMMS, though, like "xmms --play" etc., since I believe XMMS supports control like that.

---

### Post by aoberoi on 2006-06-16
Thanks for your help Jeremy,

the volume control works now!

you seem pretty knowledgable on this topic and ive had some trouble finding answers so i wanted to ask you somethings that have made me curious.

What exactly are XF86* events? Where are they defined? And, where are the commands/scripts stored that get run when those events are triggered? I thought i had a grasp of it, but then what is its relationshp to what xmodmap does?

im asking these questions becuase id eventually like to figure out how to make the other buttons on my keyboard work just as easily/smoothly. there are still some buttons that dont trigger anything in xev and i want to know if there is something i can do about mapping them.

thanks for you help!

---

### Post by Admiral Valdemar on 2006-06-16
I've also noticed that my newly acquired MX3000 desktop system had some multimedia keyboard buttons working at first, then when I tried Keytouch to get them all working, the few that did stopped being useful. Is there no mapping script for the MX3000 or other Logitech keyboards that can be installed without using Keytouch which seems ineffective now?

---

### Post by chenel on 2006-06-16
[QUOTE=aoberoi]the volume control works now![/QUOTE]
Good!

> you seem pretty knowledgable on this topic
Only a farce, my friend, only a farce :)  Honestly, the only reason I was able to fix your problem was because I had it myself and spent like 3 hours on Google and another hour or two hunting through the X11 directory to find what I was looking for.  I happened to know about the keyboard mapping stuff because I remembered something about it from back in the day when I used Gentoo and was trying to get this to work then -- back when I had to do *everything* myself.  If you hadn't posted the scancodes, though, I'd've never found it :)  I suppose after I fixed it I was a little more celebratory than I needed to be, and so my post was a little more "authoritative" than it should've been :)

I'll try to answer what I can though.

> What exactly are XF86* events? Where are they defined? And, where are the commands/scripts stored that get run when those events are triggered? I thought i had a grasp of it, but then what is its relationshp to what xmodmap does?
From what I can tell the XF86* events are sort of like pseudo-scancodes that the X server uses to communicate the keypress to the window manager.  It's hard to find any information about them on the web... You can assign them to any key on the keyboard, just like you could reassign any key on the keyboard to do something else with Xmodmap.  They're only there so that the window manager has something in particular to look for and thus metacity doesn't have to know about 18 zillion different keyboards, I think.  The available names for them are stored in /usr/share/X11/XKeysymDB.  The mappings for them, as I pointed out before, are given in /etc/X11/xkb/symbols/inet, and in turn the mappings for the X-server scancodes (your 176 from before) are defined in /etc/X11/xkb/keycodes/xfree86.

You can play with what each X Keysym (XF86*) event does in a couple of different ways.  If you're content with their default type of actions, then you can use the Keyboard Shortcut wizard thingy under System->Preferences->Keyboard Shortcuts.  If you want more flexibility (say, the ability to run some app that's not already in Gnome's list), you can use the gconf configuration editor: Applications->System Tools->Configuration Editor.  Go to apps->metacity.  Then, you go to the "global_keybindings" entry, and under one of the "run_command_n" entries, you punch in (i.e., type out the name -- you can't just push the key and have it be set, like you can with the Keyboard Shortcuts wizard) one of the X Keysyms that is assigned to one of your buttons.  Go down to "keybinding_commands", change the "command_n" (where 'n' is the same as before) to the command you want your button to have.  Then voilà!  You have your custom key events.

I've found, though, that unfortunately not all the keys on my iTouch keyboard even generate scancodes that the *kernel* recognizes...  As far as I know, the way to tell is to open up a real TTY terminal (Ctrl-Alt-FN) and use 'showkey'.  The scroll wheel on the left side of my keyboard does nothing... and I remember reading somewhere while I was hunting that on some manufacturers' keyboards there are some keys that need to be software-activated somehow before they'll even generate a scancode -- so maybe that's the deal with that one.  Apparently the kernel keyboard driver just doesn't know those Logitech proprietary activation codes :)  So as far as I can tell those keys are basically permanently useless.  Fortunately, that's the only key on my keyboard that's like that.  All the rest generate events under xev, and Ubuntu has set most of them to the right XF86 event already.  All I had to do was use the "keyboard shortcut" wizard to assign them to the right Gnome program/event.

If you need to assign XF86 events to other keys, I would say it seems smarter to use Xmodmap than to hard-code things into the configuration files -- Xmodmap is considerably easier to adjust if (say) you get a new keyboard someday, and it's designed to be flexible like that.  What it does, from what I've read, seems to be a "temporary" modification of the key mappings (I put temporary in quotes because if you start it every time you start X, the effect is hardly temporary :)).  The only reason I suggested you not use it to fix the problem before was because it was a configuration file bug.  But for your other  key-modification needs, Xmodmap seems like the way to go.

Whew.  Hope all of that helps you somehow.  If you have more questions let me know.

-Jeremy

---

### Post by chenel on 2006-06-16
[QUOTE=Admiral Valdemar]I've also noticed that my newly acquired MX3000 desktop system had some multimedia keyboard buttons working at first, then when I tried Keytouch to get them all working, the few that did stopped being useful. Is there no mapping script for the MX3000 or other Logitech keyboards that can be installed without using Keytouch which seems ineffective now?[/QUOTE]

I unfortunately have never tried Keytouch and know nothing about it.  I suppose it sounds reasonable to try to uninstall Keytouch and see if you're at least back to partial functionality? :)

In all likelihood (since I think a lot of the Logitech keyboards generate the same or similar scancodes) your keys are all working, they're just not assigned to anything yet.  The first thing to try is to go to the keyboard shortcut editor (System->Preferences->Keyboard Shortcuts) and see if you can set the shortcuts to your keys that as of right now aren't doing anything.  If you click on one, press a button, and get some "XF86..." string, you're in business :)  If not, the next thing to check is to open up a terminal, punch in 'xev', and see if you get some wash of data in the terminal when you push those coveted buttons.  If so, then we'll be able to get them to work with a small bit of effort.

The keyboard configuration files don't have an entry for the MX3000 yet (is it a new model?) but they do have a few MX-models, and if things don't work right away we can help you to get it set up so that yours is in there and works too.

Let us know how things turn out.

-Jeremy

---

### Post by Admiral Valdemar on 2006-06-16
That's the thing though. I uninstalled Keytouch and was stuck with no real usability, bar a scroll button which I can already use the mouse version of anyway.

I tried xev too, but the buttons don't show up on there, only normal keys produce a code when pushed. So it's like the keys not only aren't assigned, but won't even work in X. I believe it is a new keyboard system (came with the MX600 laser mouse too), and it actually got recognised immediately in Ubuntu, whereas I had to get XP to look it up using my old mouse to navigate first. The problem is just having all these nice multimedia keys and not being able to do anything with them, which is a waste of a good 'board.

---

### Post by chenel on 2006-06-17
Hmm.  I thought I posted either but apparently it didn't make it into the forum...


So.  Have you tried logging into a bona fide TTY terminal (Ctrl-Alt-F1 for example) and using 'showkey'?  Do you get any response that way?  If you do, then something's in the way in X, and maybe we can figure it out.  Otherwise it seems like Keytouch may have messed up the kernel driver, and I have no idea how to fix that other than maybe reinstalling your kernel.

If worst came to worst I suppose you could do a clean reinstall of X... but that seems like a Windows solution, and we'd want to avoid that if we could :)

---

### Post by ffi on 2006-06-21
[QUOTE=chenel]I unfortunately have never tried Keytouch and know nothing about it.  I suppose it sounds reasonable to try to uninstall Keytouch and see if you're at least back to partial functionality? :)

In all likelihood (since I think a lot of the Logitech keyboards generate the same or similar scancodes) your keys are all working, they're just not assigned to anything yet.  The first thing to try is to go to the keyboard shortcut editor (System->Preferences->Keyboard Shortcuts) and see if you can set the shortcuts to your keys that as of right now aren't doing anything.  If you click on one, press a button, and get some "XF86..." string, you're in business :)  If not, the next thing to check is to open up a terminal, punch in 'xev', and see if you get some wash of data in the terminal when you push those coveted buttons.  If so, then we'll be able to get them to work with a small bit of effort.

The keyboard configuration files don't have an entry for the MX3000 yet (is it a new model?) but they do have a few MX-models, and if things don't work right away we can help you to get it set up so that yours is in there and works too.

Let us know how things turn out.

-Jeremy[/QUOTE]

I have a logitech cordless pro, it works in gnome but not kde, when I look at xmodmap, there are no x86 keys, xev does give an output. I tried selecting the keyboard from system settings->regional & accessibilty ->keyboard layout but still nothing.... (btw i am running xgl)

---

### Post by strabes on 2006-06-24
I have a Dell E1705 Laptop and all the action keys are working (like play, pause, next, previous, stop, and the volume and mute ones adjust the system volume, which I like. The only key that I know of that isn't working is the circular one on the top of my keyboard next to the power one that says "MediaDirect". I don't know and can't seem to figure out what the XF86 thing or key number are. Right now, when I press this button, a window comes up which says "Couldn't execute command: rhythmbox
Verify that this command exists." This is probably because I removed rhythmbox from my computer in favor of Listen. I would like Listen to open when I press this button, but I do not know how to change this. Any ideas?

---

### Post by chenel on 2006-06-25
[QUOTE=strabes]I have a Dell E1705 Laptop and all the action keys are working (like play, pause, next, previous, stop, and the volume and mute ones adjust the system volume, which I like. The only key that I know of that isn't working is the circular one on the top of my keyboard next to the power one that says "MediaDirect". I don't know and can't seem to figure out what the XF86 thing or key number are. Right now, when I press this button, a window comes up which says "Couldn't execute command: rhythmbox
Verify that this command exists." This is probably because I removed rhythmbox from my computer in favor of Listen. I would like Listen to open when I press this button, but I do not know how to change this. Any ideas?[/QUOTE]

I don't know how to change the default "music" application for the keyboard shortcut -- but I can think of an "ugly" hack to do it, if you're interested:

1. Disable the old shortcut
  Open up the Keyboard Shortcuts box (System->Preferences->Keyboard Shortcuts) and erase the shortcut for "Launch music player" (click on it and push backspace).

2. Create a new shortcut with the Configuration Editor
  Open the Configuration Editor by pushing Alt-F2 and running "gconf-editor".  Find the key apps/metacity/global-keybindings/run_command_1.  Edit this key so that its value is the command for Listen (I've never used it, so I dont know what this is).  Then go to the key apps/metacity/keybinding_commands/command_1 and change its value so that it's whatever the X keysym for your key is.  You can find that by using xev in a terminal (read [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) to help you).

That should do it.  If you can figure out how to change the program that's launched by default by the "keyboard shortcuts" "lanuch music player" command, though, please post -- I'd like to know!

-Jeremy

---

### Post by chenel on 2006-06-25
[QUOTE=ffi]I have a logitech cordless pro, it works in gnome but not kde, when I look at xmodmap, there are no x86 keys, xev does give an output. I tried selecting the keyboard from system settings->regional & accessibilty ->keyboard layout but still nothing.... (btw i am running xgl)[/QUOTE]

Sorry I don't know much of anything about either KDE or XGl.

Anybody?

---

### Post by strabes on 2006-06-25
Yeah I finally figured that out. The name of that key is XF86AudioMedia

---

### Post by chenel on 2006-06-25
[QUOTE=strabes]Yeah I finally figured that out. The name of that key is XF86AudioMedia[/QUOTE]
So did the rest of it work?

---

### Post by strabes on 2006-06-25
The rest of the buttons you mean? For some reason they all worked without any configuration. But I had done the exact same thing you said yesterday and finally got it to work. Now I'm trying to figure out how to get it to both run listen, and bring it up from the system tray if it is already running.

---

### Post by nanotube on 2006-06-25
sorry to jump in, but i have a very related problem.
on my dell kb there is a key combo "fn-esc" that's supposed to suspend the computer, but it doesn't do anything. using xev in X, or showkey in a vty shows nothing when that key combo is pressed.

so, from the previous discussion i gather that this means that the kernel is not even seeing that keycode, and there's nothing i can do about it. ok...

but then, under breezy, i was able to go to system>preferences>kb shortcuts, and there was a line item for "sleep", which i just set to "ctl-esc" and it worked. but after dapper upgrade that line item was gone.

so now my question is, how do i set a kb shortcut for ctl-esc to be sleep? there is a file /etc/acpi/events/sleepbtn, that looks like:
```
# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/sleep.sh
```
so i am thinking to replace the "button[ /]sleep" part with a keycode for ctl-esc. using showkey, ctl-esc gives the scancode "0x1d 0x01 0x81" (if that's relevant. this actually seems separate keycodes for the keys...). so how would i go about it?

any hints appreciated. :)

---

### Post by nanotube on 2006-06-27
anyone? chenel/Jeremy? :)

---

### Post by chenel on 2006-06-27
[QUOTE=nanotube]sorry to jump in, but i have a very related problem.
on my dell kb there is a key combo "fn-esc" that's supposed to suspend the computer, but it doesn't do anything. using xev in X, or showkey in a vty shows nothing when that key combo is pressed.

so, from the previous discussion i gather that this means that the kernel is not even seeing that keycode, and there's nothing i can do about it. ok...

but then, under breezy, i was able to go to system>preferences>kb shortcuts, and there was a line item for "sleep", which i just set to "ctl-esc" and it worked. but after dapper upgrade that line item was gone.

so now my question is, how do i set a kb shortcut for ctl-esc to be sleep? there is a file /etc/acpi/events/sleepbtn, that looks like:
```
# /etc/acpi/events/sleepbtn
# Called when the user presses the sleep button

event=button[ /]sleep
action=/etc/acpi/sleep.sh
```
so i am thinking to replace the "button[ /]sleep" part with a keycode for ctl-esc. using showkey, ctl-esc gives the scancode "0x1d 0x01 0x81" (if that's relevant. this actually seems separate keycodes for the keys...). so how would i go about it?

any hints appreciated. :)[/QUOTE]

Umm.  Well, you might yet be in luck with your laptop, because often those laptop key combinations like Fn+Esc generate ACPI events (which is why you found the sleep shell script in the ACPI directory! :-)), even if their scancodes aren't registered.  I don't really know how to figure out how to detect them, though, so some Google-ing might be in order if you want to make that work.  I found [this page]("http://leufke.info/linux/asus/") on a quick look (potentially helpful info about halfway down under "ACPI and buttons") but you might be able to find something more instructive elsewhere...

Otherwise, open up the Configuration Editor (Alt+F2 and type "gconf-editor"), and go to apps/metacity/global-keybindings/run_command_1. Edit this key so that its value is /etc/acpi/sleep.sh (this is what is run by the 'sleepbtn' script you found). [You might need to put 'gksudo' (the GTK sudo frontend that GNOME uses) in first--I can't remember if ACPI scripts need to be run as root--but try it first the way it is.]  Then go to the key apps/metacity/keybinding_commands/command_1 and change its value so that it's <Ctrl><Esc>.

I think that should do it.

[Oh, and sidenote -- the 'button[ /]sleep' you were going to replace in the sleepbtn script is the ACPI event generated by the 'sleep' button.  I don't think changing that to a scancode is necessarily going to fix things, but it might.  If you can figure out how to set the 'sleep' button--and I know there's a way to do it, because I remember reading about it a couple years ago when I still used Gentoo--then that might be a cleaner solution.  Hopefully this will work in the meantime.]

-Jeremy

---

### Post by hikaricore on 2006-08-21
i saw mention of launching a music player in this thread so i'm posting it here as well, this assumes you no longer have rythmbox installed.  it won't solve the key mapping for your player if it does support it but you will still be able to atleast launch from the button :)

sudo gedit /usr/bin/rhythmbox

"type in the command that launches your music player and save the file"

sudo chmod +x /usr/bin/rhythmbox

"then hit the button you use to launch a music player"

YOU WIN!

---

### Post by spyke01 on 2006-12-29
youre a lifesaver hikaricore your directions worked perfectly

---


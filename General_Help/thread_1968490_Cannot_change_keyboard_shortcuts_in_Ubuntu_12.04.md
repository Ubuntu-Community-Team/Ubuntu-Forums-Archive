---
title: "Cannot change keyboard shortcuts in Ubuntu 12.04"
date: 2012-04-29
forum: General Help
---

### Post by Godspell on 2012-04-29
Hello fellow Ubuntu users,

Ubuntu 12.04 64bit fresh installed on my laptop. Everything is working fine, no fatal errors and so forth.
The shortcut problems I have is that I just can't set them like I used to be able to in Lucid. My usual shortcuts are

Terminal --- Super (Windows Logo key) + T
Search --- Super + S
Calculate --- Super + C
Home Folder --- Super + E
Run Command Prompt --- Super + R
Lock Screen --- Super + L

I am able to change the keyboard shortcuts to my will (All Settings -> Keyboard -> Shortcuts) but they don't work at all. For example, when I called Terminal (Super + T), the bloody recycle bin comes up. Other keys don't work out right. It's really annoying.

Another problem I have is not being able to restore them to default. I realised the preferred keyboard shortcuts cannot be set. So, I thought I'll just restore them but there doesn't seem to be a way to do it. Right now, I've disabled them.

What's happened with shortcuts??? Why can't I set them like I used to anymore? Could any of you tell me if there is any workaround? Suggestions and discussions are welcome.

Thank you very much. Best regards.

---

### Post by NaturistGirl on 2012-04-30
Me too, I upgrade my system, I think it was yesterday. I would also like to know if there is a user manual for it.

---

### Post by never2far on 2012-04-30
I have a similar problem...i can change shortcuts but after restart none of them are keept

---

### Post by Godspell on 2012-04-30
> Me too, I upgrade my system, I think it was yesterday. I would also like to know if there is a user manual for it.Now that you've mentioned, I've just remembered the "Ubuntu Desktop Guide". If you go to Dash and type "Help", it'll come up with a question mark icon. It looks like a good and simple guide. Two topics in there; "Useful keyboard shortcuts" and "Set keyboard shortcuts" explain briefly but no info about errors and troubleshooting. I did learn that some default keyboard shortcuts in Ubuntu 12.04 use Super key such as 

Super + S --------- Activate the workspace switcher. Zoom out on all workspaces
Super + W--------- Activate "Expo" mode. Show all windows from current workspace.

It's beyond me why they didn't make standard Super key shortcuts (same as Windows) since they're using it as default.

> **never2far said:**
> I have a similar problem...i can change shortcuts but after restart none of them are keept

Are your keyboard shortcuts similar to mine? Any of my shortcuts I've listed above doesn't work at all. Let me know. Sorry I can't be more helpful. I'm also trying to get help myself.

---

### Post by MrFogg on 2012-04-30
Same here... I looked quickly if there was a bug but couldn't find one... For me, I am used to switching between desktops using <super+1>, 2 , 3 and so on... "I'm lazy, the super (windows) key is just closer"

The latter works for the Alt key <Atl+1> ,2 ,3 etc.. but not for the super (windows key)...

---

### Post by maildcastro on 2012-04-30
Hello all,

I have the same issue (now in 12.04). From Ubuntu 11.10 i have problems to configure my own keyboard shortcuts. I'm tried on ubuntu 11.10 to change some shortcuts from Compiz Settings and others from keyboard configuration and some key combinations work well and others don't. Some times, works for a few days and then dont work again.
Looks lke the key combinations on Ubuntu 11.10 and 12.04 are hardcoded and they can't be changed.:cry::cry::cry:
Any help are welcome!!!

Regards!

---

### Post by gordonh on 2012-04-30
One thing I found by accident is that if you hold the super key for a short time all keyboard shortcuts are displayed, and the first 9 items on the Launcher bar (if that's the right term) can be selected by number.

This doesn't snwer the question directly, but at least you can see what's available.

---

### Post by Tommos on 2012-05-01
Hi,

I have the same issue.
Changing keyboard shortcuts in System Settings->Keyboard->Shortcuts does not have any effect. Very frustrating.
No work-around found so far, but investigating.

Note: using Gnome-Shell 3.4.1

---

### Post by marrok1 on 2012-05-01
When all else fails you can use gconf-editor or dconf-editor to edit shortcuts manually.

---

### Post by marrok1 on 2012-05-01
For example with dconf-editor under org > gnome > desktop > wm > keybindings. You can easily set the keybinding's.

---

### Post by SlawekW on 2012-05-01
Install CompizConfig Settings Manager (CCSM)
sudo apt-get install compizconfig-settings-manager

Open CCSM from System Tools>Preferences>CompizConfig Settings Manager. Open "Commands" under the General group. Enable by check marking the box on the left. Restart X

Set your options under "Commands" and "General Options > Key Bindings" in Compiz

Terminal - gnome-terminal
Calculate --- gnome-calculator
Home Folder --- nautilus

---

### Post by tomatoe on 2012-05-01
I had the same issue. Here is what I did.

> **tomatoe said:**
> Found it!

**Text Entry Shortcuts**

 If  you want to have quick access to lines of text by using a hotkey,  for  example to enter your email address in forms, then you can use   xbindkeys. Xbindkeys has a GUI utility to allow easy settings of   hotkeys, but be aware that it's a little more complicated than the   default Ubuntu Shortcutkeys interface. 
Install xbindkeys   
sudo apt-get install xbindkeysCreate the default config file for xbindkeys 
xbindkeys --defaults > /home/your-user-name/.xbindkeysrcWhen thats done, install xbindkeys-config, the GUI for xbindkeys 
sudo apt-get install xbindkeys-configNow the utility the actually does the "typing" 
sudo apt-get install xvkbdOnce each is installed, start both applications by bringing up "Run Application" with ALT -F2. 
xbindkeysand
xbindkeys-config 
To  keep the xbindkeys hotkeys active when you next start the computer  you  will have to add a new session, System --> Preferences -->   Sessions. Put in the command "xbindkeys" into the command field (without   the quotes). 


[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

---

### Post by Paddy Landau on 2012-05-01
What I have discovered is that customised keyboard short-cuts in 12.04  do not work if they use the Super key.

If I create short-cuts without  the Super key (e.g. Ctrl-Alt-Shift-D), then they work.

Disappointing.

---

### Post by RSparker on 2012-05-01
As far as I can tell, and I'm not going to plunge into the murky depths of the insane "customizations" that Ubuntu introduces with each new release to find out for sure, the changes you make to Settings > Keyboard > Shortcuts don't get written to the dconf backend, and thus they're never usable by other desktop environments and pull keybindings from there.

If I had to guess I'd say this is another "innovation" by the Ubuntu folks. Now, I don't use Unity, but I did install a fresh image of 12.04 on a virtual machine and the shortcuts work fine there. Switch to another desktop environment (e.g. gnome shell) and they don't.

The local fix, as someone has already mentioned, is to edit dconf directly:

```
sudo apt-get install dconf-tools
dconf-editor
```

Then just navigate to org.gnome.desktop.wm.keybindings and alter them there. For me, the the big ones were maximize (self-explanatory) and panel-main-menu (trigger the activities overview on gnome shell).

---

### Post by forrestcupp on 2012-05-01
> **Paddy Landau said:**
> What I have discovered is that customised keyboard short-cuts in 12.04  do not work if they use the Super key.

If I create short-cuts without  the Super key (e.g. Ctrl-Alt-Shift-D), then they work.

Disappointing.

This is what I was going to say. Save yourself a lot of headaches and don't try to use the Super key. It just doesn't work for some reason. It doesn't matter which way you go about trying to set keyboard shortcuts, if you use the Super key, it won't work. Use different key combinations, and you won't have any problems at all.

This is a pain in the backside when you have to use Windows sometimes, and you want to set it up the same in both OSs. But that's just how it is right now.

---

### Post by Paddy Landau on 2012-05-02
> **forrestcupp said:**
> ... don't try to use the Super key. It just doesn't work...
Is this something we can raise as a bug?

---

### Post by Paddy Landau on 2012-05-07
I have raised a bug for this.

If it affects you, please [go to the bug and vote for it]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/995885") (the green wording near the top of the page).

---

### Post by Sicadastra on 2012-05-08
I have the same problem. I installed dconf-editor but when I type in a shortcut for show-desktop ('<Alt>D') it isn't working. There is no command line for lock screen too. I'm at a loss on how to do it on Compiz (typing a shortcut seems not to work too).

I hope this can be fixed. :(

---

### Post by Paddy Landau on 2012-05-08
> **Sicadastra said:**
> ... when I type in a shortcut for show-desktop ... how to do it on Compiz

[LIST]
[*] Install CompizConfig Settings Manager ([ccsm]("apt:compizconfig-settings-manager")).
[*]Start ccsm.
[*]General > General Options > Key Bindings > *Show Desktop* (for the keyboard, not the mouse)
[*]Click on the button to its right > Grab key combination > (press Alt-D) > OK
[*]Close the ccsm window
[/LIST]
Test.

---

### Post by Sicadastra on 2012-05-08
> **Paddy Landau said:**
> 
[LIST]
[*] Install CompizConfig Settings Manager ([ccsm]("apt:compizconfig-settings-manager")).
[*]Start ccsm.
[*]General > General Options > Key Bindings > *Show Desktop* (for the keyboard, not the mouse)
[*]Click on the button to its right > Grab key combination > (press Alt-D) > OK
[*]Close the ccsm window
[/LIST]
Test.

Thank you for the help. Sadly, it doesn't work. I followed your instructions carefully but to no avail. I tried to put in my alt-d by clicking on the 4 button choices (super, control, alt, shift) but it still won't work. When I close CCSM then restart it, the key bindings go back to it's default (control+primary+super+d). :(

---

### Post by Paddy Landau on 2012-05-08
> **Sicadastra said:**
> When I close CCSM then restart it, the key bindings go back to it's default (control+primary+super+d).
That is so strange! I don't get that same behaviour. You are using 12.04, aren't you? There were some CCSM updates just today; perhaps you need to run Update Manager, update, reboot, and try again. Sorry, I am guessing at this point; I don't know what else to suggest.

---

### Post by Sicadastra on 2012-05-08
> **Paddy Landau said:**
> That is so strange! I don't get that same behaviour. You are using 12.04, aren't you? There were some CCSM updates just today; perhaps you need to run Update Manager, update, reboot, and try again. Sorry, I am guessing at this point; I don't know what else to suggest.

Yes, I'm running 12.04. I'll check for updates and if there's an update, I'll try with CCSM again. Thank you for your assistance. I appreciate it. :)

---

### Post by Godspell on 2012-05-08
> That is so strange! I don't get that same behaviour. You are using  12.04, aren't you? There were some CCSM updates just today; perhaps you  need to run Update Manager, update, reboot, and try again. Sorry, I am  guessing at this point; I don't know what else to suggest. > **Sicadastra said:**
> Yes, I'm running 12.04. I'll check for updates and if there's an update, I'll try with CCSM again. Thank you for your assistance. I appreciate it. :)

Forgive me if I'm wrong but isn't Compiz deprecated? I've heard a chatter about that. Ubuntu 10.04 has always been my favourite. So, when I first came onto 12.04, I was wondering where have all the desktop effects gone. Later on, somebody on the Internet said it's not compatible with 12.04.

Btw, Paddy Landau, thank you so much for the bug report. I've just voted! :)

> As far as I can tell, and I'm not going to plunge into the murky depths  of the insane "customizations" that Ubuntu introduces with each new  release to find out for sure, the changes you make to Settings >  Keyboard > Shortcuts don't get written to the dconf backend, and thus  they're never usable by other desktop environments and pull keybindings  from there.

If I had to guess I'd say this is another "innovation" by the Ubuntu  folks. Now, I don't use Unity, but I did install a fresh image of 12.04  on a virtual machine and the shortcuts work fine there. Switch to  another desktop environment (e.g. gnome shell) and they don't.I did a fresh install on my laptop, too, but I'm on Unity. Not because I like it but since it's clearly becoming 'the future', thought I'd give it a good try. I've not switched to another desktop environment but my personal shortcut settings didn't work in the first place. I tried to edit the dconf as well but that didn't work either.
I'm afraid we've pretty much hit the wall.

For the record, on another machine, I've tried Gnome-shell but didn't quite like it. I don't know how to explain but it just didn't look the same as 10.04. Maybe because back then it was using older version of Gnome.

---

### Post by phibxr on 2012-05-08
> **Godspell said:**
> Forgive me if I'm wrong but isn't Compiz deprecated? I've heard a chatter about that. Ubuntu 10.04 has always been my favourite. So, when I first came onto 12.04, I was wondering where have all the desktop effects gone. Later on, somebody on the Internet said it's not compatible with 12.04.

This does not sound accurate. Ubuntu 12.04 and especially Unity are pretty much built around Compiz.

---

### Post by Godspell on 2012-05-08
> **phibxr said:**
> This does not sound accurate. Ubuntu 12.04 and especially Unity are pretty much built around Compiz.

Alright then, ignore what I said above. In that case, I'll look into it a bit more to get Compiz installed on my machine, too.

---

### Post by Paddy Landau on 2012-05-08
> **Godspell said:**
> Forgive me if I'm wrong but isn't Compiz deprecated?
As phibxr said, no, it's very much still in use!

> **Godspell said:**
> ... I'm on Unity. Not because I like it but since it's clearly becoming 'the future', thought I'd give it a good try.
I was nervous when I first tried Unity, but actually it's fantastic. I love it. It's so much quicker than the old menu-driven interface.

---

### Post by Quatrix on 2012-05-08
I'm having problems too.  I thought I had to take special steps in version 11 to make the Windows key work, but I don't remember now.

However, it seems to depend on the key or the function.  Although I couldn't get Win+E (home folder) or Win+R (run) to do anything, Win+D works for "Hide all normal windows" (show desktop).  I'm wondering if the shortcuts ARE taking effect but are being overridden by shortcuts somewhere else.  I'm not logged into Ubuntu at the moment, but someone else might try assigning Win+D to one of the other functions and seeing if it works.

---

### Post by Paddy Landau on 2012-05-09
> **Quatrix said:**
> I thought I had to take special steps in version 11 to make the Windows key work, but I don't remember now.
I did nothing special. It just worked.

> **Quatrix said:**
>  I'm wondering if the shortcuts ARE taking effect but are being overridden by shortcuts somewhere else.
I had wondered about that, but I don't believe it is so. It seems that Unity grabs the Super key.

> **Quatrix said:**
> ... someone else might try assigning Win+D to one of the other functions and seeing if it works.
I've just tried, and no, it does not work.

As this affects you, please [go to the reported bug and vote for it]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/995885") (the green wording near the top of the page on the left-hand side).

---

### Post by Quatrix on 2012-05-09
Okay, then it's a problem with certain functions, not certain keys.  If I bind Win+E to some other functions such as "launch terminal", it works.  The Windows key just doesn't work at all for functions like "home folder" and "run".

---

### Post by Paddy Landau on 2012-05-10
> **Quatrix said:**
> Okay, then it's a problem with certain functions, not certain keys.  If I bind Win+E to some other functions such as "launch terminal", it works.  The Windows key just doesn't work at all for functions like "home folder" and "run".
I've just been testing. It seems that it is a function specifically of Custom Shortcuts.

If I use Super-E or Super-D for Launch Terminal (in the Launchers category), they work. But if I use the same keys in the Custom Shortcuts category, they don't.

---

### Post by modr on 2012-05-12
@Paddy

I can confirm that. Does anyone know what blocks/captures these Key-pressings? Or how to track this down?
By the way, what sense does it make not to allow a shortcut that is not being used. Is this some kind of anti-M$-stuff?

---

### Post by Paddy Landau on 2012-05-12
> **modr said:**
> By the way, what sense does it make not to allow a shortcut that is not being used. Is this some kind of anti-M$-stuff?
LOL, no, I think it is an accidental regression. There were problems with the Super key before; in 11.04 it worked perfectly; but the problems have arisen again.

---

### Post by modr on 2012-05-13
> **Paddy Landau said:**
> LOL, no, I think it is an accidental regression. There were problems with the Super key before; in 11.04 it worked perfectly; but the problems have arisen again.


In 11.10 I did the following: unmapped the expo kay and remapped the desired shortcuts (note: <Super> or <Mod4> in the examples below do not yield any benefit).

```

  echo "Assign Windows key and set Win+E, Win+T, Win+B"
  echo "set \"Super is mapped to Win-key\""
  gconftool-2 --type list --set \
  /desktop/gnome/peripherals/keyboard/kbd/options --list-type \
  string "[altwin	altwin:super_win]" #need to be a tab
  
  echo "set up Nautilus shortcut Win+E"
  echo "Win+E is by default set for Compiz Expo Plugin."
  echo "Set Win+X for Compiz Expo Plugin."
  gconftool-2 -t str --set \
  /apps/compiz-1/plugins/expo/allscreens/options/expo_key "<Super>x"
  gconftool-2 -t str --set \
  /apps/gnome_settings_daemon/keybindings/home "<Mod4>e"

```
Since 12.04 This does not work with the home folder but with the terminal ...:confused:

```

 echo "set up Terminal shortcut Win+T"
  gconftool-2 -t str --set \
  /apps/metacity/global_keybindings/run_command_terminal "<Mod4>t"

```


... when I press Win+E just a tiny search bock with an "e" in pops up (see screenshot).

[ATTACH]217860[/ATTACH]

Any ideas? Is there really nothing we can do to address that "regression" whatever you refer to with it?!?
Re
modr

---

### Post by Paddy Landau on 2012-05-13
> **modr said:**
> Since 12.04 This does not work with the home folder but with the terminal ...
As [post=11922661]explained before[/post], the terminal is not a custom short-cut, so it works. I don't know about the home folder, sorry.

> **modr said:**
> ... when I press Win+E just a tiny search bock with an "e" in pops up (see screenshot).That will happen even if you just press E. It starts a search box, with the Super key being ignored.

---

### Post by johngoold on 2012-05-13
I've switched to Ubuntu 12.04 from Mac OS X (and VERY occasionally, Windows). I had used it for decades (literally). That means that combinations like Command+V for "paste" (or, for non Mac people, Win+V) are ingrained reflex reactions. Try as I do to use Ctl+V (etc.), I keep tripping up.

When I experimented using a previous Ubuntu release, I was able to make the left Win key appear to be the same as Ctl.

I don't actually want to change shortcuts per se. What I really want to do is use the right Command (Win) key as Super and have the left Command (Win) key as another Ctl key.

I also want to use the right Option (Alt) key for something else (whatever the key is called that is used to allow entering accented letters, em-dash and other special characters). Currently I have the right Command (Win) key set to do that. This worked with the older Ubuntu release.

Probably related is another item. I cannot disable Caps Lock (a key I frequently activate by accident) — very annoying!

---

### Post by Paddy Landau on 2012-05-13
> **johngoold said:**
> What I really want to do is use the right Command (Win) key as Super and have the left Command (Win) key as another Ctl key...
Regarding your problems, it sounds as though you want to remap certain of the keys on the keyboard. Although this can be done (with some difficulty), I don't recommend it -- it is better to learn to use the keys for their given tasks, otherwise future upgrades will trip you up.

If you still wish to go ahead with remapping your keyboard, have a look at xev, xmodmap, xbindkeys, and [xbindkeys-config]("apt:xbindkeys-config") (the last is GUI; the others are all CLI). As I have never used any of these, I cannot help you with their use -- Canonical does not support any of them, so use them at your own risk!

---

### Post by modr on 2012-05-13
> **johngoold said:**
> 
Probably related is another item. I cannot disable Caps Lock (a key I frequently activate by accident) — very annoying!

Although running risk this thread being hijacked ...

... maybe best to start a new one and link it if need be.

Nevertheless, did you try to remap it using .Xmodmap

see
[http://wiki.archlinux.de/title/Xmodmap]("http://wiki.archlinux.de/title/Xmodmap")
[http://wiki.ubuntuusers.de/Xmodmap]("http://wiki.ubuntuusers.de/Xmodmap")

Re

modr

---

### Post by wmalam on 2012-05-16
You also cannot use the numeric keypad for shortcuts in 12.04 / 64 bit. 

In previous versions of Ubuntu, the shortcut dialog could distinguish a numeric keypad key from its counterpart on the main keyboard. (for instance "numeric_+" vs plain unicode "+"  This allowed you to use the entire set of numeric keys, shifted and otherwise, as an extra bank of function keys. Unity 12.04 does not do that. 

Also, I see no way to change the shortcuts for opening the dash and finders. 

There are many things I like about Unity. (The HUD is brilliant) but I  must have customizability, and Unity still falls far too short. I'm sticking for XFCE, for now. 

(Hey, that's why we have multiple desktops) 

:)

---

### Post by Quatrix on 2012-05-18
I installed some updates this morning, and all of my shortcuts were reset to the defaults after rebooting.  I was cautiously optimistic that they got reset because this bug was fixed, but nope.

---

### Post by Paddy Landau on 2012-05-23
The [bug for this issue]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/995885") has been raised to "High" importance. I found that surprising, as I would have made it "Moderate", but it is in progress, which is great.

---

### Post by Quatrix on 2012-05-23
I'm not very familiar with the fix rollout process.  I know noncritical Linux bugs tend to get fixed and distributed to users much faster than Windows bugs, but is this the sort of thing that would be fixed in an incremental package update or not until 12.10?

---

### Post by Godspell on 2012-05-27
I've kind of come to terms with this issue and started to learn the default shortcuts :confused:
It's pretty whacky that you can't change the shortcuts like you used to be able to in 10.04. I don't wanna sound like an old windbag but I find myself thinking about 10.04 a lot of the times, and how good it was.

> I installed some updates this morning, and all of my shortcuts were  reset to the defaults after rebooting.  I was cautiously optimistic that  they got reset because this bug was fixed, but nope. 	

You know I thought of exactly the same thing! After the reboot, I enthusiastically re-applied all the shortcuts BUT none of it worked.  Still brining up the Rubbish Bin.

Since the bug report priority is "high" and it is in progress, maybe we'll see a fix in near future. Just keep checking the bug report page, I guess.

Many thanks and regards.

---

### Post by cacycleworks on 2012-06-04
My problem is that I use Autokey (now is autokey-qt) to automate email replies. In 12.04, <super>+t always launches the recycle bin, regardless of anything else... curiously, Autokey catches super+t and does what I want and then the recycle bin pops open. :P

---

### Post by oedsrm on 2012-06-06
After a good deal of looking around I haven't found a work around that actually works.  dconf / gsettings / Custom Shortcut don't work for me.  But I'm no linux guru.  I just want my <ctl><alt><left> to be handled by my programming software.

The bug report at ubuntu is [965921]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/965921") for what it's worth.

Pete

---

### Post by cacycleworks on 2012-06-06
I later discovered that sshfs is buggy in 12.04, which is quite disheartening to me. I only use it everyday...

---

### Post by TREESofRIGHTEOUSNESS on 2012-06-17
Still a bug.  I was wondering why it was so hard to set custom keys.
It seems that the Custom Shortcuts MOSTLY don't work.
Redefining any of the 'non' custom ones seems to works (as long as you AVOID the Super/Win Key).
I say mostly don't work because I use
Ctrl+Alt+Delete bound to "/usr/lib/indicator-session/gtk-logout-helper -s"
And Changed 'System-Logout' to Ctrl+Alt+Home (Just to set it to something else) and that works...
However I cannot just launch 
/usr/bin/gnome-system-monitor
with a custom key combo.... though it used to work (and actually I used to be able to just use gnome-system-monitor in 11.10) when I first installed 12.04  the bug page says you have to use Ubuntu tweak or CCSM to workaround the problem..

---

### Post by smellytoes on 2012-10-27
Trying to change shortcuts in settings>keyboard>shortcuts does not even work.

To change the shortcuts in keyboard settings, i would have to gconftool-2 --recursive-unset /apps/metacity/global_keybindings
in terminal.

Even after doing this, the shortcuts just reset to default after keyboard setting closes just like many other users.

I've been trying to get back alt-f2 functionality for a few months now!

---


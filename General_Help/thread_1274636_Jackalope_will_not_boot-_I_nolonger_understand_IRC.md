---
title: "Jackalope will not boot- I nolonger understand IRC- rhythmbox flaky"
date: 2009-09-24
forum: General Help
---

### Post by Wanda on 2009-09-24
Please instruct on how to uninstall Jaunty Jackalope.  It no longer wants to boot up and I have been forced to return to Ibex 8.10. In August I had a resolution problem that never was resolved. That issue was posted at the Cafe.  I then upgraded to J.Jackalope in the off chance that that might resolve the problem... but no.  Today, after opting for nvidia drivers and an unexpected update of security 3 security files, the machine would not reboot w/ Jackalope.   The screen begins to load with Jaunty Jackalope's screen and then goes black, when it should normally kick over to a tan screen and the sound should load . When restarting, all options- including recovery for 9.04, do not load.  

 I also have been having intermittent problems with getting rhythmbox to load. I am aware that some of the time streamed radio stations have server problems. However, more times then not I have to click several times to simply get the application to load onto the desktop. 

I tried lamely to use IRC pidgen and could not get that to work either... I've never used IRC extensively and have become very stale in how to operate it. If anyone can tell me how to register and refresh me as to how to connect, it may be easier to resolve these other problems. After I post this I will resume looking for a tutorial on how to get that working... and will check back here for guidance.

Sadly at this point I am willing to loose my settings, however shedding things like bookmarks don't mean that much. I am more interested in having a machine that operates relatively well. 
TIA
wanda

---

### Post by bboston7 on 2009-09-24
I recommend xchat for IRC.  Pidgin isn't really built for an IRC conversation.

You want to
/server irc.server.com
/join #room

then talk.  Type
/nick nickname
to change your nickname.

---

### Post by fcuk112 on 2009-09-24
irssi is pretty good for irc.

---

### Post by Wanda on 2009-09-25
Thank you for responding. Could you please guide me through this with a little more detail: 
> **bboston7 said:**
> I recommend xchat for IRC.  Pidgin isn't really built for an IRC conversation.

You want to
/server irc.server.com
/join #room

then talk.  Type
/nick nickname
to change your nickname.

When you state: "/server irc.server.com"
Where am I to enter that?
In a browser?
In launchpad?
I assume that the "/" means enter...? 

Sorry for being so thick about this. I have been on the internet for > 2 decades but I think I have chatted perhaps 4 times. :confused: 


The main reason why I want to operate IRC is to discuss resolving the problem with Jaunty Jackalope, which is not booting up. I have resolved one problem with rhythmbox and now have full volume. I still am not clear what caused the problem, but it is functioning... at present...

What must I do to get xchat to work? Once I do that and register my name, do I then go to irc.ubuntu.com and then go to the corresponding chat room to ask about what I should do to resolve the Jaunty Jackalope issue? 

Yesterday I tried to go to irc.ubuntu.com and I think I got on line but the resolution was so bad I could not read what was being typed... If all else fails I may try working on this problem from a different machine that has no resolution problems. When I refer to resolution issues this means that the page on any given screen is displayed wacky. Often I have to play with the browser (FF) settings so I am able to read the screen. I am thinking that the graphics card on this machine is very poor and that this may be part of the problem. When I go to preferences, resolution I am only offered a resolution ration of 800x600 when in the past I was allowed something about 1000 x 800...

Sorry for the digression but it too plays a factor.

TIA
Wanda

---

### Post by t0p on 2009-09-25
> **Wanda said:**
> Thank you for responding. Could you please guide me through this with a little more detail: 


When you state: "/server irc.server.com"
Where am I to enter that?
In a browser?
In launchpad?
I assume that the "/" means enter...? 

Sorry for being so thick about this. I have been on the internet for > 2 decades but I think I have chatted perhaps 4 times. :confused: 


The main reason why I want to operate IRC is to discuss resolving the problem with Jaunty Jackalope, which is not booting up. I have resolved one problem with rhythmbox and now have full volume. I still am not clear what caused the problem, but it is functioning... at present...

What must I do to get xchat to work? Once I do that and register my name, do I then go to irc.ubuntu.com and then go to the corresponding chat room to ask about what I should do to resolve the Jaunty Jackalope issue? 

Yesterday I tried to go to irc.ubuntu.com and I think I got on line but the resolution was so bad I could not read what was being typed... If all else fails I may try working on this problem from a different machine that has no resolution problems. When I refer to resolution issues this means that the page on any given screen is displayed wacky. Often I have to play with the browser (FF) settings so I am able to read the screen. I am thinking that the graphics card on this machine is very poor and that this may be part of the problem. When I go to preferences, resolution I am only offered a resolution ration of 800x600 when in the past I was allowed something about 1000 x 800...



To get better resolution options, open a terminal and type the command

```
xrandr
```If higher resolutions are available, they will be listed in the terminal.  Then you can return to **System > Preferences > Display** and the higher reolution settings will now be available.

You don't really need to register a nick (name) on irc.  And you won't need those commands if you use xchat as it has a gui with menus etc.  I don't think xchat is installed by default.  So install it yourself, in Synaptic; or type into a terminal:

```
sudo apt-get install xchat
```

As for getting rid of Jaunty: fire up a live cd, run gparted and tell it to format the Jaunty partition.  You'll then be able to add the released space to another partition if you want.

---

### Post by marshag63 on 2009-09-26
Wanda, if you don't mind a dos-like chat box (which should be easier for you to see given your resolution problem) you could try an IRC chat application by the name of "irssi"

Once booted into Ubuntu, press Ctrl + Alt + F1 keys at the same time and it will take you to a "terminal" (looks like a DOS screen) which will ask for your user name and password (just like when you logged in to ubuntu). Once you are logged in there you will see something like:

[COLOR="Blue"]wanda@wanda-desktop ~ $
[/COLOR]
You can now install "irssi" from the command line by typing this:

[COLOR="Blue"]sudo apt-get install irssi [/COLOR] (then press the enter key)

you may have to answer a yes/no question (go with yes) or two before install is completed.

Once install is completed and still at command line (wanda@wanda-desktop) then type the follow command to start "irssi"

[COLOR="Blue"]irssi[/COLOR]

You will then see an application running on the screen.  At the very bottom of the screen there will be the word "status" - that is where you type commands to run the program and also enter text to chat on IRC.

A forward slash tells the application you are entering a command.

First command to join a server:

[COLOR="Blue"]/server irc.freenode.com [/COLOR] (then press enter)

Watch the screen and wait a few seconds to make sure you get connected to the server - you will see something like:

Irssi:  [COLOR="Blue"]Join to[/COLOR] [COLOR="Orange"]#irc.freenode.com[/COLOR] [COLOR="Blue"]was synced in 1 secs[/COLOR]

Second command - join a chat channel

[COLOR="Blue"]/join ubuntu[/COLOR] (then press enter)

You need to enter a "nickname" for yourself - it can be whatever

[COLOR="Blue"]/nick wanda[/COLOR]

You should now be in the Ubuntu IRC chat channel, where others can answer questions, etc.

A little tip:  If you are chatting to one specific person, type the first letter of their name and press the tab key until their name comes up and then type your question (some of the names are crazy to try and type out).

Also, you can use the PageUp key to scroll back through what has been said if you need to re-read something, then use PageDown to get back to the last entry in the channel.

When you are done chatting and want to leave a chat:

[COLOR="Blue"]/part[/COLOR] (leaves the chat, but does not close irssi)

[COLOR="Blue"]/quit[/COLOR] (leaves the chat and quits the program).

To log out of the DOS-like terminal window just type the word "[COLOR="Blue"]exit[/COLOR]"

You can still see your graphical desktop at anytime by pressing:  [COLOR="Blue"]Ctrl + Alt + F7[/COLOR]

Pressing Ctrl + Alt + F1 takes you back to the DOS-like screen.  You can leave your chat running there and switch back and forth while you work on your resolution problem and once that is fixed, you can use a terminal window to run irssi from the graphical desktop.

Hope this is helpful - see you in the chat room :)

MarshaG.

---


---
title: "I need some troubleshooting help"
date: 2010-09-03
forum: General Help
---

### Post by Just-trevor on 2010-09-03
My computer does not reach the log-in screen on start-up. My monitor is working; it shows the motherboard screen on boot and the grub loads fine. When I load the kernel the screen stays black and does not change. The power light is blue, meaning it is still on and connected. When I turn the computer off it searches for inputs, like usual.

It happened like this:
I turned on the compiz benchmark and noticed it was kind of low, 100 fps when it is usually around 300 after everything is fully loaded. (yah, it's a pretty good computer.) I figured this might be because I had been using suspend to turn it off and I hadn't really restarted it in some time. When I did that, the above happened.

So: some info. It is pretty hot and humid here. 90's ish I think and humid. I have good ventilation in my box, 8 fans in all, but when I touched the back of my computer on the graphics card where the monitor plugs in, it was very hot. I wouldn't really want to hold my finger there for long because it hurts. I didn't feel anything else for heat, figuring it was just the video card being safe.
This is the first time I've had a non-os related problem with this computer since I got it. 

To figure out what's up, I've tried several things so far. I switched the port the monitor was plugged into. Hey, you never know. It didn't work. I have no other video cards to try, and there is no onboard monitor port for the motherboard.
I also tried acting as if the computer was booting like normal and the monitor just wasn't on. I loaded the kernel from the GRUB, and waited for a while, looking at the blank screen. After I was sure it must have reached the log-in screen, I hit enter and typed in my password. Almost every time I boot the computer, after I sign in, some fans go on high for a second then go back to normal. I listened for this and heard nothing. 
I would try hitting super+space and typing 'restart' so gnome-do would hypothetically restart the comp, but gnome-do is not a start-up program because I've had some problems with it on start-up in the past.

Booting in safe mode works. So my question for you is this: What can I do using nothing but the command line and physical observation to figure out what's ailing my poor computer?

Thanks in advance and sorry about the wall of text

---

### Post by harrismh777 on 2010-09-03
What do you mean, "booting in safe mode works"?

What happens if you press the ctrl-alt-F1 keys to switch into terminal mode?

If the machine is plugged into the network can you ping it, or login to it?

If the machine is unplugged from the network will it boot normally?

---

### Post by Just-trevor on 2010-09-04
At the grub screen I can select ubuntu kernel blah blah blah (safe mode) and it will give me a command line and I can log on.

EDIT: no wait recovery mode. Ooops.
Also, I booted normally, waited a while, the logged in, waited a while, then clicked on the top-right corner and hit enter to try and make it turn off or something because that's where the log off button or something is, and nothing happened I think, but when I hit ctrl alt del a little later without doing anything, it restarted.
I think the only problem is that nothing is displaying on the monitor, but how can I test that or fix it w/out getting a new graphics card?

---

### Post by harrismh777 on 2010-09-08
Boot the machine and wait for it to stabilize... num lock light is usually on and the disk lite quits flashing.  Then,

... press and hold the ctrl-alt  keys and while holding those keys down press your F1 key.

Tell me what happens. Do you get a terminal black and white screen where you can logon... if so, can you logon?

Also, while holding the ctrl-alt keys down you might try pressing the F9 key to look at the logs.

If you can get a terminal to open then pressing F2-F6 will display your available sessions, F7 may bring up the GDM login manager (but probably not) and F9 will show the logs.

When the machine is booted up can you ping the machine from another machine on your network. If so, can you login to it with a terminal like ssh or telnet? 

You might try borrowing someone's older graphics card. You might be surprised how many of your friends have one... after they upgraded and so forth. Sometimes if you have bad hardware in the system the machine won't boot-up. In that case you'll need to get another card in that thing.

Hope this stuff helps.

---

